# Level Authoring Guide

## Principle
Each level teaches or combines a small number of rules. It must be solvable, fair, readable, deterministic and playtested—not simply contain more vehicles.

## Required specification
Stable ID/title/world/order/difficulty/learning goal; road graph/geometry/capacity; signals/legal transitions/conflicts; vehicle spawns/routes/destinations; movement/headway/queues/downstream constraints; win/loss/restart; expected solutions/failure cases; star thresholds/scoring rationale; tutorial/audio/assets; automated validation and human playtest record.

## Workflow
1. Pick one learning objective or controlled combination.
2. Sketch graph/routes before decoration.
3. Enumerate conflicts and downstream capacity.
4. Write a safe solution and expected failures.
5. Set arrivals/queues without hidden timing assumptions.
6. Define achievable star thresholds.
7. Run schema/route/conflict/reachability/score validation.
8. Play from clean start; test restart, pause/resume and alternatives.
9. Ask an unfamiliar person to play uncoached.
10. Fix issues and record approval.

## Difficulty rubric
Rate 1–5: signal groups, active vehicles, conflict density, queue interactions, linked junctions, timing sensitivity and novelty. Do not increase all dimensions at once. Isolate new mechanics, then consolidate.

## Fairness and validation
Routes/destinations visible before consequential action; no frame-rate/random failure; explain illegal actions; safe solution exists unless explicitly teaching failure; avoid pixel-perfect timing; no unintended deadlock/impossible route; explain vehicle waits; restart reproduces initial state.
- [ ] Unique IDs/references and connected routes.
- [ ] Signals/conflicts/capacity consistent.
- [ ] Intended solution reachable; no accidental deadlock.
- [ ] Stars achievable and ordered.
- [ ] Tutorial/audio/assets resolve and are licensed.
- [ ] Restart/pause/resume/retry work.
- [ ] Automated validation and human test evidence recorded.
- [ ] Scene legible at phone scale.

## Evidence record
Record build/tester/device, first attempt, completion time, score/stars, confusion, failed assumptions, issues/fixes and approval. Author or AI solver alone cannot validate a level.

## Level schema (P0-07, decided 25 Oct 2026)
This is the logical schema. Every field maps to a rule in the "Traffic rules specification" in `docs/design/GAME_DESIGN_DOCUMENT.md`. The file format (typed Godot Resources or JSON) is chosen in P2-06. Whichever format is chosen must carry exactly these fields, and there is only ever one canonical format.

### Meta
| Field | Type | Rule |
|---|---|---|
| `schema_version` | int | Must be supported by the loader |
| `id` | string, e.g. `w1-l03` | Unique across all levels; never reused or renamed after release |
| `world`, `order` | int | Unique pair; ordering is gapless within a world |
| `title_key`, `objective_key` | string key | Text lives in the string tables, never in level data |
| `learning_goal` | string | One sentence, for authors and reviewers |
| `difficulty` | 7 ints, 1–5 | Rubric dimensions: signal groups, active vehicles, conflict density, queue interactions, linked junctions, timing sensitivity, novelty |

### Road graph
| Field | Type | Rule |
|---|---|---|
| `lanes[]` | `id`, `kind` (entry / link / exit), `slots` (int ≥ 1) | Slot count is the lane's capacity |
| `junctions[]` | `id`, `slots[]` (junction slot IDs) | Junction slots are the only places conflicts happen |
| `movements[]` | `id`, `junction`, `from_lane`, `to_lane`, `path[]` (junction slot IDs, in order), `signal_group` | `from_lane` ends at the stop line; `to_lane` is the exit segment for "don't block the box" |
| `conflict_zones[]` | `id`, `junction`, `slot`, `movements[]` | Authored explicitly, then cross-checked against the paths (rule V05) |

### Signals
| Field | Type | Rule |
|---|---|---|
| `signal_groups[]` | `id`, `initial` (GO / STOP), `locked` (bool), `movements[]`, `control_anchor` | `control_anchor` places the on-screen control near its movements |

### Vehicles
| Field | Type | Rule |
|---|---|---|
| `vehicles[]` | `id` (int), `class`, `ticks_per_slot` (int ≥ 1), `spawn_tick` (int ≥ 0), `route[]` (lane and movement IDs, in order), `required` (bool) | IDs are stable integers because they break ties in the tick order |

### Scoring and solution
| Field | Type | Rule |
|---|---|---|
| `reference_solution[]` | list of (`tick`, `signal_group`) taps | Authored. Must replay to a win |
| `s_par` | int | Equals the number of taps in the reference solution |
| `w3`, `w2` | int | Authored; `w3 ≤ w2` |
| `w_opt` | int | Computed by the validator, not typed by hand |
| `w_opt_proven` | bool | False if the validator's search hit its budget. Perfect Flow is disabled while false |

### Presentation and tutorial
`camera_preset`, `theme`, `set_dressing[]`, `audio_cues[]`, `hints[]` (`trigger`, `string_key`). All are references by ID to assets or strings. None of them can change simulation outcomes.

## Validation rules
The validator runs on every level, locally and in CI. Each error reports **level ID, rule code, field path, and a plain message**. It never skips an invalid level or loads it silently. The build fails on any error.

| Code | Check |
|---|---|
| V01 | All IDs unique within their kind; level `id` unique across the game |
| V02 | Every reference resolves (lanes, junction slots, movements, groups, assets, string keys) |
| V03 | Every vehicle route is contiguous: entry lane, then movement and lane pairs, ending at an exit lane |
| V04 | Every movement belongs to exactly one signal group |
| V05 | `conflict_zones` equal the junction slots shared by two or more movement paths, with no missing or extra zones |
| V06 | No signal group contains two movements that conflict with each other (otherwise GO could never be safe) |
| V07 | Numeric ranges: `slots ≥ 1`, `ticks_per_slot ≥ 1`, `spawn_tick ≥ 0`, difficulty 1–5, at least one required vehicle |
| V08 | The reference solution replays to a win, with no conflict or deadlock |
| V09 | Determinism: replaying the reference solution twice gives identical per-tick state hashes |
| V10 | Scoring order: `w_opt ≤` reference `W ≤ w3 ≤ w2`, and the reference uses exactly `s_par` taps |
| V11 | `w_opt` computed by bounded search over tap schedules; `w_opt_proven` set honestly |
| V12 | No deadlock reachable within the bounded search from the initial state, unless the level is flagged as teaching deadlock |
| V13 | The reference solution never taps a locked signal |
| V14 | Tutorial hint triggers refer to events that actually occur in the reference replay |

The validator proves a level is solvable and consistent. It does not prove the level is fun or fair. Every level still needs the human playtest record described above before it counts as done.

