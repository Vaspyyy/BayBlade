# Art & Presentation

## 1. Direction

Target: **stylized realism with hyper-detailed mechanical presentation**.

The project should not require photorealistic humans, city environments, or cinematic AAA production.

Visual fidelity should be concentrated where it matters most:
- tops,
- components,
- materials,
- workshop machines,
- damage,
- machining,
- testing,
- arenas,
- high-speed replays.

This creates a practical blend of "B + C":

- stylized, manageable environments and characters,
- highly convincing engineering objects and physical effects.

## 2. Visual hierarchy

Priority order:

1. competition tops,
2. damage and material response,
3. workshop machinery,
4. arena and contact surface,
5. measurement/testing equipment,
6. tools and raw stock,
7. environment,
8. characters.

If art capacity is limited, protect this order.

## 3. Mechanical detail

Mechanical assets should support close inspection.

Desired detail:
- machining marks,
- tool paths,
- brushed finishes,
- polished contact edges,
- anodizing,
- oxide layers,
- heat tint,
- coating wear,
- scratches,
- gouges,
- dents,
- chipped edges,
- grease,
- dust,
- metal chips,
- polymer whitening near stressed zones,
- cracked coatings,
- worn tip profiles.

These details communicate mechanical state, not just decoration.

## 4. Damage presentation

Damage should be readable at multiple scales.

### Match scale
- sparks,
- fragments,
- wobble,
- bent silhouette,
- loose component motion,
- contact flashes,
- smoke/dust only where physically justified.

### Inspection scale
- dents,
- edge rounding,
- crack lines,
- discoloration,
- pitting,
- galling,
- coating loss.

### Analysis scale
- stress overlay,
- thermal overlay,
- crack markers,
- wear map,
- contact history.

## 5. Stylization boundaries

Stylization can affect:
- proportions of rooms,
- character rendering,
- UI,
- color grading,
- environmental clutter,
- shape language.

Stylization should **not** make mechanical geometry misleading.

A 3 mm wall should look meaningfully thinner than a 10 mm wall.

Material categories should remain visually legible.

Damage should match the simulated event.

## 6. Characters

Characters are not the primary rendering budget.

A stylized-realistic character approach is acceptable.

Important needs:
- readable silhouettes,
- recurring rival identity,
- clothing variation,
- expressions,
- simple animation,
- sponsor/team branding.

The game does not require high-end facial capture.

## 7. Workshop

The workshop should feel increasingly capable over time.

Early:
- cramped,
- improvised,
- mixed household/garage equipment,
- visible mess,
- cheap lighting,
- plastic bins,
- hand tools.

Mid:
- organized benches,
- proper machines,
- metrology corner,
- stock storage,
- safety equipment.

Late:
- precision machines,
- controlled lighting,
- test cells,
- inspection stations,
- automated equipment,
- clean zones,
- high-end computing.

The workshop is part progression screen, part museum of the player's career.

## 8. Asset modularity

Workshop art should be highly modular.

Build around:
- wall modules,
- floor modules,
- benches,
- shelving,
- machine footprints,
- cable/utility runs,
- storage,
- lighting fixtures,
- safety barriers.

This reduces Blender workload and lets the space evolve without requiring entirely new environments.

## 9. Top asset strategy

Player-created tops cannot rely on manually authored meshes.

The game requires procedural or CAD-derived geometry.

Art-authored content should focus on:
- premade starter parts,
- commercial NPC parts,
- materials,
- decals,
- fastener libraries,
- bearing assets,
- launcher assets,
- surface shaders.

Custom geometry comes from the design system.

## 10. Materials

Material rendering is critical.

Distinct classes:
- injection-molded plastic,
- machined polymer,
- rubber/elastomer,
- aluminum,
- steel,
- titanium,
- tungsten alloys,
- ceramics,
- coated surfaces,
- composites,
- near-future materials.

Shader parameters should be driven partly by physical state:
- roughness changes with wear,
- discoloration with heat,
- coating masks erode,
- scratches accumulate,
- grease/contamination appears,
- polished contact zones develop.

## 11. Manufacturing visuals

Manufacturing should feel satisfying even when automated.

Visual moments:
- chips leaving a cutter,
- coolant,
- tool engagement,
- sparks during grinding,
- polishing,
- part probing,
- balancing correction,
- thermal treatment glow where appropriate,
- inspection scans.

These can be selectively simulated or authored.

The goal is readable process, not a machining CAM visualizer at all times.

## 12. Arena presentation

Official arenas should feel engineered for containment and spectatorship.

Features:
- replaceable bowl inserts,
- containment walls,
- camera ports,
- sensors,
- lighting,
- inspection access,
- debris collection,
- sponsor branding.

Different competitive levels can visibly scale from community hall setups to professional venues.

## 13. Camera language

Normal competition:
- clear broadcast-like camera,
- player-selectable viewpoints,
- close enough to understand contact.

Replay:
- free camera,
- ultra slow motion,
- orbit,
- macro close-up,
- follow fragment,
- contact-point camera,
- technical orthographic views.

The replay camera is part entertainment and part engineering instrument.

## 14. High-speed impact presentation

Use restrained time dilation and replay rather than fake mid-match superpowers.

High-speed replays can emphasize:
- tooth contact,
- elastic flex,
- debris release,
- ring deformation,
- tip slip,
- wall impact,
- crack propagation.

The normal real-time match should remain physically continuous.

## 15. UI style

UI should combine:
- workshop utility,
- motorsport telemetry,
- engineering software,
- approachable game readability.

Avoid making every screen look like enterprise CAD.

Information density should scale with player capability.

Early UI:
- simple,
- qualitative,
- limited measurements.

Late UI:
- dense,
- quantitative,
- customizable graphs and overlays.

## 16. Sound

Mechanical sound is essential.

Need distinct layers for:
- launcher,
- spin,
- tip contact,
- bearing condition,
- wobble,
- metal-on-metal impacts,
- plastic hits,
- ceramic hits,
- wall impacts,
- loose components,
- fracture,
- debris.

Sound can communicate hidden problems before the player owns instruments capable of quantifying them.

A skilled player may hear a bad bearing before they can measure it.

## 17. Performance strategy

Visual fidelity should be scalable.

Important because:
- custom geometry can become complex,
- debris can accumulate,
- replays may use extreme slow motion,
- workshop scenes contain many persistent items.

Use:
- LODs,
- debris relevance thresholds,
- procedural detail maps,
- instancing,
- baked/static environment lighting where appropriate,
- higher visual fidelity during replay than full-speed simulation if needed.

## 18. Blender team practicality

To keep the art pipeline sustainable:

- use modular environment kits,
- prioritize machines and tops over people,
- rely on procedural materials,
- derive custom top geometry from CAD rather than artist modeling,
- build reusable damage/material systems,
- author a smaller number of high-quality machine assets,
- use variants and attachments instead of unique assets for every tier.

The intended look is expensive where the player stares, economical where they do not.
