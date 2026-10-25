# Usability Test Plan — Signal Shift: Tiny City
**Task:** P0-08 · **Date:** 25 Oct 2026 · **Status:** Decided (delegated by David); review at the Phase 0 gate.

These are formative tests with small samples. They show where players struggle. They do not prove market success, and no result here should be reported as statistically significant.

## Hypotheses
| ID | Hypothesis | Tested in |
|---|---|---|
| H1 | Players understand signal control without a long tutorial | Round 2 |
| H2 | Near-misses and Perfect Flow feel satisfying, not stressful | Round 2, Round 3 |
| H3 | The miniature-city look increases interest compared with a flat board | Round 1 |
| H4 | Players replay levels to improve stars | Round 3 |
| H5 | A small set of mechanics produces enough level variety | Round 3 |
| H6 | Optional monetization does not damage early trust (deferred; no v1 monetization) | Not tested in v1 |
| H7 | Store screenshots and a short real-gameplay clip explain the mechanic quickly | Round 1 (concept), Phase 9 (real build) |
| H8 | Players see it as a thinking puzzle, not a reflex game (differentiator, D-017) | Round 2 |
| H9 | Players understand the commitment rule after their first conflict failure | Round 2 |

## Rounds
| Round | When | What players see | Participants |
|---|---|---|---|
| 1. Concept | Phase 1, after Stitch screens | Gameplay screenshot, diorama vs flat-board image, 3-frame storyboard | 8 |
| 2. Core mechanic | Phase 3, P3-13 | Greybox build, levels 1–5, on a real mid-range Android phone | 10 |
| 3. First world | Phase 5, after P5-03 | Polished World 1 (levels 1–10) | 10 |

Each round uses new participants who did not work on the game. A round may be repeated after fixes, always with new participants.

## Recruitment and privacy
- Casual mobile players, 18 or older, comfortable reading English. Include players in India (test market). No one from the project.
- Mix of genders and ages where possible. Record only a pseudonym (P01, P02…), age band, and how often they play mobile puzzles.
- Get spoken or written consent before the session, including for any screen or audio recording.
- Delete raw recordings after notes are written. Never store names, phone numbers, or contact details in the repository.

## Session script (Round 2; adapt for Rounds 1 and 3)
Facilitator reads this aloud and does not explain the game.

1. **Intro (1 min):** "Thanks for helping. We are testing the game, not you. There are no wrong answers. Please think out loud: say what you're looking at and what you expect to happen. I can't help during the game, but I'll answer questions at the end."
2. **First look (no time limit):** Hand over the phone on the Level 1 READY screen. Say only: "Please start whenever you like." Start the timer. Do not point or hint.
3. **Play levels 1–5.** Stay silent. If the participant is stuck for 90 seconds, say "What are you trying to do right now?" and log it as an assist.
4. **After level 1:** "In your own words, what is the goal of this game?"
5. **After the first conflict failure:** "What happened there? Why did the level end?"
6. **After level 5:** "You can stop here or keep playing. It's completely up to you." Log the choice. If they continue, observe for up to 3 more minutes.
7. **Closing questions (neutral wording):**
   - "How would you describe this game to a friend?" (Record the exact words.)
   - "How easy or hard was it to play?" (1 = very hard, 7 = very easy.)
   - "How much did you enjoy it?" (1–5.)
   - "Was there anything that felt unfair or confusing?"
   - "Was there anything you wanted to do but couldn't?"
8. **Thank them.** Answer their questions now.

## Metrics (per participant)
| Metric | How measured |
|---|---|
| Time to first meaningful action | Seconds from READY screen to first signal tap |
| Goal explained correctly | Yes/no, from step 4, scored against "control signals so all cars get through safely" |
| Time to first success | Seconds to first level win |
| Mis-taps | Taps that hit no control, or a locked signal |
| Failures by cause | Conflict (commitment rule or other), deadlock |
| Commitment rule explained | Yes/no, from step 5 |
| Assists | Count of the 90-second prompts |
| Voluntary continuation | Yes/no, from step 6 |
| Star replays | Count of replays of an already-won level |
| Descriptor | Puzzle/thinking words vs reflex/speed words, from step 7 |
| Ease (SEQ) and enjoyment | 1–7 and 1–5 ratings |
| Unfair or confusing moments | Level and quote |

## Go / no-go criteria (Round 2)
| Criterion | Go threshold (n = 10) | Hypothesis |
|---|---|---|
| Comprehension | ≥ 8 of 10 explain the goal correctly after level 1 with no assist; median first action ≤ 10 s | H1 |
| Commitment rule | ≥ 7 of 10 explain their first conflict failure correctly | H9 |
| Differentiator | ≥ 6 of 10 describe it with puzzle/thinking words rather than reflex/speed words | H8 |
| Enjoyment | ≥ 6 of 10 choose to keep playing; median enjoyment ≥ 4 of 5 | H2 |
| Fairness | No level where ≥ 3 of 10 call a failure unfair or unclear | H1, H9 |

**Decision rules:**
- **Go:** every criterion met. Proceed to P3-15 gameplay acceptance.
- **Iterate:** one or more criteria missed. Fix the cause (tutorial, feedback, level design), then rerun Round 2 with 10 new participants. At most two iterations.
- **No-go:** comprehension or differentiator still missed after two iterations. Stop and review the concept with David (change the core mechanic, pivot, or drop) before more production work.

Round 1 (concept) uses softer criteria: ≥ 6 of 8 can say what the player does from the screenshot, and the diorama is preferred over the flat board by ≥ 5 of 8. Missing these changes the art direction or screenshots, not the go/no-go decision.

## Recording template
| Participant | Device | First action (s) | Goal correct | First win (s) | Mis-taps | Failures (cause) | Rule explained | Assists | Continued | Star replays | Descriptor (quote) | SEQ | Enjoy | Unfair/confusing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P01 | | | | | | | | | | | | | | |

Store completed sheets in `docs/research/usability/` as one file per round (for example `round-2a.md`), with pseudonyms only.
