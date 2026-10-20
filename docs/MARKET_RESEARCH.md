# Market Research — Signal Shift: Tiny City
**Snapshot:** 20 October 2026. Desk research only; player validation remains required.

## Summary
Puzzle is a large, competitive mobile category. That proves audience familiarity, not demand for this specific game. The hypothesis is a traffic-logic puzzle where players control signal groups to guide cars through conflicting routes. The differentiator must be signal scheduling, not merely “traffic in 3D.” Validate the mechanic before producing 50 levels or buying installs.

## Category context
AppMagic's *Mobile Market Landscape 2026* reports merge grew from 14% of puzzle revenue in 2024 to 20% in 2025; Block Puzzle and Logic Puzzle grew from smaller shares. This is directional context, not proof of opportunity for this title: https://appmagic.rocks/files/view/upload/Reports/EN_MobileMarkeLandscape2026.pdf

PocketGamer.biz reported on 27 July 2026, citing AppMagic's H1 2026 report, that puzzle accounted for over 44% of casual mobile spending, with reported puzzle spending of $4.9B and match-3 contributing about half. Third-party estimates, not a forecast: https://www.pocketgamer.biz/puzzle-accounts-for-44-of-casual-mobile-earnings-in-h1-2026/

## Competitors
**Car Out! Traffic Parking Games — Tripledot Studios**  
https://play.google.com/store/apps/details?id=com.flyingwhalegames.carout  
Listing snapshot observed 20 Oct 2026 displayed 10M+ downloads and approximately 4.7 stars; locale/date can affect values. Tap cars in a gridlocked layout to find an exit-clearing order; listing states ads and IAP. Takeaway: traffic puzzles are familiar; a car-removal clone is not differentiated.

**Traffic 3D Parking: Escape Jam — Pleasure City**  
https://play.google.com/store/apps/details?id=traffic.parking.jam.escape.car3d.games  
Snapshot observed 20 Oct 2026 displayed 10M+ downloads and a 4.9-star rating. Traffic/parking gridlock puzzle; listing states ads and IAP. Takeaway: 3D alone is not a unique selling point.

Store tiers/ratings are snapshots and do not reveal retention, revenue, conversion or acquisition costs. This is not yet a systematic review analysis or hands-on teardown.

## Positioning
**“Control the lights. Keep the tiny city moving.”** Players schedule traffic streams, protect conflict zones and prevent downstream queues blocking junctions. A polished miniature-city diorama supports recognition; optional Perfect Flow scoring encourages mastery. Test against a flat board and a traffic-jam interaction.

## Audience assumptions
- Initial audience hypothesis: general casual-puzzle players who enjoy short logic challenges and tactile presentation.
- Age target, rating and child-directed status are undecided. Do not assume child-directed status; review Families policy before child-directed marketing/ad SDK selection.
- English-first and India as a test market are hypotheses. Do not assume equal ad revenue across countries.

## Competitor comparison
| Dimension | Traffic/parking norm | Signal Shift hypothesis |
|---|---|---|
| Action | Tap car to move | Tap signal to control flow |
| Puzzle | Clear blocked exits | Schedule conflicting routes safely |
| Failure | Jam/blocked move | Explainable conflict/deadlock |
| Replay | More levels | Stars + optional Perfect Flow |
| Main risk | Clone density | Signal control may not feel distinct |

## Validation experiments
1. **Comprehension:** New player infers goal within 10 seconds. Test uncoached; record first action, hint use, mis-taps and explanation of outcome. Formative target: 8/10 understand without external explanation (not statistical proof).
2. **Enjoyment:** Test 3–5 levels, offer replay, observe voluntary replay and ask neutral questions.
3. **Art appeal:** Compare flat-board and diorama creatives using same mechanic/copy.
4. **Perfect Flow:** Compare completion-only results with optional mastery feedback; first completion must still feel good.
5. **Store clarity:** Show real screenshot and 10–20 second clip to unfamiliar people; reject misleading creatives.

## Monetization/acquisition
Consider opt-in rewarded ads only after first success and for a clearly described reward; one-time remove-ads only if ads exist. No forced ads during active play/tutorial or paid randomized rewards. Measure active users, eligible impressions, fill, realized eCPM, payer conversion, refunds and fees—not installs alone. Make provider integration replaceable; offline play must work when ads/billing fail. Use real gameplay clips and fix first-session friction before paid acquisition.

## Risks
| Risk | Countermeasure |
|---|---|
| Clone-like positioning | Validate signal control before production |
| Content burden | Data-driven authoring, handcrafted mechanics |
| Unclear simulation | Route previews and deterministic feedback |
| Low discovery | Strong real-gameplay creative/listing |
| Ads harm UX | Opt-in reward and sentiment measurement |
| Diorama performance | Choose device target and profile early |
| Policy delay | Recheck Play requirements before release |

## Backlog
- [ ] Hands-on teardown of five direct/adjacent games.
- [ ] Review representative positive/negative reviews.
- [ ] Save dated store screenshots and locale.
- [ ] Check title/trademark availability.
- [ ] Run concept comprehension tests.
- [ ] Recheck target API and testing requirements before submission.

## Sources
- AppMagic report: https://appmagic.rocks/files/view/upload/Reports/EN_MobileMarkeLandscape2026.pdf
- PocketGamer.biz: https://www.pocketgamer.biz/puzzle-accounts-for-44-of-casual-mobile-earnings-in-h1-2026/
- Car Out!: https://play.google.com/store/apps/details?id=com.flyingwhalegames.carout
- Traffic 3D Parking: https://play.google.com/store/apps/details?id=traffic.parking.jam.escape.car3d.games
- Play developer help: https://support.google.com/googleplay/android-developer/
- Target API: https://support.google.com/googleplay/android-developer/answer/11926878
- Godot Android export: https://docs.godotengine.org/en/4.6/tutorials/export/exporting_for_android.html

**Integrity:** Desk research dated 20 Oct 2026. Market figures are third-party estimates and store metrics are snapshots. Player validation has not occurred; no install, retention or revenue outcome is guaranteed.
