# Physics & Simulation

## 1. Simulation goal

BayBlade should create the impression of a serious mechanical simulation without requiring every physical phenomenon to be solved at industrial-analysis cost.

The target is a **hybrid multiphysics simulation**:

- high-frequency rigid-body dynamics for motion and contact,
- reduced-order models for bearings, fasteners, deformation, fatigue, heat, wear, fracture, and aerodynamics,
- event-driven structural changes when parts loosen, bend, crack, chip, or fail,
- persistent state carried from match to match.

The simulation must prefer **causal consistency** over fake complexity.

A player should be able to ask "why did this fail?" and receive an answer that corresponds to actual simulated state.

## 2. Coordinate and unit policy

Use SI units internally.

Recommended canonical units:
- distance: meter,
- mass: kilogram,
- time: second,
- force: newton,
- torque: newton-meter,
- angular velocity: radians/second,
- temperature: kelvin internally, Celsius in UI,
- pressure/stress: pascal,
- energy: joule.

UI can present friendlier derived units such as:
- millimeters,
- grams,
- RPM,
- micrometers,
- kilonewtons,
- gigapascals.

Do not mix arbitrary "game units" into the mechanical core.

## 3. Assembly model

A top is an assembly graph rather than one monolithic rigid body.

Possible components:
- upper body / attack ring,
- mass ring,
- inserts,
- core,
- shaft,
- bearing races,
- rolling elements or simplified bearing element,
- tip,
- damping layers,
- washers,
- fasteners,
- launcher interface.

Each component owns persistent physical state:
- geometry,
- mass,
- center of mass,
- inertia tensor,
- material,
- temperature,
- wear,
- plastic deformation,
- accumulated fatigue,
- crack state,
- surface state,
- manufacturing deviations.

Connections between parts also own state:
- preload,
- fit,
- friction,
- clearance,
- stiffness,
- damping,
- temperature,
- loosening,
- damage.

## 4. Multirate stepping

Not every subsystem should run at the same rate.

Suggested conceptual stepping:

### Very high frequency
Used for:
- collision detection,
- contact impulse resolution,
- tip/arena contact,
- critical bearing and joint response.

### Physics tick
Used for:
- rigid-body integration,
- gyroscopic motion,
- precession,
- assembly constraints,
- aerodynamic loads.

### Lower-frequency material tick
Used for:
- heat conduction,
- wear accumulation,
- fatigue accumulation,
- lubricant state,
- fastener loosening,
- surface evolution.

### Event driven
Used for:
- fracture,
- connection separation,
- chipped geometry,
- debris spawning,
- permanent bend threshold crossing,
- bearing seizure,
- catastrophic burst.

Adaptive substepping should increase fidelity around violent impacts and high-speed instability.

## 5. Rotational dynamics

The game must model:
- full inertia tensor,
- angular momentum,
- torque,
- gyroscopic stability,
- precession,
- nutation/wobble,
- shifting center of mass after damage,
- asymmetric mass distribution,
- imbalance,
- changing inertia after fracture or debris loss.

The top's behavior should emerge from actual geometry and component mass placement rather than a fixed "stamina" value.

## 6. Contact model

Contacts should account for:
- local surface normal,
- relative velocity,
- material pair,
- friction curve,
- restitution,
- compliance,
- contact patch approximation,
- temperature,
- surface contamination,
- surface wear,
- local damage.

Friction should support more than one constant coefficient.

Useful regimes:
- static / sticking,
- sliding,
- rolling,
- transitional behavior,
- speed-dependent friction,
- temperature-dependent friction.

Tip behavior is particularly sensitive and deserves a specialized contact model.

## 7. Collision energy and local load estimation

For each significant impact, capture:
- contact location,
- relative velocity,
- impulse,
- normal and tangential load,
- transferred angular momentum,
- estimated local pressure,
- estimated strain energy,
- duration,
- temperature contribution.

This becomes input to:
- elastic response,
- plastic deformation,
- crack/fatigue models,
- fastener loosening,
- damage visualization,
- telemetry.

## 8. Deformation model

Do not attempt full real-time finite-element analysis for every part.

Use a layered approximation.

### Layer 1: elastic compliance
Small transient deformation affects impact timing and restitution.

### Layer 2: permanent local deformation
When estimated local stress exceeds material-dependent yield behavior:
- create dent/bend state,
- alter local collision geometry,
- modify balance,
- change stress concentration.

### Layer 3: component-level bending modes
Long thin or cantilevered features can carry a small number of precomputed or generated deformation modes.

### Layer 4: structural failure
When accumulated damage crosses a failure criterion:
- crack,
- chip,
- split,
- separate,
- fragment.

The approximation should preserve the consequences players expect from geometry and material choice.

## 9. Stress proxy system

Each manufactured component can maintain a reduced structural representation.

Possible representation:
- stress zones / cells tied to geometry,
- local thickness,
- curvature,
- notch factors,
- fastener holes,
- interfaces,
- high-risk edges,
- user-defined inserts.

During impacts, loads are distributed to nearby zones.

Each zone can track:
- peak stress proxy,
- mean stress,
- alternating stress,
- plastic strain proxy,
- fatigue damage,
- temperature,
- crack initiation probability/state.

CAD analysis can use a higher-resolution offline version of the same model.

## 10. Fatigue

Fatigue is persistent across matches.

A practical model can use:
- material S-N curves or simplified equivalents,
- mean-stress correction,
- cycle counting approximation,
- stress concentration multipliers,
- temperature effects,
- surface-finish effects,
- manufacturing-defect modifiers.

Fatigue damage should not be perfectly predictable unless the player has excellent material data and inspection.

A part can look fine while approaching failure.

## 11. Crack model

Cracks should be explicit persistent defects.

Track:
- origin,
- direction,
- length,
- opening mode approximation,
- growth rate,
- detectability,
- effect on stiffness,
- effect on stress concentration.

Cracks may:
- remain stable,
- grow slowly,
- grow under repeated impacts,
- jump during overload,
- trigger brittle fracture.

Inspection equipment determines whether the player knows a crack exists.

## 12. Fracture and debris

When a component fractures:
- alter or split collision geometry,
- conserve momentum as closely as practical,
- generate one or more physically meaningful fragments,
- preserve important mass distribution,
- spawn debris if above a relevance threshold.

Debris can interact physically with:
- tips,
- tops,
- arena surface,
- walls.

Very tiny debris can be represented statistically or visually to protect performance.

Large chunks, screws, inserts, or broken teeth should remain physical objects.

## 13. Bearings

Bearings need dedicated simulation because they strongly influence high-RPM behavior.

Possible state:
- type,
- geometry,
- preload,
- clearance,
- lubrication,
- contamination,
- temperature,
- race condition,
- wear,
- vibration,
- misalignment.

Behavior can affect:
- frictional torque,
- heat generation,
- shaft motion,
- vibration,
- noise,
- seizure risk,
- fatigue.

A damaged bearing should be able to turn a previously smooth top into a vibrating disaster.

## 14. Fasteners and joints

Fasteners may track:
- preload,
- friction,
- tightening quality,
- temperature,
- cyclic load,
- loosening,
- permanent stretch,
- thread damage.

Repeated impacts can reduce clamp load.

A loose connection can:
- introduce play,
- change balance,
- amplify vibration,
- increase local stress,
- eventually separate.

## 15. Thermal simulation

Heat sources include:
- bearing friction,
- tip friction,
- sliding contact,
- plastic deformation,
- repeated impacts,
- machining history where relevant.

Model:
- component temperature,
- contact hot spots,
- conduction between connected parts,
- convection/radiation approximation,
- thermal expansion,
- temperature-dependent material behavior.

Temperature can change:
- bearing clearance,
- friction,
- lubricant viscosity,
- damping,
- strength,
- wear rate,
- fit.

## 16. Wear

Wear should modify actual mechanical behavior.

Wear modes may include:
- abrasive wear,
- adhesive wear,
- tip flattening,
- edge rounding,
- coating loss,
- race damage,
- fretting at joints.

Persistent wear can change:
- geometry,
- roughness,
- balance,
- friction,
- stress concentrations.

## 17. Arena surface

The arena surface is not a single coefficient.

Track spatially varying:
- material,
- roughness,
- compliance,
- temperature,
- deposits,
- scratches,
- grooves,
- chips,
- contamination,
- wear.

For performance, use a surface field or tiled data structure rather than per-triangle simulation state.

Significant damage can modify collision geometry.

## 18. Aerodynamics

Aerodynamics are a full design consideration, but should use practical real-time approximations.

Relevant effects:
- skin/friction drag,
- pressure drag,
- rotational pumping,
- geometry-dependent drag,
- lift/downforce-like axial effects,
- asymmetric aero loads,
- drag changes with wobble,
- heat transfer effects.

A possible implementation path:
1. derive aerodynamic descriptors from geometry,
2. precompute or approximate coefficients across angular velocity and attitude,
3. interpolate at runtime,
4. allow higher-end simulation software to estimate descriptors more accurately.

The game should not require real-time CFD.

## 19. Launcher physics

Launchers have physical properties:
- gear ratio,
- rotational inertia,
- mechanical efficiency,
- stiffness,
- maximum torque,
- pull length,
- cord/rack behavior,
- release consistency,
- alignment error,
- wear.

Manual input maps to physical launch conditions rather than directly setting RPM.

Output launch state includes:
- angular velocity,
- translational velocity,
- orientation,
- angular misalignment,
- lateral position,
- release variation.

## 20. Manufacturing deviations

The manufactured object is not necessarily identical to CAD.

Possible deviations:
- dimensional error,
- runout,
- flatness error,
- concentricity error,
- surface roughness,
- density variation,
- residual stress,
- heat-treatment variability,
- tool marks,
- misaligned inserts,
- imbalance.

These deviations become real simulation inputs.

Better manufacturing reduces distributions and uncertainty rather than magically adding "quality."

## 21. Material variability

A nominal material grade has a property distribution.

Supplier data may include:
- certified range,
- batch,
- provenance,
- heat treatment,
- contamination,
- uncertainty.

Cheap or shady suppliers may provide less certainty.

The simulation can sample a hidden "true" material state while exposing only what the player can measure or what certification claims.

## 22. Measurement uncertainty

Every measurement has:
- range,
- resolution,
- precision,
- calibration state,
- systematic error,
- random error.

Better instruments improve confidence.

This matters because the player's model of the machine can differ from the machine's hidden true physical state.

## 23. Telemetry

The simulation should emit structured telemetry.

Core channels:
- time,
- position,
- orientation,
- linear velocity,
- angular velocity / RPM,
- angular momentum,
- energy,
- wobble angle,
- tip contact state,
- contact impulses,
- bearing temperature,
- component temperatures,
- vibration,
- damage events,
- fatigue state,
- crack events,
- debris events,
- arena contacts,
- aerodynamic losses,
- frictional losses.

Telemetry should be recorded independently of rendering.

## 24. Replay and failure analysis

Replays should support:
- pause,
- frame stepping,
- variable slow motion,
- free camera,
- contact markers,
- force vectors,
- stress overlays,
- thermal overlays,
- crack markers,
- RPM graph,
- energy graph,
- damage timeline,
- synchronized telemetry cursor.

Failure analysis should be generated from actual events, for example:

> Crack initiated at outer-ring fastener bore after repeated high-cycle loading. A later overload event increased crack length beyond the remaining ligament tolerance, causing final fracture.

The explanation system must never invent causes that the simulation did not record.

## 25. Determinism

Where practical, matches should be reproducible from:
- assembly state,
- arena state,
- launch inputs,
- simulation version,
- random seed,
- hidden manufacturing state.

This is valuable for:
- debugging,
- replay,
- regression testing,
- comparing design revisions.

Perfect floating-point determinism across every platform is optional, but deterministic-enough development tooling is highly desirable.

## 26. Fidelity tiers

The architecture should support different fidelity contexts.

### Runtime match
Fast enough for interactive simulation.

### Replay analysis
Can compute additional derived metrics after the fact.

### Workshop simulation
Can run slower, higher-resolution design analysis.

### Offline engineering analysis
Potentially much slower and more detailed for endgame tooling.

This avoids forcing every feature into the real-time loop.

## 27. Simulation validation

The project should include mechanical regression scenes:
- free-spin decay,
- gyroscopic precession,
- known tip friction tests,
- symmetric collision,
- off-center collision,
- ring-out trajectory,
- balance sensitivity,
- bearing heat test,
- crack growth test,
- fastener loosening test,
- debris interaction,
- thermal expansion test.

Each test should have tolerance bands rather than relying on visual inspection.

## 28. Performance principle

Spend computation where the player can observe consequences.

Do not simulate ten million microscopic chips individually if a statistical roughness change produces the same macroscopic behavior.

Do simulate the 8 g tungsten insert that just tore free and is bouncing toward the opponent's tip.

That distinction is fundamental to making the intended depth computationally practical.
