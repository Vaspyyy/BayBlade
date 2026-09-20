# Technical Architecture

## 1. Purpose

This document defines architecture requirements, not the final engine or language choice.

The technology stack should be chosen **after** these requirements are accepted, because the simulation architecture is important enough that the engine must fit the game rather than the game being bent around an engine.

## 2. Fundamental architecture rule

The mechanical simulation must be separable from presentation.

Conceptually:

```
Game / UI / Rendering
        |
Simulation Facade
        |
Mechanical Core
        |
State + Materials + Geometry + Solver Systems
```

The mechanical core should be capable of running:
- with rendering,
- headless,
- faster than real time where possible,
- in automated regression tests,
- for batch design analysis,
- for NPC evaluation,
- for replay reconstruction.

This separation is non-negotiable.

## 3. Major subsystems

Recommended top-level systems:

### Mechanical core
- rigid-body state,
- assembly graph,
- contact,
- constraints,
- launcher,
- bearings,
- fasteners,
- damage,
- fatigue,
- fracture,
- thermal,
- wear,
- aerodynamics,
- arena surface,
- debris.

### Geometry
- CAD/design representation,
- collision representation,
- render mesh generation,
- mass-property calculation,
- structural proxy generation,
- manufacturability data.

### Materials
- material definitions,
- property ranges,
- temperature dependence,
- friction pair data,
- fatigue data,
- manufacturing response.

### Manufacturing
- machines,
- tooling,
- process plans,
- tolerance generation,
- hidden manufactured state,
- inspection,
- rework.

### Telemetry
- channel definitions,
- event stream,
- match recorder,
- replay data,
- failure-analysis inputs.

### Career simulation
- calendar,
- competitors,
- events,
- economy,
- suppliers,
- sponsors,
- regulations,
- marketplace,
- technology diffusion.

### Presentation
- renderer,
- audio,
- particles,
- camera,
- UI,
- workshop navigation,
- animation.

## 4. Simulation state ownership

Avoid putting authoritative simulation state in scene objects or visual components.

Authoritative state should live in explicit data structures.

Rendering reads from simulation snapshots.

UI requests commands through controlled APIs.

This is necessary for:
- replay,
- determinism,
- save/load,
- headless tests,
- batch simulation,
- debugging.

## 5. Assembly graph

Represent a top as a graph.

Nodes:
- physical components.

Edges:
- mechanical connections.

A node may contain:
- geometry reference,
- material state,
- mass properties,
- thermal state,
- wear state,
- damage state,
- manufacturing state.

An edge may contain:
- joint type,
- stiffness,
- damping,
- preload,
- clearance,
- friction,
- damage,
- loosening.

Structural changes mutate this graph.

Examples:
- screw loosens,
- connection gains clearance,
- ring fractures,
- fragment becomes a new free body,
- bearing seizes,
- insert ejects.

## 6. Geometry representations

One geometry should not be forced to serve every purpose.

A design may generate:

### Design representation
Precise parametric/B-rep-like or constructive representation.

### Render representation
High-detail mesh.

### Collision representation
Optimized convex/compound/mesh collision data.

### Structural representation
Reduced stress zones / beam-like modes / proxy cells.

### Aerodynamic representation
Descriptors, simplified surfaces, or coefficient tables.

### Manufacturing representation
Features, tolerances, surfaces, process annotations.

These representations are derived from one design source but optimized for different jobs.

## 7. Generated geometry IDs

Procedurally generated parts need stable feature identifiers.

A surface, hole, tooth, insert pocket, or edge should be traceable across:
- CAD,
- manufacturing,
- stress analysis,
- damage,
- replay,
- inspection.

Example:

```
Part: AR-07 Rev C
Feature: radial_tooth[5].leading_edge
```

Then telemetry can say exactly where a failure began.

## 8. Hidden truth versus player knowledge

The game should separate:

### True state
What physically exists.

### Known state
What the player currently believes or has measured.

Example true state:
- diameter = 69.9824 mm
- radial runout = 14.2 µm
- 0.8 mm subsurface crack exists.

Player knowledge with cheap tools:
- diameter ≈ 70.0 mm
- "seems mostly straight"
- crack unknown.

This distinction should be foundational rather than patched in later.

## 9. Material database

Material definitions should be data-driven.

A material can expose curves or ranges for:
- density,
- elastic behavior,
- yield behavior,
- hardness,
- fracture toughness proxy,
- restitution,
- thermal conductivity,
- heat capacity,
- expansion,
- friction pair behavior,
- fatigue,
- wear,
- machinability.

Do not hardcode material behavior inside gameplay logic.

## 10. Physical property uncertainty

Material and manufacturing state can carry uncertainty.

Use explicit distributions/ranges where appropriate.

This supports:
- supplier quality,
- batch variability,
- measurement confidence,
- simulation uncertainty,
- quality control.

Avoid arbitrary random stat rolls detached from physical causes.

## 11. Solver boundaries

The core should expose clear solver interfaces.

Example conceptual APIs:
- `step_motion(dt)`
- `resolve_contacts(dt)`
- `update_thermal(dt)`
- `accumulate_fatigue(dt)`
- `evaluate_failures()`
- `update_surface(dt)`

The implementation can use different time steps internally.

This makes individual models replaceable as fidelity improves.

## 12. Event system

Important physical events should be explicit structured events.

Examples:
- ContactEvent
- YieldEvent
- CrackInitiated
- CrackAdvanced
- FastenerSlip
- FastenerLoose
- BearingOverheat
- BearingSeized
- FragmentDetached
- TipTransition
- RingOut
- SpinDeath

Events feed:
- sound,
- particles,
- replay,
- failure analysis,
- achievements/history,
- debugging.

Presentation should react to physics events rather than infer everything visually.

## 13. Telemetry storage

Telemetry should support two levels.

### Continuous channels
Sampled values:
- RPM,
- temperature,
- vibration,
- energy,
- attitude.

### Discrete events
Sparse important moments:
- impact,
- crack,
- fracture,
- loosening,
- ring-out.

Use configurable recording rates.

Very high-frequency raw data can be reduced after the match for normal replays while development builds retain deeper traces.

## 14. Replay architecture

Prefer replay from recorded authoritative state/events or deterministic input reconstruction.

Requirements:
- scrub,
- pause,
- frame step,
- arbitrary camera,
- telemetry synchronization,
- overlays,
- event markers.

Replays should not depend on live gameplay scripts being in exactly the same UI state.

## 15. Save-game architecture

Career saves may become large.

Separate:
- world state,
- player economy,
- competitor state,
- design library,
- manufactured items,
- workshop state,
- competition history,
- regulations,
- marketplace state.

Physical items need stable IDs.

A retired top on a shelf is the same persistent object that competed years earlier.

## 16. Design files

Custom designs should be stored as structured editable data, not only baked meshes.

A design record should support:
- parameters/features,
- assembly structure,
- materials,
- tolerances,
- metadata,
- revision history.

Manufactured parts reference the design revision they came from but also contain their own actual measured/hidden deviations.

## 17. Manufacturing reproducibility

A process plan should be versionable.

A part should know:
- design revision,
- stock batch,
- machine,
- tooling,
- process plan revision,
- operator/automation mode,
- manufacturing timestamp/sequence,
- inspection results.

This lets a player answer:

> Why were the last five rings worse than the first batch?

## 18. Career AI architecture

NPC competitors should not require full player-interface simulation.

Use hierarchical decision making:

### Strategic
- budget allocation,
- event selection,
- workshop upgrades,
- supplier choice,
- sponsor choice.

### Engineering
- architecture selection,
- design-family iteration,
- material choice,
- manufacturing-quality target.

### Tactical pre-match
- choose hardware,
- maintenance,
- launch setup.

All NPC designs ultimately resolve to normal physical parts and assemblies.

No hidden combat stat bonuses.

## 19. NPC engineering approximation

NPC design search can use:
- templates,
- parameter optimization,
- genetic/evolutionary search,
- heuristics,
- cached simulation results,
- reduced-fidelity simulation.

Only the final hardware needs full match fidelity.

This enables a large ecosystem without simulating thousands of CAD users click-by-click.

## 20. Job system

The game will likely benefit from asynchronous computational jobs for:
- mesh generation,
- CAD rebuilds,
- structural analysis,
- aerodynamic analysis,
- batch simulation,
- NPC optimization,
- telemetry reduction.

The architecture should avoid blocking the main render loop on expensive engineering calculations.

Jobs must still be deterministic/reproducible where required.

## 21. Threading policy

Keep authoritative mutation controlled.

Potential model:
- simulation thread owns match state,
- render thread consumes snapshots,
- worker pool performs derived/offline computations,
- career simulation advances through scheduled jobs outside active matches.

Avoid shared mutable physics state across arbitrary worker threads.

## 22. Precision

Because parts are small and RPM can be high, numerical precision needs deliberate testing.

Requirements:
- stable small-scale contact,
- high angular velocity,
- low drift,
- robust gyroscopic behavior.

Do not assume default engine physics settings are sufficient.

A technical spike must validate this before engine lock-in.

## 23. Physics engine strategy

Three broad strategies are possible:

### Engine physics extended heavily
Fastest integration, but risk of fighting black-box solver limits.

### Dedicated third-party rigid-body library
More control and headless use, still avoids writing everything from scratch.

### Custom specialized mechanical solver
Maximum control, highest development cost and risk.

Likely direction: a proven rigid-body/contact foundation with **custom domain-specific layers** for everything that makes BayBlade unique.

The final choice belongs in the technology-stack decision, not this design spec.

## 24. CAD strategy

The CAD feature set does not require implementing an industrial general-purpose CAD kernel on day one.

Possible staged architecture:
- top-specific parametric primitives,
- constrained sketches,
- rotational features,
- booleans,
- assemblies,
- later generalization.

The internal design representation should leave room for deeper CAD without requiring it immediately.

## 25. Data-driven content

Prefer external data definitions for:
- materials,
- machines,
- tools,
- suppliers,
- regulations,
- tournament classes,
- commercial parts.

Benefits:
- iteration without code changes,
- balancing,
- modding potential,
- easier testing.

## 26. Modding

Modding is not currently a locked requirement, but architecture should avoid making it impossible.

Data-driven content naturally enables future support for:
- materials,
- premade parts,
- events,
- regulations,
- suppliers,
- machines,
- arenas.

Arbitrary simulation-code mods are a separate future decision.

## 27. Debug tooling

The game needs unusually strong developer tools.

Required debug views:
- collision shapes,
- center of mass,
- inertia axes,
- contact points,
- impulses,
- angular momentum,
- joint forces,
- fatigue zones,
- thermal field,
- crack state,
- surface wear,
- aero forces,
- solver timing,
- substep count.

A simulation-heavy game without excellent debug visualization will become impossible to tune.

## 28. Regression tests

Automated tests should include:
- materials serialization,
- mass property generation,
- CAD parameter stability,
- manufacturing deviation bounds,
- free-spin decay,
- contact energy conservation limits,
- gyro stability,
- fracture event consistency,
- thermal convergence,
- save/load identity,
- replay synchronization.

Simulation changes should not silently rewrite the entire game.

## 29. Profiling

Performance instrumentation should report:
- contact count,
- rigid bodies,
- active constraints,
- debris bodies,
- simulation substeps,
- solver time,
- thermal time,
- damage time,
- render time,
- geometry generation time.

A match should make it obvious what is expensive.

## 30. Technology stack decision criteria

When choosing the actual stack, evaluate:

1. high-RPM rigid-body stability,
2. custom contact-model access,
3. headless simulation,
4. geometry/CAD integration,
5. runtime procedural mesh support,
6. job/threading control,
7. replay/debug tooling,
8. desktop performance,
9. asset pipeline,
10. iteration speed for a hobby/small team,
11. long-term maintainability.

Graphics quality alone is not enough to choose the engine.

## 31. Core architectural north star

**The exact same physical object should be understandable across its entire life:**

CAD design  
→ manufacturing process  
→ inspection  
→ assembly  
→ launch  
→ collision  
→ damage  
→ failure analysis  
→ repair  
→ next match  
→ retirement on the workshop shelf.

If the architecture breaks that chain into unrelated fake stat systems, it has failed the design.
