# Roadmap

## 1. Roadmap philosophy

This roadmap intentionally does **not** define the final scope of a numbered first release.

The immediate purpose is to reduce technical risk in the correct order before committing to production scale.

BayBlade has several expensive systems. They should not all be built simultaneously.

## 2. Phase 0: architecture and technology selection

Goals:
- choose engine/runtime,
- choose language boundaries,
- select rigid-body/contact foundation,
- prove headless simulation path,
- establish repository structure,
- define serialization/data formats,
- establish test strategy.

Exit criteria:
- technology can support high angular velocities at small physical scale,
- custom contact/material behavior is accessible,
- simulation can run independently of rendering,
- procedural geometry path is credible.

## 3. Phase 1: rotational physics laboratory

Build a developer-only simulation lab.

Prove:
- stable spinning top,
- realistic free-spin decay,
- precession,
- wobble,
- tip contact,
- arena curvature,
- off-center collision,
- ring-out,
- configurable mass distribution,
- manual/defined launch state,
- telemetry.

No career systems.

No elaborate art.

The purpose is to answer:
**Can watching two simulated machines collide already be fascinating?**

## 4. Phase 2: assemblies and persistent physical state

Add:
- multi-component top,
- joints,
- bearing model,
- fastener model,
- temperature,
- wear,
- manufacturing imbalance,
- persistent part identity.

Prove that nominally identical assemblies can behave differently for physically explainable reasons.

## 5. Phase 3: damage and failure

Add:
- structural proxy,
- yielding,
- permanent bend,
- fatigue,
- cracks,
- fracture,
- debris,
- failure events,
- failure-analysis replay.

Exit criterion:
a catastrophic failure can be traced from impact history to a specific physical cause.

## 6. Phase 4: arena and environment fidelity

Add:
- richer arena geometry,
- spatial surface state,
- wear,
- grooves,
- deposits,
- debris persistence,
- wall/containment interaction,
- arena material variation.

## 7. Phase 5: aerodynamic and advanced thermal layer

Add:
- geometry-dependent drag,
- wobble-dependent aero,
- thermal coupling,
- lubricant/clearance behavior,
- thermal expansion,
- more advanced friction response.

Validate that these systems materially affect design decisions before increasing complexity further.

## 8. Phase 6: design representation

Create the first structured custom-part system.

Start with domain-specific features:
- rotational profiles,
- rings,
- radial patterns,
- insert pockets,
- holes,
- tip profiles,
- assemblies.

Generate:
- render mesh,
- collision geometry,
- mass properties,
- structural proxy.

Do not begin by cloning a full industrial CAD package.

## 9. Phase 7: manufacturing truth

Separate ideal design from manufactured object.

Add:
- material batches,
- dimensional variation,
- surface finish,
- runout,
- imbalance,
- process history,
- inspection state.

Build the hidden-truth/player-knowledge architecture.

## 10. Phase 8: starter workshop loop

Implement early manual fabrication:
- sanding,
- drilling,
- gluing,
- crude balancing,
- assembly.

Add:
- cheap tools,
- primitive measurement,
- raw stock,
- consumables,
- damaged inventory.

Goal:
make bad early engineering entertaining and understandable.

## 11. Phase 9: precision workshop

Add:
- lathe,
- mill,
- tooling,
- process parameters,
- tolerances,
- proper metrology,
- dynamic balancing,
- heat treatment,
- rework.

This is where the player begins manufacturing serious custom hardware.

## 12. Phase 10: automation and advanced CAD

Add:
- CNC,
- reusable process plans,
- automated inspection,
- batch production,
- richer CAD features,
- assemblies,
- tolerance annotations,
- higher-end design analysis.

The player should feel a dramatic reduction in repetitive labor.

## 13. Phase 11: competition framework

Add:
- event definition,
- technical classes,
- inspections,
- brackets,
- elimination rules,
- event calendar,
- results history.

Keep competition logic data-driven.

## 14. Phase 12: career economy

Add:
- money,
- expenses,
- prize winnings,
- workshop upgrades,
- suppliers,
- used market,
- machine maintenance,
- financial recovery paths.

Avoid adding sponsorship and manufacturing business until the base economy is understandable.

## 15. Phase 13: persistent rivals

Add:
- competitor identity,
- budgets,
- inventories,
- workshop capability,
- design preferences,
- event participation,
- persistent career history.

Then add:
- counter-development,
- strategy adaptation,
- retirement,
- new entrants.

## 16. Phase 14: marketplace and technology diffusion

Add:
- player products,
- rival products,
- adoption,
- licensing,
- batch quality,
- reputation,
- copied concepts,
- market trends.

Prove the key fantasy:
**the player can lose to technology they helped introduce.**

## 17. Phase 15: sponsorship and professional sport

Add:
- sponsor relationships,
- obligations,
- professional events,
- manufacturer involvement,
- advanced rulebooks,
- larger venues,
- broadcast presentation.

## 18. Phase 16: evolving regulation ecosystem

Add:
- seasonal technical changes,
- safety-driven rule changes,
- class evolution,
- advance notice,
- AI adaptation,
- obsolete-design pressure.

Rule changes should force creativity without feeling arbitrary.

## 19. Phase 17: side leagues and experimental content

Once the grounded core is strong, add:
- weird arenas,
- oversized classes,
- prototype rules,
- destructive exhibitions,
- unusual materials,
- experimental competition formats.

This is controlled lunacy built on top of a coherent simulator.

## 20. Phase 18: long-career world depth

Expand:
- rival career transitions,
- manufacturers,
- retired competitors,
- supplier evolution,
- historical records,
- event archives,
- dynamic market stories,
- late-game near-future materials and machinery.

## 21. Cross-cutting tracks

These do not belong to only one phase.

### Replay/telemetry
Start immediately and grow continuously.

### Testing
Every simulation feature ships with regression coverage.

### UI
Expose only as much complexity as the player's current tools justify.

### Art
Begin with functional prototypes, then concentrate production quality on mechanical assets.

### Audio
Add early because spin, bearing, impact, and wobble sounds are important diagnostic feedback.

### Performance
Profile from the first high-frequency physics prototype.

## 22. Development risk order

Highest-risk questions should be answered first:

1. Can we stably simulate high-RPM tops at this scale?
2. Can contacts look and feel violent without becoming numerically unstable?
3. Can reduced-order damage/fatigue models produce believable failure?
4. Can procedural design geometry feed all required representations?
5. Can the simulation remain fast enough with debris and component assemblies?
6. Can NPC engineering use reduced fidelity while obeying the same world?
7. Can the workshop complexity remain understandable?

Career content is large, but these are the technical existential risks.

## 23. Avoided trap

Do not build:
- 50 tournaments,
- 200 commercial parts,
- sponsor dialogue,
- character customization,
- giant workshop environments

before the mechanical core is proven.

Content cannot rescue uninteresting spinning physics.

## 24. Production principle

At each stage, prefer a small system that produces real emergent behavior over a large scripted imitation.

BayBlade should grow outward from its physics, not inward from a feature checklist.
