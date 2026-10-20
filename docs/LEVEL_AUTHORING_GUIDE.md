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
