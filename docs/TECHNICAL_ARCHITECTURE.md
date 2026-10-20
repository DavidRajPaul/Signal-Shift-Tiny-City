# Technical Architecture — Signal Shift: Tiny City
**Status:** Proposal; review before project skeleton. Pin exact Godot 4.x stable version in Phase 2.

## Boundaries
- **Domain:** road graph, lanes, signals, vehicles, routes, conflicts, simulation, win/loss/scoring; avoid scene-node dependencies.
- **Application:** state transitions, level lifecycle, pause/resume/restart, progression/events.
- **Presentation:** Godot scenes for roads, vehicles, signals, camera, HUD, menus, VFX/audio. Reads authoritative state; never decides collision.
- **Content:** one canonical level format.
- **Infrastructure:** saves/settings, platform integration, logs and optional approved monetization/analytics.

## Proposed layout
\`\`\`text
project/
  project.godot
  scenes/{boot,menus,gameplay,results,settings,shared}/
  scripts/{app,gameplay,traffic,levels,scoring,progression,save,audio,accessibility,platform,monetization}/
  data/{levels,progression,tuning}/
  assets/{models,materials,textures,audio,fonts,ui}/
  tests/{unit,integration,levels}/
  docs/
\`\`\`
Keep scripts focused and autoloads few/documented.

## Domain concepts
LevelDefinition, RoadNode, LaneSegment, SignalGroup, VehicleDefinition, VehicleRuntimeState, ConflictZone, LevelRuntimeState, LevelResult, ProgressSave, GameSettings. Stable IDs required for content/tests/logs.

## Deterministic simulation
Use a fixed simulation tick or another tested deterministic method. Render FPS, wall-clock time, unordered iteration and tween completion must not affect safety/scoring.
1. Read queued commands.
2. Validate signal transitions.
3. Update signal logic.
4. Compute movement intent from route, signal, conflict occupancy and downstream capacity.
5. Resolve competing intents in stable order.
6. Advance vehicles/queues.
7. Detect delivery/conflict/deadlock/win/loss.
8. Publish state to presentation.
9. Optionally record test state hashes.
Define multi-zone reservations, headway, priority, blocked exits and deadlock. Same level/input sequence must produce same state sequence.

## State machine
BOOT, MENU, WORLD_SELECT, LEVEL_INTRO, READY, RUNNING, PAUSED, SUCCESS, FAILURE, RESULTS. Guard transitions centrally. Repeated taps cannot duplicate scenes/results. Pause freezes domain advancement; resume must not catch up hidden ticks. Restart reconstructs from immutable level definition and resets all runtime state.

## Level validation
Choose typed Godot Resources vs JSON after comparing editor ergonomics, diffability and agent edit safety; never keep duplicate canonical formats. Validate unique IDs, route connectivity/destinations, legal signal groups/transitions, consistent conflicts, valid paths/assets, achievable ordered stars, reachable intended solution, no accidental deadlock, tutorial keys and license records. Report exact level/error; never silently skip invalid content.

## Saves/scoring
Score immutable result summary, never animation time/frame rate. Formula is Phase 0 decision. Version save schema, validate values, migrate explicitly, write safely, recover corrupt/missing saves. Save at result and setting changes, not every tick. Local purchase flags are not proof of purchase. Never store secrets/payment credentials. Offline play cannot depend on ads/billing.

## UI/audio/art
Implement approved Stitch screens via reusable Godot components and docs/ux/DESIGN.md tokens. Test safe areas, targets, text scaling and aspect ratios. Use Master/Music/SFX/Ambience buses with cooldowns/polyphony. Missing optional audio must not crash. Reuse meshes/materials; limit expensive transparency/lights/particles; profile real Android hardware. Debug overlays excluded from release.

## Monetization
Select no SDK before checking maintenance, Godot compatibility, Android requirements, privacy and Play policy. Rewarded ads require explicit action/verified completion; purchases need pending/success/failure/restore and idempotent entitlement handling. Provider failure returns to play. Child-directed audience requires separate Families review.

## Android build
Pin engine/export templates/toolchain. Keep package ID stable after release. Produce signed AAB; never commit keystore/credentials. Verify orientation, icons, permissions, version, signing and install. Recheck Play target API/testing requirements.
- Godot export: https://docs.godotengine.org/en/4.6/tutorials/export/exporting_for_android.html
- Play target API: https://support.google.com/googleplay/android-developer/answer/11926878
- Play testing: https://support.google.com/googleplay/android-developer/answer/14151465

## Tests and agent ownership
Unit: signal/conflict/route/capacity/determinism/win-loss/scoring/migrations. Integration: load→act→result→save/reload; pause/restart. Content: all levels plus human tests. UI: navigation/settings/controls/safe areas/reference images. Device: install, performance, audio, background/resume, low storage, offline.
Gameplay agent owns simulation/tests; content agent levels/validator; UX agent approved UI; art/audio agents their assets/integration; QA tests/reports; release agent build/store docs. Parallelize only after interfaces/file ownership agreed. Open decisions: exact engine/test framework, level format, tick, signal model, undo, scoring, device budget, analytics, monetization.
