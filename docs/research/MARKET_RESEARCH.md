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

## Signal-control competitor audit (P0-02)
**Checked:** 25 Oct 2026, web sources only. No hands-on play, store screenshots, or review sampling yet. Store values are snapshots and locale-dependent.

**Crazy Traffic Control — BoomHits sp. z o.o.**
App Store listing (https://apps.apple.com/us/app/-/id1529430333): free with in-app purchases ("NO ADS" $2.99, coin bundles $4.99–$19.99). Casual category. About 4.2 stars from 1.7K ratings. Listing says: "Tap & change lights - you're the one responsible now!" Intersections grow more complex as you progress. Version 3.9.3, last updated Aug 19 (year not shown). No Google Play data checked yet.
*Takeaway:* This is the closest mechanic match (tap to change lights in real time) and it already uses a free-with-IAP model. Ads and coin currency are part of its model, which matters for our "no fake currency" principle.

**Traffix — developer not stated in the source**
Press coverage (GIGAZINE, 5 Aug 2019: https://gigazine.net/gsc_news/en/20190805-traffix) describes a manual traffic-signal puzzle. The player taps a signal to pass one car, or double-taps to release a queue. Tapping again toggles red and green. Stages clear by safely sending about 40–80 cars. Some cars follow signals ("white") and others run free ("black"). Ten accidents end the game. Listed as a paid app (480 yen at the time) with no IAP or ads mentioned. Available on iOS, Android, and Steam (https://store.steampowered.com/app/1102580/Traffix). Android package com.infinity.traffix is listed on SimilarWeb; current Play status not verified.
*Takeaway:* This game already does manual signal control with queue release, which is close to our core loop. Our differentiator cannot be "manual signal control" alone. It has to come from the level-design, route-conflict, and downstream-capacity rules, and we need to test that. This is a significant finding and it weakens the positioning in the next section.

**Earlier desk entries** (Car Out!, Traffic 3D Parking) remain below as recorded on 20 Oct 2026. Neither is a signal-control game.

**Implications for P0 decisions:**
- Re-run the differentiation hypothesis against Traffix and Crazy Traffic Control before the GDD is locked.
- Free-with-IAP (Crazy Traffic Control) and paid (Traffix) are both live models. The no-monetization v1 default is still viable, but the paid-premium option should be assessed as well.
- Check Traffix's current Play status and version before using it as evidence in the store listing.

**Open backlog from this audit:** store screenshots with dates and locale, review sampling, hands-on teardown, and a current Traffix Play listing check.

## Title check (P0-09, 25 Oct 2026)
Web search only. This is not a legal trademark search.
- **"Signal Shift":** no app or game with this name found on Google Play, the App Store, or Steam. Nearby names: an itch.io creator page named "SignalShift" (https://signalshift.itch.io, content not reviewed) and an itch.io game "Shifting Signals" (https://spoocejuice.itch.io/shifting-signals). Neither is a store listing for a traffic game.
- **"Tiny City":** a generic phrase used in several titles, including "Tiny City Racer" on the App Store (https://apps.apple.com/us/app/id1562171345) and a "tiny city" itch.io project (https://gamedevgio.itch.io/tiny-city). It works as a subtitle but cannot be protected on its own.
- David also checked and found the title clear.
- **Still required before P9-02 (final title and package ID):** a formal registry search (IP India classes 9 and 41, plus USPTO and EUIPO if launching beyond India) and a domain and social-handle check.

## Competitor matrix (P0-03, 25 Oct 2026)
Built from the store pages and press sources cited above. No reviews have been sampled yet, so review themes are marked "not sampled".

| | Crazy Traffic Control | Traffix | Car Out! | Traffic 3D Parking: Escape Jam | **Signal Shift (planned)** |
|---|---|---|---|---|---|
| Player action | Tap lights in real time | Tap a signal to pass one car; double-tap to release a queue | Tap cars to leave a jam | Tap cars to leave a jam | Tap signal groups (binary GO/STOP) |
| Core loop | Keep cars from crashing as junctions get busier | Send 40–80 cars safely per stage; 10 accidents end the game | Find a clearing order | Find a clearing order | Plan, switch, deliver every car; stars for low waiting |
| Pressure | Real-time, reflex | Real-time; accidents build up | Low | Low | None early; no timer; level starts frozen |
| Failure | Crash | Accident count | Blocked move | Blocked move | Named conflict or deadlock, frozen before any crash |
| Content | Levels of growing complexity | Stages | Many levels | Many levels | 50 authored levels across 5 worlds (30 minimum) |
| Replay hook | Not checked | Not stated | More levels | More levels | 3 stars, flow score, optional Perfect Flow |
| Art | Not checked | Not checked | 2D/3D cars | 3D | Miniature-city diorama |
| Monetization | Free; IAP: no-ads $2.99, coins $4.99–$19.99 | Paid (480 yen in 2019); no IAP or ads mentioned | Ads and IAP (per listing) | Ads and IAP (per listing) | None in v1 |
| Store signals | ~4.2★, 1.7K ratings (App Store) | Not checked | 10M+ downloads, ~4.7★ | 10M+ downloads, ~4.9★ | — |
| Review themes | Not sampled | Not sampled | Not sampled | Not sampled | — |
| What we take from it | Closest mechanic; its coins clash with our no-fake-currency rule | Proves manual signal control already exists; we must win on planning and network puzzles | Traffic puzzles are familiar | 3D alone is not a selling point | Thinking puzzle, not reflex game (D-017) |

**Gaps to fill before launch:** sample 20 or more reviews per game, check Crazy Traffic Control and Traffix on Google Play, record art and replay hooks from hands-on play, and refresh the store numbers.

## Positioning
**Updated 25 Oct 2026:** After the P0-02 audit, the differentiator is "a thinking puzzle, not a reflex game": planned, deterministic, explainable, with network reasoning and authored levels. See `docs/design/GAME_DESIGN_DOCUMENT.md`. The original positioning below still applies.

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
