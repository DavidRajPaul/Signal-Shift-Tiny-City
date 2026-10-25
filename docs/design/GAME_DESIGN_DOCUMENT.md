# Game Design Document — Signal Shift: Tiny City
**Version:** 0.1 proposal · **Date:** 20 October 2026 · **Status:** Phase 0 approval required.

## High concept
The player is a traffic coordinator for a miniature city. They operate signal groups to guide cars through intersections, avoid conflicting movements, prevent downstream queues blocking junctions, and deliver every vehicle safely.  
**Pitch:** “Control the lights. Keep the tiny city moving.”

## Pillars
1. Instant readability. 2. Satisfying feedback. 3. Fair deterministic rules. 4. Diorama charm without visual clutter. 5. Mastery without punishing first completion. 6. Short sessions and safe resume. 7. No placeholder-only shipped screens/assets/audio.

## Session and core loop
Audience is hypothesized to be casual puzzle players; age target/rating remains undecided. Intended level length 30–120 seconds; first meaningful action target under 10 seconds. Offline, account-free play. No forced timer early; no monetization before first success.

Observe → understand routes/signals → tap signal → watch traffic resolve → feedback → deliver safely → earn stars → unlock/replay.

At level start show a stable intersection and concise objective. Signals use color plus shape/icon/animation. Routes/destinations are visible before action. Early instruction pauses/slows simulation. Signal taps request legal transitions and are acknowledged immediately. Same level/input sequence must produce same result. Invalid actions explain why.

Success: brief celebration, stars, persist before navigation, Next Level primary. Failure: explain conflict/deadlock, Retry primary. Restart resets every runtime field. No standard level may contain unavoidable failure.

## Rules
- Road graph has entries, intersections, exits/destinations and directed lane segments.
- Signal groups define controlled movements, initial state, legal transitions and conflicts.
- Vehicles have stable IDs, routes, spawn triggers, destinations, movement profile and queue state.
- Conflict zones are authored, not inferred from visual overlap.
- Check downstream capacity before entering junctions.
- Simulation—not tween/render state—decides safety. Queue spacing, deadlock, simultaneous arrivals and priorities are deterministic.
- Win when all required vehicles arrive. Loss only on defined unsafe conflict or unresolvable deadlock with a visible cause.
- **Open decisions:** binary vs amber signals; undo in v1. Agents must not assume silently.

## Scoring
Transparent/deterministic. Formula decided; see "Score formula" below. Candidate inputs were: safety (mandatory), signal changes/avoidable stops, queue delay and completion. Thresholds authored per level. One-star completion remains satisfying; Perfect Flow is optional mastery, not a main-path gate. Create five worked examples with multiple valid solutions before implementation. Never score on render FPS or hidden timing.

## Campaign: 50-level target
These are concepts, not validated maps. Every final level needs a map, conflict matrix, solution/failure analysis, automated validation and human playtest.

### World 1 — Little Crossroads (1–10)
Sunny neighborhood, few vehicles, one intersection, generous gaps.
1 signal/stream tutorial; 2 non-conflicting streams; 3 crossing conflict; 4 alternate directions; 5 short queue; 6 downstream capacity; 7 two groups/one safe ordering; 8 known rules/new route; 9 optional efficiency; 10 finale combining known rules.

### World 2 — Two-Way Streets (11–20)
Opposing flows and queue release.
11 opposing routes preview; 12 safe alternation; 13 two queues; 14 release without blocking exit; 15 three movements/two conflicts; 16 consolidation; 17 long route/capacity; 18 efficiency with alternate solutions; 19 queue + opposing flow; 20 anticipation finale.

### World 3 — Busy Blocks (21–30)
Multiple signals and staged arrivals.
21 third group in isolation; 22 coordinate three groups; 23 staggered arrivals; 24 sequencing with queue; 25 non-conflicting simultaneous flow; 26 consolidation; 27 prevent blocked exit; 28 multi-signal efficiency; 29 capacity + coordination; 30 deterministic finale.

### World 4 — City Connections (31–40)
Linked intersections and downstream blocking.
31 two linked nodes; 32 avoid feeding full segment; 33 release downstream first; 34 locally safe/global block; 35 coordinate arrivals; 36 consolidation; 37 third node/modest traffic; 38 linked efficiency; 39 capacity + signals; 40 staged-arrival finale.

### World 5 — Perfect Flow (41–50)
Master known rules, no new rule after level 45.
41 sequencing mastery; 42 queue optimization; 43 non-conflicting flow; 44 two-node capacity; 45 teach scoring nuance; 46 replay challenge; 47 two strategies/different scores; 48 longer chain; 49 combine mechanics without hidden constraints; 50 visual showcase with optional Perfect Flow.

## UX screen requirements
- Main menu: miniature-city hero, one Play/Continue, progress, map/settings; no fake currency.
- Level select: clear unlocks/stars; list/grid fallback if 3D map hurts usability.
- Gameplay: objective/pause, large signal controls near movements, no color-only meaning or permanent timer.
- Pause: freeze; Resume/Restart/Exit; confirm destructive actions.
- Success: brief star reveal, Next Level primary; save first.
- Failure: explain cause, Retry primary; no forced ad.
- Settings: independent music/SFX/haptics, Help/accessibility/privacy/credits/licenses; persist.
Tutorial: one contextual instruction at a time; no countdown or first-action failure; replayable from Help.

## Art/audio
Stable isometric/three-quarter top-down camera, warm daylight, controlled shadows, tactile materials, readable vehicles and roads. Smooth stops/turns; restrained skippable VFX. Audio cues: UI, signal, safe passage, conflict, progress, star, completion, unlock, ambience/music. Separate audio buses and persisted controls.

## Monetization/accessibility
Conditional on validation/policy: opt-in rewarded ad and remove-ads only; no forced ads during active play/tutorial or paid randomized rewards. Offline play cannot depend on provider. Never rely on red/green alone; support readable touch targets, safe areas, text scaling, reduced motion where needed and externalized strings.

## Content complete
Level: valid, completable, no unintended deadlock, deterministic score, readable routes, sounds, restart and human test record. Screen: all states/interactions, loading/error behavior, approved-reference match and aspect-ratio testing. Audio: licensed, normalized, routed and tested.

## Decisions to approve
Title/package ID, audience/rating/regions, portrait vs landscape, signal model, undo, score formula, feasibility of 50 levels, monetization, minimum device/performance budget.

## Phase 0 decisions (approved 21 Oct 2026)

- **Working title:** Signal Shift: Tiny City. Trademark and package-ID check still pending (P0-09).
- **Audience:** general casual puzzle players. Not child-directed. Age rating to be confirmed in the content rating questionnaire (P9-07).
- **Markets:** English first; India as test market.
- **Device class:** mid-range Android (about 4 GB RAM). Confirm with profiling in P2-11.
- **Orientation:** portrait-first, pending UX testing.
- **Signal model:** binary signals only in v1.
- **Undo:** not in v1.
- **Monetization:** none in v1. Revisit after validation.

**Decided 25 Oct 2026 (delegated by David; review at the Phase 0 gate):** differentiator, score formula, and 50-level feasibility. See the sections below.

## Differentiator (decided 25 Oct 2026)
The closest competitors (Traffix, Crazy Traffic Control; see `docs/research/MARKET_RESEARCH.md`) are real-time reflex games: lights are tapped under pressure, and accidents accumulate until the run ends. Signal Shift is a **thinking puzzle, not a reflex game**:
1. **Plan before pressure.** Routes, destinations, and conflict zones are visible before action, and early levels have no countdown.
2. **Deterministic and explainable.** The same inputs always give the same result, and every failure names its cause.
3. **Network reasoning.** Downstream capacity and linked intersections (Worlds 3–5) make the puzzle about ordering and flow, not tap speed.
4. **Authored levels with star mastery.** Each level is a designed puzzle with replayable star targets, not an endless survival run.

**Testable claim:** in uncoached tests, players describe the game as a puzzle rather than a reaction game, and replay levels for stars. If testers call it a reflex game, revisit before Phase 3 ends.

## Score formula (decided 25 Oct 2026)
All values are integers computed from the simulation's result summary, never from animation time or frame rate.

**Inputs (per level run):**
- `W` = total wait ticks: the sum, over all vehicles, of ticks spent stopped at a signal or in a queue.
- `S` = signal changes the player made.
- Authored per level: `S_par` (minimum switches in the reference solution), `W3` and `W2` (wait thresholds, `W3 ≤ W2`), and `W_opt` (minimum achievable wait, found by the level validator).
- `E = max(0, S − S_par)`, the extra switches.

**Safety:** any conflict-zone violation or unresolvable deadlock is a failure. No stars, no score.

**Stars (successful run):**
- 1 star: every required vehicle delivered safely.
- 2 stars: `W ≤ W2`.
- 3 stars: `W ≤ W3` and `E ≤ 1` (one spare switch is allowed, so alternative orderings can still earn 3 stars).

**Perfect Flow (optional mastery badge):** `W = W_opt` and `S = S_par`. It is never required for progression.

**Flow score (shown on results details and used for best-score replay):** `max(0, 1000 − 5·W − 20·E)`.

Tutorial levels set generous `W3`/`W2`. Tick rate is a Phase 2 technical decision; thresholds are expressed in ticks so they stay valid if the rate is fixed early.

### Worked examples
| # | Level | `S_par`, `W3`, `W2`, `W_opt` | Player run | Result |
|---|---|---|---|---|
| 1 | L1, one signal, 3 cars | 1, 15, 40, 0 | Switches at once: `W=0`, `S=1` | 3 stars, Perfect Flow, score 1000 |
| 2 | L1 | 1, 15, 40, 0 | Switches a moment late: `W=12`, `S=1` | 3 stars, no Perfect Flow, score 940 |
| 3 | L3, crossing conflict, 2 groups, 4 cars | 2, 40, 80, 30 | Reference order: `W=30`, `S=2` | 3 stars, Perfect Flow, score 850 |
| 4 | L3 | 2, 40, 80, 30 | Other valid order, one extra switch: `W=38`, `S=3` | 3 stars, no Perfect Flow, score 790 |
| 5 | L3 | 2, 40, 80, 30 | Cautious play: `W=120`, `S=6` | 1 star, score 320 |
| 6 | L3 | 2, 40, 80, 30 | Releases both groups together, cars meet in the conflict zone | Failure: conflict explained, Retry |

Examples 3 and 4 are two valid solutions that both earn 3 stars. Example 5 shows a one-star clear that still counts as success.

## 50-level feasibility (decided 25 Oct 2026)
- 50 levels stay the target.
- Minimum shippable content is Worlds 1–3 (30 levels), if needed.
- Decide at the end of P5-03 (levels 1–10 authored and tuned) using measured hours per level, including validation and playtesting. If the projected total exceeds the schedule, ship 30 and add Worlds 4–5 as an update.
