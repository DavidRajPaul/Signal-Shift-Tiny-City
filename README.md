# Signal Shift: Tiny City

> A premium-feeling, offline-first traffic-logic puzzle game for Android.
>
> Working title only. Check trademark, store-name, and package-ID availability before release.

![Status: Planning](https://img.shields.io/badge/status-planning-blue)
![Engine: Godot 4](https://img.shields.io/badge/engine-Godot%204-478CBF)
![Platform: Android](https://img.shields.io/badge/platform-Android-3DDC84)

## Project status

- **Current phase:** Phase 0 — Product definition and validation
- **Release status:** Not implemented; not submitted to Google Play.
- **Source of truth:** this README and the documents listed under [Documentation plan](#documentation-plan).

This project is intended to become a **complete, store-deployable game**, not a three-dimensional-block prototype. Placeholder geometry is acceptable only during short internal experiments. It must not be reported as a completed production feature. The final game needs coherent production art, complete UX, designed audio, validated level content, reliable progression and saves, release QA, and store-ready assets.

## Vision

The player controls traffic signals at miniature-city intersections. They observe approaching vehicles, change signals, resolve traffic conflicts, and deliver every vehicle safely. Levels are short, legible puzzles. Mastery is rewarded with up to three stars and a **Perfect Flow** score for efficient, well-timed control.

### Product principles

1. **Readable in seconds:** a new player understands the first objective without a wall of text.
2. **Fun before scale:** validate the mechanic before expanding content; never confuse a validation build with the finished product.
3. **Premium craft:** intentional typography, lighting, materials, camera framing, animation, sound, haptics, transitions, and error states.
4. **Fair difficulty:** failures are understandable and attributable to player choices.
5. **Offline-first:** core gameplay, levels, settings, and progression work without an account or network.
6. **Maintainable:** deterministic simulation, data-driven levels, modular systems, automated validation.
7. **Ethical monetization:** optional, clearly disclosed, and never disruptive to the core puzzle loop.
8. **AI with guardrails:** agents implement small, reviewable tasks and provide evidence. Human approval is required at phase gates.
9. **No fake completion:** never claim a feature, test, asset, build, or Play Console submission is complete without evidence.
10. **Production quality is the target:** no debug UI, unlicensed assets, broken levels, missing audio, empty screens, or temporary primitives in the release build.

## Proposed MVP

These are planning assumptions to confirm during Phase 0.

- Android mobile game; portrait-first unless UX testing shows landscape is better.
- Single-player, offline-first, deterministic traffic puzzles.
- A guided first session and a polished first world.
- **50 handcrafted and validated levels** as the initial target. Levels must have meaningful variations, not merely different vehicle counts.
- Three-star performance scoring and Perfect Flow.
- Local progress, settings, audio controls, pause/restart, safe resume, and first-run tutorial.
- Cohesive miniature-city 3D art, optimized assets, and consistent lighting.
- Designed sound effects, restrained music, optional haptics, and signal indicators that do not rely on color alone.
- Optional rewarded ads and one-time remove-ads purchase only after gameplay validation and policy review. Monetization can be excluded from v1 if it threatens quality or schedule.
- Store icon, screenshots, short gameplay trailer, privacy disclosures, signed Android App Bundle, QA evidence, and Play Console release checklist.

### Non-goals for v1

Multiplayer, accounts, cloud saves, user-generated levels, live operations, runtime generative AI, open world, complex vehicle physics, loot boxes, subscriptions, or mandatory backend.

## Core gameplay

### Player promise

“Read the intersection, switch the signals, and keep the city moving.”

### Standard level loop

1. **Read:** show a stable intersection view with clear routes and signal states.
2. **Plan:** allow observation without countdown pressure in early levels.
3. **Act:** tapping a signal requests a state change; acknowledge input immediately.
4. **Simulate:** vehicles follow deterministic routes and obey right-of-way/conflict rules.
5. **Resolve:** safe delivery advances the objective; conflict produces clear, recoverable failure feedback.
6. **Score:** calculate stars from documented criteria such as safety, efficiency, and flow. Never use opaque or random scoring.
7. **Reward:** show a concise result, unlock progress, and make Next Level the primary action.

### Interaction rules

- Signal controls must be comfortably tappable and must not obscure roads or routes.
- Every controlled lane has an unambiguous state, reinforced by shape/icon/animation as well as color.
- Routes and conflict zones are legible before movement begins.
- Simulation is deterministic for the same level and input sequence.
- Pause freezes gameplay safely; background/resume cannot duplicate movement or lose progress.
- Restart resets the complete level to its authored initial state.
- If undo exists, its limits are consistent and it cannot corrupt scoring or simulation.
- Teach one rule at a time; introduce at most one new mechanic in a teaching level.
- Avoid unavoidable failure, hidden timing requirements, and pay-to-win progression.

## Level design and progression

| World / levels | Learning goal | Design requirements |
|---|---|---|
| World 1: Little Crossroads (1–10) | Tap a signal, understand safe movement, learn completion | One intersection, few vehicles, no timer pressure, generous feedback |
| World 2: Two-Way Streets (11–20) | Alternate traffic directions and anticipate conflicts | Opposing flows, simple crossing paths, clear previews |
| World 3: Busy Blocks (21–30) | Coordinate signals and manage queues | More lanes/vehicles, staged introduction, no visual clutter |
| World 4: City Connections (31–40) | Solve linked intersections and avoid downstream blocking | Small connected network, readable destinations |
| World 5: Perfect Flow (41–50) | Master timing, efficiency, and score challenges | Multiple valid solutions where practical; replayable star targets |

This is a progression outline, not a substitute for authored level definitions.

### Required specification for every level

Each level must define:

- Unique ID, title, world, order, difficulty, and learning outcome.
- Board dimensions and road/intersection geometry.
- Lane definitions, vehicle spawn points, destinations, routes, and vehicle classes.
- Signal groups, initial states, legal transitions, and conflict matrix.
- Vehicle speeds/movement durations, spacing, queue behavior, and destination behavior.
- Win/loss conditions, restart behavior, undo rules if applicable.
- Star thresholds and Perfect Flow calculation.
- Tutorial copy/contextual hints, if any.
- Camera framing, visual callouts, audio cues, and special set dressing.
- Automated validation result and manual playtest record.
- Accessibility/readability check and known edge cases.

### Difficulty curve

- **Levels 1–3:** teach signal tap, vehicle movement, and safe completion separately.
- **Levels 4–7:** repeat learned rules with small variations.
- **Levels 8–10:** combine learned rules and finish the world with a confidence-building level.
- Later worlds add complexity in controlled steps, followed by consolidation levels.
- Evaluate difficulty with first-time players, not only developers or AI agents.
- Three stars should reward mastery without making one-star completion feel like failure.

## UX and visual direction

### Art direction

A tactile, premium miniature-city diorama: stylized buildings, compact streets, small expressive vehicles, carefully controlled materials, soft shadows, warm daylight, selective saturated accents, and restrained visual effects. The city should feel charming and intentional—not cluttered, generic, or like an unedited asset pack.

### UX principles

- The intersection is the hero during play.
- One primary action per screen; secondary actions have lower visual weight.
- Consistent spacing, type scale, corner radius, elevation, icon family, and motion language.
- Bright accent colors reserved for actionable or important states.
- Never communicate red/green alone; combine color with shape, label, pattern, or animation.
- Respect safe areas, notches, navigation bars, and varied aspect ratios.
- Motion clarifies state, acknowledges input, and rewards success; it must not delay the player.
- Provide reduced-motion consideration and independent music/SFX controls.
- No ad, purchase prompt, or rating request during the first tutorial or active puzzle.

### Required screens and states

1. Splash/loading.
2. Main menu/city hub.
3. World selection or level map.
4. Level intro/objective.
5. Gameplay: ready, running, paused, conflict, success, failure, restart confirmation.
6. Level-complete results with stars and next-level action.
7. Settings: music, SFX, haptics, accessibility, privacy, credits.
8. Optional rewarded-ad offer and unavailable/error state.
9. Remove-ads purchase screen and pending/success/failure/restore states, if included.
10. First-run tutorial, contextual hint, and help.
11. No-network state that does not block core play.
12. Save-recovery/corrupted-save fallback.
13. Privacy policy, credits, licenses, and support entry point.

### Stitch UX deliverables

Use Google Stitch to create high-fidelity screens and interaction flows before implementation. Deliverables:

- Master prompt describing game, audience, device, visual direction, and constraints.
- High-fidelity designs for all required screens and important states—not just the home screen.
- Representative Android gameplay screen.
- Reusable design system documented in `docs/ux/DESIGN.md`.
- Tokens for color, typography, spacing, radius, elevation, and motion.
- Component inventory/variants for buttons, signal controls, cards, dialogs, toasts, progress, and stars.
- Interaction notes, navigation map, loading/error/empty states, accessibility, and responsive behavior.
- Exported reference images and implementation notes under `docs/ux/` where available.
- Human review before UI implementation.

Stitch is a design tool, not proof that the final in-engine UI matches the designs. QA must compare real Android screenshots against approved references.

## Sound and music bible

Audio is part of gameplay feedback, not late decoration.

| Event | Sound direction | Requirement |
|---|---|---|
| UI press | Soft, tactile click | Fast, consistent, not harsh |
| Signal switch | Distinct mechanical/electronic tick | Clearly distinguishable from UI click |
| Vehicle starts | Gentle motor/rolling cue | Avoid repetitive, loud engine loops |
| Safe passage | Short positive confirmation | Must not mask important cues |
| Conflict/collision | Brief, restrained negative cue | Clear without excessive volume |
| Objective progress | Light chime | Supports comprehension |
| Star earned | Three-stage escalating sparkle/chime | Timed to star animation |
| Level complete | Short celebratory musical sting | Memorable and skippable |
| Unlock | Warm, bright reward cue | Avoid casino-like excess |
| Invalid action | Quiet, distinct cue | Also explain visually |
| City ambience | Subtle traffic/birds/wind | Optional and below gameplay cues |
| Music | Playful, modern, low-distraction | Seamless loop; vocals unnecessary |

### Audio implementation rules

- Separate master, music, SFX, and ambient buses with independent settings.
- Respect mute/silent-mode expectations and persist preferences.
- Prevent repeated sounds from stacking uncontrollably; define polyphony and cooldowns.
- Normalize perceived loudness; test on phone speakers, headphones, and low volume.
- Use original, commissioned, or clearly licensed audio; record source/license in the asset register.
- Optimize audio files for mobile and avoid gameplay hitches during loading.
- Haptics are optional and never required to understand a puzzle.
- AI-generated audio may ship only after commercial-use rights are checked and output reviewed.

## Technical architecture

### Proposed stack

- **Engine:** Godot 4.x stable; pin exact version and export templates in project documentation/CI.
- **Language:** typed GDScript with clear module boundaries.
- **Target:** Android first; portrait-first pending UX validation.
- **Art:** Blender-authored stylized 3D assets, optimized materials/textures.
- **Content:** version-controlled data-driven level resources. Choose one canonical format during architecture work.
- **Persistence:** versioned local save data with safe writes and migration support.
- **Testing:** maintained GDScript test framework or project-native test harness, level-schema validator, Android device smoke tests.
- **Version control:** Git, small commits, feature branches/PRs where practical.
- **Build:** reproducible validation where supported and signed Android App Bundle for release.
- **Monetization:** optional adapter interfaces; select SDK/plugin only after policy, maintenance, and compatibility review.
- **Analytics:** minimal and privacy-conscious; omit until data collection and disclosures are understood.

### Proposed project structure

```text
project/
  project.godot
  scenes/
    boot/
    menus/
    gameplay/
    results/
    settings/
    shared/
  scripts/
    app/                 # lifecycle and navigation
    gameplay/            # level orchestration and state
    traffic/             # deterministic simulation/conflicts
    levels/              # schema, loading, validation
    scoring/             # stars and Perfect Flow
    progression/         # unlocks/world progress
    save/                # versioned persistence
    audio/               # buses/settings/event routing
    accessibility/
    platform/             # platform-specific adapters
    monetization/        # optional interfaces
  data/
    levels/
    progression/
    tuning/
  assets/
    models/
    materials/
    textures/
    audio/
    fonts/
    ui/
  tests/
    unit/
    integration/
    levels/
  docs/
```

Validate this layout against the pinned Godot version before creating the project skeleton.

### Gameplay state machine

`BOOT → MENU → WORLD_SELECT → LEVEL_INTRO → READY → RUNNING`

From `RUNNING`, permitted transitions include `PAUSED`, `SUCCESS`, and `FAILURE`. `PAUSED` can return to `RUNNING` or `MENU` through a defined confirmation flow. `SUCCESS` transitions to `RESULTS`; `FAILURE` permits retry or exit. Transitions must be explicit and tested.

### Deterministic traffic simulation

- Model vehicles with route, current segment, progress, speed profile, and state.
- Represent lanes and conflict zones explicitly; do not use sprite overlap alone to determine collisions.
- Use a fixed simulation tick or another documented deterministic update strategy.
- Validate right-of-way/conflict rules before entering a shared conflict zone.
- Separate simulation state from rendered transforms; animation cannot alter game logic.
- Define queue spacing, deadlock prevention, blocked exits, and destination behavior.
- Use stable IDs and deterministic ordering when multiple events happen on the same tick.
- Test signal transitions, simultaneous arrivals, queue blocking, restart, pause/resume, and all win/loss paths.
- Debug visualization must be development-only and absent from release builds.

### Save and progression

- Save schema includes version, unlocked levels, best stars/scores, settings, and relevant purchase entitlement state.
- Use safe write/replace behavior and validate data on load.
- Provide migration logic when schema changes.
- Handle missing/truncated/invalid saves without crashing.
- Never store secrets or payment credentials in local save data.
- Verify purchases through the supported billing flow; client-only flags are not proof of purchase.

### Performance and device quality

- Select a minimum supported device class and set performance targets.
- Profile on real hardware; editor FPS is not release evidence.
- Avoid unnecessary real-time lights, expensive transparency, oversized textures, excessive draw calls, and unbounded particles.
- Reuse meshes/materials; use texture compression and LOD/simpler distant assets where useful.
- Test memory, startup, frame pacing, battery/thermal behavior, app background/resume, and low storage.
- Test touch targets/text across small and large screens.
- Define explicit performance budgets in Phase 2 and verify them during QA.

## Market research and validation

Market figures and competitor listings are snapshots and must be refreshed before launch. Existing games prove category demand, not the viability of this specific game.

### Competitor set

Study traffic/parking logic games, one-touch arcade/timing puzzles, casual puzzles with short levels and star mastery, and miniature/isometric simulation games.

Record each competitor's store URL, date checked, category, visible install/rating signals, core loop, first-session flow, art direction, update activity, monetization observations, review themes, and differentiators. Do not copy proprietary art, names, assets, or level layouts.

### Hypotheses to test

1. Players understand signal control without a long tutorial.
2. Near-miss and Perfect Flow moments feel satisfying, not stressful.
3. Miniature-city presentation increases interest versus a flat board.
4. Players replay levels to improve stars.
5. A modest set of mechanics can produce enough level variety.
6. Optional monetization does not damage early retention or trust.
7. Store screenshots and a short real-gameplay clip communicate the mechanic quickly.

### Validation method

- Conduct uncoached usability tests with people who did not design the game.
- Ask them to explain the goal and complete early levels; observe without prompting.
- Record confusion points, mis-taps, failures, time-to-first-success, and qualitative enjoyment.
- Test store-icon/screenshot concepts with organic audiences where feasible.
- Do not buy installs until the core gameplay and first-session UX are credible.
- Document sample sizes and decision thresholds; do not infer statistical certainty from a handful of testers.
- Define go/no-go criteria in Phase 0 and revisit after each test.

## Monetization and policy

Monetization is conditional on validation and must not compromise the game.

- Free core game; no forced ad during active gameplay or the first-run tutorial.
- Rewarded ads must be player-initiated; grant the advertised reward only after confirmed completion.
- Remove-ads purchase must accurately describe what it removes and handle pending, failed, restored, and refunded states.
- No randomized paid loot boxes in v1.
- Provide an accurate privacy policy and Data safety declarations for every included SDK.
- Audit third-party SDK collection, permissions, advertising IDs, consent, and target-audience implications.
- If children are in the target audience, review Google Play Families policies and compliant ad SDK/format requirements before choosing monetization.
- Never claim compliance until exact SDKs, disclosures, and release settings have been audited.

## Release definition of done

- [ ] All MVP screens and states are implemented against approved production UX.
- [ ] Art is consistent; no debug primitives or placeholder-only scenes remain.
- [ ] All launch levels are authored, tested, balanced, and valid.
- [ ] Tutorial, pause, restart, resume, results, progression, settings, and save recovery work.
- [ ] SFX/music mixes, mute controls, and haptics preferences work.
- [ ] Automated checks pass; no known release-blocking crash/data-loss bug remains.
- [ ] Real-device QA passes on the declared device/OS matrix.
- [ ] Performance/package budgets are met or approved exceptions are documented.
- [ ] Accessibility, contrast, touch targets, and color-independent signal cues are reviewed.
- [ ] Release build contains no debug menus, development endpoints, test purchases, or secrets.
- [ ] Third-party asset/font/music/plugin/SDK licenses are recorded.
- [ ] Privacy policy, Data safety, content rating, target audience, ads declaration, and permissions are accurate.
- [ ] Store title, descriptions, icon, screenshots, feature graphic, and gameplay video are reviewed.
- [ ] AAB is signed using a secure, backed-up process; signing secrets are not committed.
- [ ] Internal/closed testing and account-specific Play Console obligations are complete.
- [ ] Release notes, monitoring plan, support contact, and rollback/hotfix plan are ready.
- [ ] Production rollout is deliberate and post-release smoke checks are recorded.

## Phase roadmap and granular work backlog

**Agent rules:** one task at a time unless parallel work is explicitly approved. Before implementation, report assumptions, files, risks, and tests. After implementation, report changed files, exact test outcomes, build/screenshots where relevant, limitations, and the next proposed task. Stop for David's approval at every phase gate. Never silently proceed to the next phase.

### Phase 0 — Product definition and validation

- [x] **P0-01** Confirm working title, audience, age-rating intent, target markets, and supported device class. *(Decisions recorded in `docs/design/GAME_DESIGN_DOCUMENT.md`, approved 21 Oct 2026.)*
- [ ] **P0-02** Audit traffic-puzzle competitors and record dated store evidence.
- [x] **P0-03** Build a competitor matrix: loop, UX, content, reviews, monetization, differentiation. *(See `docs/research/MARKET_RESEARCH.md`, 25 Oct 2026. Review themes not yet sampled.)*
- [x] **P0-04** Write the formal GDD and lock MVP/non-goals. *(GDD v1.0, 25 Oct 2026.)*
- [x] **P0-05** Specify right-of-way, conflicts, queues, failure, and restart precisely. *(See `docs/design/GAME_DESIGN_DOCUMENT.md`, 25 Oct 2026.)*
- [x] **P0-06** Define three-star and Perfect Flow scoring with examples. *(See `docs/design/GAME_DESIGN_DOCUMENT.md`, 25 Oct 2026.)*
- [x] **P0-07** Define level schema and validation rules. *(See `docs/production/LEVEL_AUTHORING_GUIDE.md`, 25 Oct 2026; file format chosen in P2-06.)*
- [x] **P0-08** Define research hypotheses, usability script, metrics, and go/no-go criteria. *(See `docs/research/USABILITY_TEST_PLAN.md`, 25 Oct 2026.)*
- [x] **P0-09** Check title/trademark/store-name availability before final naming. *(Web and store-name check 25 Oct 2026, no conflict found. Formal registry search required before P9-02.)*
- [ ] **P0-10** Approve scope, risk register, and phase gates.

**Gate:** GDD, research plan, MVP boundary, and acceptance criteria approved.

### Phase 1 — UX, art direction, sound preproduction

- [ ] **P1-01** Write Stitch master prompt and visual-reference brief.
- [ ] **P1-02** Generate/iterate main-menu concepts in Stitch.
- [ ] **P1-03** Design gameplay and all signal/vehicle states.
- [ ] **P1-04** Design world/level selection, results, settings, pause, tutorial, errors, and purchase states.
- [ ] **P1-05** Create navigation map and interaction/state specifications.
- [ ] **P1-06** Document approved tokens/components in `docs/ux/DESIGN.md`.
- [ ] **P1-07** Define responsive layout, safe areas, touch targets, contrast, and non-color cues.
- [ ] **P1-08** Create miniature-city art bible and asset list.
- [ ] **P1-09** Define scale, camera, lighting, materials, palette, and post-processing.
- [ ] **P1-10** Create sound cue sheet, music brief, mix requirements, and license-register template.
- [ ] **P1-11** Review design feasibility and mobile performance.
- [ ] **P1-12** Obtain human approval of UX/art/audio direction.

**Gate:** approved references, DESIGN.md, art bible, and audio plan.

### Phase 2 — Engineering foundation

- [ ] **P2-01** Pin Godot stable version, export templates, plugin policy, and project settings.
- [ ] **P2-02** Establish folders, naming rules, formatting, and contribution guidance.
- [ ] **P2-03** Configure Git ignore and asset/license register.
- [ ] **P2-04** Create boot flow, lifecycle, and navigation/state foundation.
- [ ] **P2-05** Define typed models for lanes, signals, vehicles, routes, and levels.
- [ ] **P2-06** Choose/document canonical level data format.
- [ ] **P2-07** Implement schema validation and useful authoring errors.
- [ ] **P2-08** Establish unit/integration tests and CI checks.
- [ ] **P2-09** Establish logging and development-only debug visualization.
- [ ] **P2-10** Create Android export smoke build and install on a real device.
- [ ] **P2-11** Define performance, memory, startup, and package-size budgets.
- [ ] **P2-12** Document build/test/export/troubleshooting commands.

**Gate:** reproducible project, runnable tests, and basic Android build installed.

### Phase 3 — Production gameplay systems

- [ ] **P3-01** Implement explicit state machine and guarded transitions.
- [ ] **P3-02** Implement lane/road graph and route traversal.
- [ ] **P3-03** Implement signal states and legal transitions.
- [ ] **P3-04** Implement conflict zones and safety checks.
- [ ] **P3-05** Implement deterministic vehicle simulation and movement interpolation.
- [ ] **P3-06** Implement queue spacing, blocked exits, and deadlock prevention.
- [ ] **P3-07** Implement input, immediate feedback, and invalid-action behavior.
- [ ] **P3-08** Implement win/loss evaluation and clear feedback.
- [ ] **P3-09** Implement restart, pause, background/resume, and duplicate-input protection.
- [ ] **P3-10** Implement scoring, star thresholds, and Perfect Flow.
- [ ] **P3-11** Implement level loading and runtime content validation.
- [ ] **P3-12** Test edge cases and deterministic replays.
- [ ] **P3-13** Playtest core mechanic uncoached and record findings.
- [ ] **P3-14** Tune interaction/simulation from evidence.
- [ ] **P3-15** Obtain gameplay acceptance approval.

**Gate:** tested core mechanic—not just moving blocks.

### Phase 4 — Production art and polish

- [ ] **P4-01** Create final roads, curbs, markings, sidewalks, and terrain.
- [ ] **P4-02** Create final vehicle models/materials and a coherent vehicle family.
- [ ] **P4-03** Create modular buildings, props, vegetation, and city dressing.
- [ ] **P4-04** Establish camera, lighting, shadows, and rendering settings.
- [ ] **P4-05** Implement smooth turns, acceleration/deceleration, stopping, and spacing.
- [ ] **P4-06** Implement signal animations and clear active/disabled states.
- [ ] **P4-07** Implement polished menus/components from Stitch references.
- [ ] **P4-08** Implement transitions, star animation, feedback, and restrained VFX.
- [ ] **P4-09** Implement audio buses, SFX routing, music, ambience, and persisted settings.
- [ ] **P4-10** Implement optional haptics and safe fallbacks.
- [ ] **P4-11** Compare in-engine screenshots against Stitch references.
- [ ] **P4-12** Profile rendering and optimize assets on target hardware.
- [ ] **P4-13** Remove prototype-only visuals from production scenes.
- [ ] **P4-14** Complete art/audio/UX review and obtain approval.

**Gate:** coherent, polished visuals/audio; no placeholder-only shipped assets.

### Phase 5 — Content and progression

- [ ] **P5-01** Build level-authoring workflow and reusable templates.
- [ ] **P5-02** Author levels 1–3 and validate tutorial learning.
- [ ] **P5-03** Author levels 4–10 and tune first-world difficulty.
- [ ] **P5-04** Author levels 11–20 with opposing flows.
- [ ] **P5-05** Author levels 21–30 with multi-signal/queue coordination.
- [ ] **P5-06** Author levels 31–40 with connected intersections.
- [ ] **P5-07** Author levels 41–50 with mastery challenges.
- [ ] **P5-08** Add distinct titles/objectives and meaningful visual variations.
- [ ] **P5-09** Run schema, reachability, and win-condition validation on all levels.
- [ ] **P5-10** Manually playtest every level and record results/fixes.
- [ ] **P5-11** Add unlocks, best stars/scores, and replay support.
- [ ] **P5-12** Verify every level is completable and scoring reproducible.
- [ ] **P5-13** Balance progression and remove unfair/repetitive levels.
- [ ] **P5-14** Obtain content-completeness approval.

**Gate:** launch levels complete, validated, and playtested.

### Phase 6 — Save, settings, accessibility, resilience

- [ ] **P6-01** Implement versioned save schema and safe writes.
- [ ] **P6-02** Test validation, recovery, and migration.
- [ ] **P6-03** Persist progress, best scores, settings, and unlocks.
- [ ] **P6-04** Implement music/SFX/haptics controls.
- [ ] **P6-05** Review text scaling, contrast, signal semantics, and touch targets.
- [ ] **P6-06** Test pause/resume, process death, app switching, and rotation policy.
- [ ] **P6-07** Test low storage, corrupt saves, missing assets, and interruptions.
- [ ] **P6-08** Verify offline play on first launch and repeat sessions.
- [ ] **P6-09** Conduct accessibility/usability review and fix blockers.

**Gate:** no known save/progression blockers; offline/recovery verified.

### Phase 7 — Monetization and privacy (conditional)

- [ ] **P7-01** Decide if monetization is justified by validation results.
- [ ] **P7-02** Research maintained Godot-compatible SDK/plugin options.
- [ ] **P7-03** Document SDK versions, data collection, permissions, and policy impact.
- [ ] **P7-04** Implement monetization behind a replaceable interface.
- [ ] **P7-05** Implement player-initiated rewarded ads and verified rewards.
- [ ] **P7-06** Implement purchase pending/success/failure/restore states if applicable.
- [ ] **P7-07** Test sandbox purchases and ads, not production transactions.
- [ ] **P7-08** Verify no forced ads during active gameplay/tutorial.
- [ ] **P7-09** Draft privacy policy and audit data/consent.
- [ ] **P7-10** Review target audience and Families policy if children are included.
- [ ] **P7-11** Ensure disclosures match shipped SDKs and behavior.
- [ ] **P7-12** Obtain monetization/privacy approval.

**Gate:** monetization tested/compliant or deliberately excluded.

### Phase 8 — QA, optimization, release candidate

- [ ] **P8-01** Define Android versions, device matrix, and release configuration.
- [ ] **P8-02** Run unit, integration, schema, and all-level validation.
- [ ] **P8-03** Test install/launch/play/complete/restart/resume on real devices.
- [ ] **P8-04** Test small/large screens, low memory, and performance.
- [ ] **P8-05** Test touch, audio, haptics, settings, saves, and offline scenarios.
- [ ] **P8-06** Test monetization edge cases if included.
- [ ] **P8-07** Run regression after release-blocking fixes.
- [ ] **P8-08** Profile startup, frame pacing, memory, thermals, and package size.
- [ ] **P8-09** Resolve release-blocking crashes/errors.
- [ ] **P8-10** Audit licenses, attribution, secrets, permissions, debug flags, and SDKs.
- [ ] **P8-11** Generate release candidate AAB and verify signature/metadata.
- [ ] **P8-12** Complete checklist and obtain human sign-off.

**Gate:** release candidate passes required tests with no unresolved critical/high-severity issue.

### Phase 9 — Store assets and Play Console

- [ ] **P9-01** Verify developer account status, testing obligations, and production access.
- [ ] **P9-02** Finalize title, application ID, developer contact, and support channel.
- [ ] **P9-03** Create icon and feature graphic to current specs.
- [ ] **P9-04** Capture accurate production-build screenshots.
- [ ] **P9-05** Record short gameplay trailer from actual gameplay.
- [ ] **P9-06** Write/review store descriptions and localization if needed.
- [ ] **P9-07** Complete content rating and target-audience declarations.
- [ ] **P9-08** Complete Data safety, ads declaration, privacy URL, and permissions review.
- [ ] **P9-09** Configure signing securely; back up credentials; never commit secrets.
- [ ] **P9-10** Create internal/closed testing release and recruit testers as required.
- [ ] **P9-11** Collect feedback, fix issues, and complete account-specific testing.
- [ ] **P9-12** Verify listing and release configuration before submission.

**Gate:** listing and policy declarations complete; account eligibility verified.

### Phase 10 — Production rollout and post-launch

- [ ] **P10-01** Upload signed AAB to the appropriate Play Console track.
- [ ] **P10-02** Resolve Play Console validation/policy issues.
- [ ] **P10-03** Apply for production access/submit for review when eligible.
- [ ] **P10-04** Resolve rejection feedback if any.
- [ ] **P10-05** Roll out deliberately; use staged rollout where available and appropriate.
- [ ] **P10-06** Verify public listing, install, launch, gameplay, saves, and monetization.
- [ ] **P10-07** Monitor crashes, ANRs, reviews, and defects.
- [ ] **P10-08** Maintain hotfix and rollback plan.
- [ ] **P10-09** Review early retention, level drop-off, ad engagement, and store conversion where lawful data is available.
- [ ] **P10-10** Document lessons and prioritize updates after launch stability.

**Gate:** public release verified on Google Play and post-launch monitoring active.

## AI-agent operating contract

1. Read this README and relevant docs before changing files.
2. Work only on the assigned task ID.
3. Do not silently expand scope or start the next phase.
4. Before work, state assumptions, planned changes, risks, and verification.
5. Respect approved Stitch designs, DESIGN.md tokens, architecture, and licenses.
6. Prefer small, typed, testable components over monolithic scripts.
7. Add/update tests with behavior changes; never disable tests just to pass CI.
8. Do not invent command output, device tests, screenshots, store status, or deployment success.
9. Never commit API keys, signing keys, service-account credentials, personal data, or private store information.
10. Do not use unlicensed assets, music, fonts, or copied level layouts.
11. If requirements conflict, SDKs are unavailable, designs are infeasible, or credentials are needed, stop and ask David.
12. Report changed files, exact test outcomes, remaining risks, and next proposed task.
13. Update checklist items only when acceptance criteria have evidence.
14. Ask for explicit approval at every phase gate.
15. Do not claim production readiness until the release definition of done is satisfied.

### Required task report

```text
Task ID:
Summary:
Files changed:
Design references followed:
Tests/commands run:
Results (pass/fail/not run):
Device/build evidence:
Known issues and risks:
Licenses or SDKs introduced:
Acceptance criteria satisfied:
Recommended next task (not started):
Approval required:
```

## Decision log

| ID | Decision | Status |
|---|---|---|
| D-001 | Working title: Signal Shift: Tiny City | Approved as working title; trademark and package-ID check pending (P0-09) |
| D-002 | Godot 4 + GDScript | Proposed; pin exact stable version in Phase 2 |
| D-003 | Android-first, offline-first, single-player | Proposed |
| D-004 | Target 50 handcrafted levels | Proposed; validate in Phase 0 |
| D-005 | Google Stitch for UX and design-system documentation | Planned; human review required |
| D-006 | Rewarded ads / remove-ads purchase | Excluded from v1 (approved 21 Oct 2026); revisit after validation |
| D-007 | No runtime AI or mandatory backend in v1 | Proposed |
| D-009 | Audience: general casual players; not child-directed | Approved 21 Oct 2026 |
| D-010 | Markets: English first; India as test market | Approved 21 Oct 2026 |
| D-011 | Device: mid-range Android (about 4 GB RAM) | Approved 21 Oct 2026; confirm in P2-11 |
| D-012 | Portrait-first orientation | Approved 21 Oct 2026; validate in UX testing |
| D-013 | Binary signals only in v1 | Approved 21 Oct 2026 |
| D-014 | No undo in v1 | Approved 21 Oct 2026 |
| D-015 | Score formula: wait ticks + extra switches, authored thresholds, optional Perfect Flow | Decided 25 Oct 2026 (delegated); review at gate |
| D-016 | 50 levels target; 30 (Worlds 1–3) minimum; decide after P5-03 | Decided 25 Oct 2026 (delegated); review at gate |
| D-017 | Differentiator: thinking puzzle, not reflex game | Decided 25 Oct 2026 (delegated); validate in usability tests |
| D-008 | Public GitHub repository | Created by project owner; verify visibility in GitHub |

## Documentation plan

These files are planned; do not assume they exist until committed:

- `docs/research/MARKET_RESEARCH.md` — dated competitor/market research, sources, confidence notes.
- `docs/research/USABILITY_TEST_PLAN.md` — hypotheses, test rounds, session script, metrics, go/no-go criteria.
- `docs/design/GAME_DESIGN_DOCUMENT.md` — detailed mechanics, progression, scoring, and level specifications.
- `docs/ux/STITCH_WORKFLOW.md` — prompts, screen inventory, review and export process.
- `docs/ux/DESIGN.md` — approved tokens, typography, components, motion, visual rules.
- `docs/technical/TECHNICAL_ARCHITECTURE.md` — simulation, schemas, persistence, performance, testing.
- `docs/audio/AUDIO_BIBLE.md` — sound design, cue sheet, mix rules, licensing.
- `docs/art/ART_BIBLE.md` — art direction, asset pipeline, optimization, provenance.
- `docs/production/LEVEL_AUTHORING_GUIDE.md` — authoring, validation, difficulty rubric.
- `docs/production/AI_AGENT_PLAYBOOK.md` — prompts, token discipline, task protocol, approval gates.
- `docs/qa/QA_AND_RELEASE_PLAN.md` — device matrix, QA, privacy, Play Console, signing, rollout.

## References

Prefer official/primary sources for implementation and release requirements. Re-check version-sensitive requirements before release.

- [Godot documentation](https://docs.godotengine.org/)
- [Godot Android export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_android.html)
- [Google Play Console Help](https://support.google.com/googleplay/android-developer/)
- [Google Play Families Policy](https://support.google.com/googleplay/android-developer/answer/9893335)
- [Google Stitch](https://stitch.withgoogle.com/)
- [Android App Bundle](https://developer.android.com/guide/app-bundle)
- [Google Play testing requirements](https://support.google.com/googleplay/android-developer/answer/14151465)

---

**Next action:** complete **P0-01** and **P0-02**. Do not start building game scenes until Phase 0 scope and Phase 1 UX/art direction are approved.
