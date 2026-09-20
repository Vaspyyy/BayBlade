# BayBlade Design Bible

## 1. Vision

BayBlade is a hardcore spinning-top engineering and career simulation.

The player begins as an ordinary competitor using cheap, premade, toy-scale plastic hardware. Their early "workshop" is barely a workshop at all: hand tools, glue, sanding, drilling, improvised balancing, cheap scales, and trial-and-error experimentation.

Over a long career, the player becomes capable of designing, machining, inspecting, testing, and manufacturing increasingly extreme machines. Late-game hardware may exceed ordinary real-world toy scale and mass, but should remain compact enough to feel like an evolved spinning-top sport rather than giant robots or vehicle combat.

The intended end-state is not "unlock the legendary top." It is becoming good enough at engineering that the player can create their own terrifying championship hardware from first principles.

## 2. Player identity

The player is not a corporation or disembodied manager.

They are a **random person who competes personally**.

They:
- own and improve a workshop,
- design and manufacture parts,
- launch their own machines,
- enter tournaments,
- build relationships and rivalries,
- earn money and reputation,
- take risks with hardware they may genuinely lose.

Later systems can grow around them, but the fantasy remains personal.

## 3. Core match philosophy

### 3.1 No post-launch control

Once the top is released, the player has **no direct control** over it.

There are no:
- steering inputs,
- boosts,
- special attacks,
- magical timing prompts,
- mid-match corrections.

The engineering, setup, and launch are the gameplay.

### 3.2 Physics target

Simulation should aim for physically serious behavior with only slight exaggeration where needed for readability, spectacle, and pacing.

The player should be able to understand a loss in mechanical terms:
- bad launch,
- poor balance,
- thermal fade,
- bearing wear,
- instability,
- resonance,
- material failure,
- unfavorable contact geometry,
- fatigue crack propagation,
- debris interaction,
- surface degradation,
- or simply being out-engineered.

### 3.3 Main competition win conditions

Main career events are elimination-based, not point-based.

A top loses when it:
- stops spinning,
- leaves the legal arena,
- becomes mechanically unable to continue,
- catastrophically fails.

Alternative scoring systems may exist in side leagues or special events, but they are not the identity of the main game.

## 4. Progression philosophy

Progression should be **capability-based** rather than stat-tree-based.

Bad progression:
- "Titanium II unlocked"
- "+12% machining quality"
- "Engineering level 37"

Good progression:
- buy a better lathe,
- gain access to titanium stock,
- acquire tooling that can cut it,
- learn a process that avoids work hardening,
- obtain a better measuring instrument,
- discover your runout is unacceptable,
- rework the process,
- improve balancing,
- build a better part.

New tools reveal new design spaces.

New instruments reveal new truths.

New suppliers reveal new materials and tolerances.

New machines let the player manufacture designs that were previously impossible.

## 5. Customization progression

Early game begins with premade parts and crude modification.

Example early actions:
- swap a body,
- swap a tip,
- add washers,
- glue weights,
- sand contact surfaces,
- drill material away,
- rebalance by trial and error,
- replace cheap bearings,
- salvage parts from damaged tops.

As workshop capability improves, the player gains access to:
- custom shafts,
- custom bearings and bearing fits,
- mass inserts,
- damping layers,
- custom bodies,
- custom tips,
- fastener choices,
- tolerance specification,
- heat treatment,
- finishing processes,
- fully custom geometry,
- complete custom assemblies.

Late game should allow the player to customize essentially every mechanically meaningful part.

## 6. Simulation depth

The intended simulation covers:

- rigid-body dynamics,
- multi-component assemblies,
- rotational inertia,
- gyroscopic behavior,
- precession and wobble,
- contact and friction,
- deformation approximations,
- stress and strain proxies,
- fatigue accumulation,
- crack initiation and propagation,
- fracture,
- heat generation and conduction,
- thermal expansion,
- bearing behavior,
- lubricant degradation,
- fastener loosening,
- wear,
- surface roughness,
- aerodynamic drag and shape effects,
- debris,
- arena surface degradation,
- manufacturing tolerances,
- material variability,
- measurement uncertainty.

The implementation may use approximations and reduced-order models rather than brute-force engineering solvers. The **player-facing behavior** should remain coherent and mechanically explainable.

## 7. Failure is content

Damage is persistent.

Possible outcomes include:
- bent rings,
- cracked plastics,
- chipped ceramics,
- dented metal,
- loosened fasteners,
- bearing play,
- worn tips,
- surface galling,
- fatigue cracks,
- heat damage,
- lubricant breakdown,
- balance drift,
- resonance-induced damage,
- debris damage,
- structural fragmentation.

A favorite championship machine may slowly become worse and eventually need:
- repair,
- remachining,
- retirement,
- or complete rebuild.

This gives individual machines history.

## 8. Launch system

Launch can be:
- assisted,
- manually skill-based,
- or partially automated depending on equipment and competition rules.

Manual launch can affect:
- pull speed,
- launch energy,
- launch angle,
- release timing,
- lateral offset,
- repeatability.

Assistance should make the game accessible, but a skilled player using manual launching should be able to achieve better consistency or deliberately unusual launch states.

## 9. Arena philosophy

Career competition uses legitimate standardized or semi-standardized arenas with meaningful differences in:
- curvature,
- diameter,
- wall height,
- pocket geometry,
- surface material,
- compliance,
- roughness,
- temperature,
- wear state.

Side leagues and events may use experimental or active arenas.

Arena surfaces can accumulate:
- scratches,
- grooves,
- deposits,
- chips,
- debris,
- localized damage.

This can alter traction and behavior during and between matches where rules permit.

## 10. Material philosophy

Materials should be mechanically distinct rather than arranged as a simple tier list.

Relevant properties may include:
- density,
- elastic modulus,
- yield behavior,
- hardness,
- toughness,
- brittleness,
- thermal conductivity,
- thermal expansion,
- friction,
- wear resistance,
- fatigue performance,
- machinability,
- cost,
- consistency,
- supplier quality.

Late-game materials can include near-future or exotic engineering materials, but they should remain grounded in plausible physical behavior.

## 11. Measurement and knowledge

The player does not automatically know everything about a part.

At first:
- "looks smooth"
- "seems balanced"
- "bearing sounds rough"

Later:
- measured surface roughness,
- radial runout,
- vibration spectra,
- bearing temperature,
- hardness,
- balance error,
- crack location,
- dimensional maps,
- stress history,
- thermal history.

Instrumentation converts vague observations into quantitative engineering knowledge.

## 12. CAD philosophy

The late-game design system should approach a streamlined in-game mechanical CAD environment.

Desired capabilities:
- sketches,
- constraints,
- extrusions,
- revolves,
- booleans,
- fillets,
- chamfers,
- circular patterns,
- measurements,
- assemblies,
- material assignment,
- tolerance specification,
- mass-property visualization,
- interference checks,
- manufacturability checks,
- simulation previews.

The interface should help the player make a simple round part quickly while still allowing deep design work.

## 13. Manufacturing philosophy

Manufacturing is a real system.

Relevant choices can include:
- stock material,
- stock dimensions,
- machine,
- tool,
- workholding,
- spindle speed,
- feed rate,
- passes,
- coolant,
- tolerance target,
- heat treatment,
- finishing,
- inspection.

Poor choices can cause:
- bad finish,
- dimensional error,
- excessive tool wear,
- part warping,
- chatter,
- tool breakage,
- damaged stock,
- hidden defects.

Automation unlocks gradually.

Late game supports reusable manufacturing workflows and batch production.

## 14. Simulation versus prototyping

Digital simulation becomes more useful over time, but never becomes perfectly omniscient.

Its accuracy can depend on:
- material data quality,
- measurement quality,
- solver sophistication,
- computing hardware,
- mesh/model resolution,
- known defects,
- manufacturing uncertainty.

Real prototypes remain valuable because actual manufactured parts contain imperfections and chaotic interactions that simulations may miss.

## 15. Economy and business

The player can earn money through:
- tournament winnings,
- sponsorship,
- contracts,
- exhibitions,
- part sales,
- design licensing,
- custom work.

Selling successful designs has consequences.

NPC competitors may:
- buy player parts,
- copy design ideas,
- adopt player hardware,
- develop counters,
- compete against the player using technology the player helped popularize.

The marketplace should feed back into competition.

## 16. Rival ecosystem

NPC competitors should participate in the same broad engineering world as the player.

They can have:
- budgets,
- suppliers,
- workshops,
- strengths,
- weaknesses,
- preferred strategies,
- signature designs,
- debts,
- sponsors,
- careers,
- retirements,
- team changes,
- businesses.

Important rivals persist for years.

Some amateurs can become champions.

Some champions can go broke.

Some retired competitors can become manufacturers.

New competitors enter the world over time.

## 17. Competition structure

The career uses a seasonal, open-calendar ecosystem with:
- local events,
- regional events,
- national events,
- professional championships,
- invitationals,
- exhibitions,
- side leagues,
- qualifying requirements,
- rankings,
- sponsor obligations,
- off-season development,
- engineering rule changes.

The player chooses which risks to take.

## 18. Regulations

Competition classes have technical regulations.

Examples:
- maximum mass,
- maximum diameter,
- material restrictions,
- allowed fasteners,
- launch-energy limits,
- tip restrictions,
- safety factors,
- containment requirements,
- inspection rules.

Rulebooks can evolve between seasons as technology and safety incidents change the sport.

This creates engineering churn rather than a single solved meta.

## 19. Difficulty and financial risk

The economy is intentionally capable of punishing reckless decisions.

Destroyed parts are genuinely lost.

Expensive mistakes matter.

A player can put themselves into financial trouble by:
- overbuilding too early,
- entering hardware they cannot afford to lose,
- destroying prototypes,
- buying machines before they can support them,
- trusting bad suppliers,
- mismanaging production.

The game should avoid cheap "game over because of one bad roll" design, but real financial danger is part of the fantasy.

## 20. Long-term scale

A first serious career should support **100+ hours** of progression.

The simulation and economy should remain open-ended after the player reaches elite competition.

The game should not end because the player unlocked the final material.

Endgame is continued engineering.

## 21. Presentation direction

Target style: **stylized realism leaning heavily into hyper-detailed engineering presentation**.

People and environments do not need photorealistic production cost.

Mechanical objects should receive the visual budget:
- machining marks,
- grease,
- scratches,
- impact dents,
- heat discoloration,
- polished edges,
- chipped coatings,
- debris,
- sparks,
- thermal overlays,
- slow-motion deformation,
- microscopic wear.

The workshop should be walkable, but interaction should use menus or focused interfaces where full physical manipulation would become tedious.

## 22. Safety philosophy

The game may warn the player about dangerous designs.

It should not generally prohibit them.

Example:
- outer ring rated for 14,000 RPM,
- player configures 24,000 RPM,
- calculated safety factor 0.61,
- UI warns clearly,
- **LAUNCH remains available**.

The simulator knows physics, not mercy.

## 23. Design north star

Every major system should answer at least one of these questions:

1. Does this make engineering decisions matter?
2. Does this create understandable physical consequences?
3. Does this make progression feel earned through capability?
4. Does this create stories around specific machines, rivals, or failures?
5. Does this make testing and iteration satisfying?

If not, it probably does not belong in BayBlade.
