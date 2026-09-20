# Workshop & Manufacturing

## 1. Workshop progression

The workshop is a physical representation of the player's increasing capability.

It evolves roughly through:

1. desk / bedroom tinkering,
2. improvised garage bench,
3. serious hobby workshop,
4. precision machining shop,
5. professional engineering workshop,
6. advanced laboratory and automated production cell.

Progress should be visible in the space.

Old equipment can remain in the room or be replaced, sold, stored, or kept for sentimental reasons.

## 2. Early-game fabrication

Early fabrication should feel manual and imperfect.

Possible operations:
- sanding,
- filing,
- drilling,
- cutting,
- gluing,
- clamping,
- adding washers,
- adding weights,
- trimming plastic,
- crude polishing,
- hand assembly,
- improvised balancing.

These can use interactive minigames where player execution influences quality.

Examples:
- drill angle affects hole alignment,
- sanding pressure/time affects geometry,
- glue placement affects mass distribution,
- hand tightening affects fastener preload,
- balancing by trial and error consumes time and may overshoot.

Early-game manual work should be charmingly bad, not frustratingly unusable.

## 3. Automation curve

Manual processes gradually become assisted and automated.

A useful progression:
- fully manual,
- jigs and fixtures,
- powered tools,
- basic machine tools,
- digital readouts,
- CNC,
- automated probing,
- recipe-based process control,
- robotic or near-automatic workflow execution.

Once a player has demonstrated competence and bought the appropriate equipment, repetitive tasks should become automatable.

Depth should remain available without forcing repetitive labor.

## 4. Machines

Potential machines and equipment:

### Basic
- vise,
- drill press,
- rotary tool,
- bench grinder,
- belt sander,
- polishing wheel.

### Machining
- manual lathe,
- manual mill,
- CNC lathe,
- CNC mill,
- precision grinder,
- EDM-like advanced equipment where justified.

### Thermal/process
- heat-treatment furnace,
- curing oven,
- quench setup,
- coating equipment,
- cleaning system.

### Metrology
- calipers,
- micrometers,
- dial indicators,
- surface plate,
- precision scale,
- tachometer,
- dynamic balancer,
- profilometer,
- hardness tester,
- optical microscope,
- high-speed camera,
- thermal camera,
- vibration analyzer,
- ultrasonic inspection,
- X-ray / CT inspection in high-end play.

### Test rigs
- bearing bench,
- spin chamber,
- overspeed chamber,
- impact rig,
- fatigue rig,
- material tensile/compression tester,
- destructive burst test fixture.

## 5. Machine properties

Machines are not simple unlock flags.

They can have:
- working envelope,
- rigidity,
- spindle power,
- maximum RPM,
- backlash,
- runout,
- thermal stability,
- controller quality,
- repeatability,
- achievable surface finish,
- probing capability,
- tool capacity,
- maintenance state.

A cheap used machine can be useful but imperfect.

Players can:
- calibrate,
- repair,
- upgrade,
- replace components,
- add DRO/probing,
- improve fixturing,
- maintain lubrication.

## 6. Tooling

Tool choice matters.

Tool properties:
- geometry,
- coating,
- material,
- diameter,
- flute count,
- sharpness,
- wear,
- temperature limits,
- suitable materials.

Manufacturing can fail because the player owns the machine but not the right tooling.

This prevents "bought CNC = can make anything."

## 7. Stock and suppliers

Raw material comes from suppliers.

Stock has:
- nominal material grade,
- form,
- dimensions,
- certification,
- batch,
- property uncertainty,
- price,
- lead time,
- availability.

Supplier types can include:
- local hardware store,
- hobby vendor,
- industrial metal supplier,
- specialist ceramic supplier,
- aerospace surplus,
- auction,
- scrap dealer,
- sponsor,
- shady reseller,
- experimental research partner.

This supports both normal purchasing and occasional goblin-mode finds.

## 8. Process planning

A manufactured part is created through a process plan.

A plan may specify:
- source stock,
- setup,
- workholding,
- machine,
- tool,
- spindle speed,
- feed,
- depth of cut,
- number of passes,
- coolant,
- roughing strategy,
- finishing strategy,
- tolerance target,
- deburring,
- heat treatment,
- coating,
- grinding,
- polishing,
- balancing,
- inspection.

Processes affect the hidden true state of the part.

## 9. Failure during manufacturing

Bad manufacturing choices can create:
- chatter,
- poor finish,
- dimensional error,
- excessive runout,
- broken tools,
- scrapped parts,
- residual stress,
- warping,
- burns,
- cracked brittle materials,
- bad heat treatment,
- bad fit,
- hidden damage.

The game should explain failures using process telemetry and available knowledge.

## 10. CAD

Late-game CAD is a streamlined mechanical CAD environment.

Desired feature set:
- 2D sketches,
- geometric constraints,
- dimensions,
- revolve,
- extrude,
- cut,
- boolean,
- fillet,
- chamfer,
- circular pattern,
- hole features,
- reference geometry,
- assemblies,
- interference checking,
- parameter tables,
- materials,
- tolerance annotation.

Top-specific convenience features should make common geometry fast:
- rotational symmetry helpers,
- radial tooth pattern generator,
- insert pockets,
- balance preview,
- launcher-interface templates,
- tip profile editor.

Players should never need twenty clicks to make a simple ring.

## 11. CAD to manufacturing

CAD describes ideal geometry.

Manufacturing determines actual geometry.

The workflow:

1. design part,
2. assign material,
3. inspect mass properties,
4. check assembly,
5. run optional simulation,
6. choose manufacturing process,
7. manufacture,
8. inspect,
9. accept/rework/scrap,
10. assemble,
11. test.

This separation is crucial.

## 12. Tolerances

Players can eventually specify:
- dimensional tolerance,
- concentricity,
- flatness,
- runout,
- fit class,
- surface finish.

Tighter tolerances:
- cost more time,
- require better machines and inspection,
- increase scrap risk,
- improve repeatability where relevant.

Not every dimension needs extreme precision.

Learning **where precision matters** is gameplay.

## 13. Inspection

Inspection reveals properties rather than improving them.

Examples:
- caliper gives approximate diameter,
- micrometer improves dimensional confidence,
- dial indicator reveals runout,
- profilometer measures roughness,
- dynamic balancer locates imbalance,
- microscope reveals visible cracks,
- ultrasonic inspection reveals internal defects,
- CT can reveal hidden geometry and inclusions.

An unmeasured property still exists.

The player simply does not know it accurately.

## 14. Rework

Parts can often be reworked:
- skim a surface,
- rebore a hole,
- polish,
- rebalance,
- replace an insert,
- add/remove material,
- re-heat-treat where valid.

Rework may:
- save money,
- weaken geometry,
- consume tolerance allowance,
- introduce new uncertainty.

## 15. Assembly

Assembly is also a manufacturing step.

Important variables:
- fastener torque,
- preload,
- thread treatment,
- fit,
- alignment,
- bearing installation,
- lubrication,
- cleanliness,
- shim thickness,
- balance.

Early game may involve manual execution.

Later game can use:
- torque tools,
- jigs,
- presses,
- automated assembly checks.

## 16. Balancing

Balancing deserves a dedicated loop.

Progression:
- eyeballing,
- simple static balance,
- trial-and-error mass correction,
- dynamic balancer,
- multi-plane correction,
- automated balance workflow.

Corrections can include:
- removing material,
- adding mass,
- changing insert weight,
- replacing parts,
- rotating components relative to each other.

Perfect balance is difficult and unnecessary in every design.

## 17. Testing

Testing should be a first-class activity rather than a hidden stat check.

Possible tests:
- free-spin,
- controlled launch,
- overspeed,
- vibration sweep,
- bearing endurance,
- thermal soak,
- impact,
- repeated impact,
- fatigue cycling,
- surface friction,
- destructive burst.

Testing consumes:
- time,
- wear,
- electricity,
- stock,
- sometimes the tested part itself.

Destructive testing should be valuable precisely because it destroys something.

## 18. Knowledge from testing

Tests produce data only if the player has instrumentation capable of recording it.

Example early result:

> Failed after a loud vibration and broke near the outer ring.

Later result:

> 1× rotational resonance crossed at 16,420 RPM. Radial vibration rose from 0.31 mm/s RMS to 8.4 mm/s RMS. Final crack initiated at the second insert pocket.

The physical event is the same kind of event. The player's ability to understand it improves.

## 19. Simulation workstation

Digital engineering tools progress like physical tools.

Capabilities may include:
- mass-property calculator,
- balance predictor,
- simple collision estimator,
- structural stress proxy,
- thermal analysis,
- fatigue estimate,
- aerodynamic estimate,
- launch simulation,
- probabilistic tolerance analysis,
- full virtual match batches.

Accuracy depends on:
- software capability,
- compute,
- geometry fidelity,
- material data,
- measured part data,
- known defects,
- model assumptions.

## 20. Production workflows

Late game supports reusable workflows.

Example:

**Titanium Attack Ring v7**
1. saw stock,
2. CNC rough,
3. stress relief,
4. CNC finish,
5. deburr,
6. surface grind,
7. polish selected faces,
8. dynamic balance,
9. ultrasonic inspect,
10. final dimensional inspection.

The player can:
- save recipes,
- batch produce,
- assign acceptable tolerances,
- define inspection gates,
- reject or rework failed pieces.

Automation is earned through equipment and process maturity.

## 21. Selling parts

Player-created components can become products.

The player can:
- name a design,
- choose revision,
- manufacture batches,
- set pricing,
- set quality targets,
- publish specs,
- sell directly,
- license designs.

Customer experience depends on actual manufactured quality.

Poor batches can hurt reputation.

Successful products can spread through the competitive ecosystem.

## 22. Design revision history

Every custom design should support revisions.

Examples:
- AR-01 Rev A
- AR-01 Rev B
- AR-02 Prototype 7

Track:
- geometry changes,
- material changes,
- manufacturing recipe,
- test results,
- failures,
- competition history.

The game should make iteration legible.

## 23. Physical inventory

Important physical items should exist persistently:
- raw stock,
- tools,
- parts,
- assemblies,
- damaged parts,
- trophies,
- retired tops.

The workshop can display history.

A destroyed championship ring should be something the player can put on a shelf rather than having it vanish into an abstract inventory counter.

## 24. Workshop UX principle

The workshop is walkable, but tedious actions should collapse into focused interfaces when appropriate.

Good:
- walk to the lathe,
- interact,
- enter machining interface.

Bad:
- manually walk each screw from a drawer to the bench for every assembly.

Presence matters.

Chore simulation does not.
