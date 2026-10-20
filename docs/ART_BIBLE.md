# Art Bible — Signal Shift: Tiny City
**Status:** Direction proposal; no production art is claimed complete.

## Visual target
Premium tactile miniature-city diorama: warm daylight, compact architecture, expressive vehicles, clean markings, soft grounded shadows, controlled materials and limited accent palette. Puzzle readability outranks decoration.

## Camera/composition
Stable three-quarter/isometric top-down view. Reveal routes, signals, queues and destinations. Keep controls/routes away from safe-area edges. Avoid cinematic camera movement during decisions. Preserve consistent framing.

## Materials/lighting
Consistent scale/material response; road contrasts with markings/sidewalks. Props must not resemble controls/routes. Warm light and soft shadows cannot hide vehicles. Restrained saturation and high-contrast interactive accents. Avoid excessive reflections, transparency, post-processing and real-time lights.

## Asset families
Roads/curbs/sidewalks/intersections; signal heads and accessible state indicators; cohesive vehicle family; modular buildings/shops/houses/fences/street furniture/vegetation; UI icons/stars/level selection; restrained signal glow and completion VFX. Store assets must represent the actual game.

## Pipeline/performance
Model in Blender/approved tool with consistent units/pivots. Apply transforms; name meshes/materials predictably; validate normals, UVs, scale, orientation and materials on device. Reuse meshes/materials; compress/atlas where useful. Set budgets in Phase 2. Profile actual Android hardware; editor FPS is not release evidence. Debug overlays excluded from release.

## QA/rights
- [ ] Shared scale, camera, lighting and palette.
- [ ] No mismatched asset styles.
- [ ] Vehicles/signals readable at phone size; roads contrast with decoration.
- [ ] No important occlusion or placeholder primitives in release.
- [ ] Performance verified on target device.
Record creator, source, license, attribution, permission/receipt, modifications and intended use for every model/texture/font/icon/animation/VFX. Never copy competitor assets/layouts. Free or AI-generated does not automatically mean commercially usable.
