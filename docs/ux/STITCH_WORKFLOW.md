# Stitch UX Workflow — Signal Shift: Tiny City
**Status:** P1-01 drafted 25 Oct 2026 (master prompt v2 and visual-reference brief). No screens have been generated or approved yet. Tool: https://stitch.withgoogle.com/

## Design brief
Android phone, portrait-first (D-012); casual traffic-logic puzzle; miniature-city diorama; calm, clever, tactile, charming and legible. Core action: tap a signal to control vehicle movement. General casual audience, 18+, not child-directed (D-009). English UI (D-010). No ads, purchases, or currency in v1 (D-006). Avoid generic dashboards, clutter, fake currency, false urgency, tiny controls, unreadable roads and decorative elements that look interactive.

## Visual-reference brief (P1-01)
Collect references for **mood only**. Never copy another game's art, layouts, characters, or UI. Record every reference image's source in the review log, and do not commit images without a license.

**Look for:**
- Tilt-shift photography of real cities (small-scale feel, shallow depth of field).
- Model railway and architectural dioramas (tactile materials, neat streets, painted surfaces).
- Clean low-poly or soft-shaded isometric city illustration (simple shapes, readable roads).
- Warm late-morning daylight with soft grounded shadows.
- Toy-like but tidy vehicles: rounded, chunky silhouettes, readable from above.

**Avoid (anti-references):**
- Neon, casino, or slot-machine styling.
- Cluttered asset-pack cities where props compete with roads.
- Flat hyper-casual boards with no depth.
- Realistic gritty traffic, crash imagery, or damage effects.
- Night scenes or heavy fog for gameplay levels.

**Palette:** use the `color.*` tokens in `docs/ux/DESIGN.md`. World colors stay softer than the UI accent colors, so controls always stand out.

**Signal states:** use the binary mapping in `docs/ux/DESIGN.md` §7 (GO, STOP, BLOCKED, DISABLED), each with a color, an icon, and a label.

## Master prompt v2 (P1-01)
Paste this first in Stitch, then add one screen prompt at a time.

> Design a premium Android casual puzzle game called "Signal Shift: Tiny City". Portrait phone layout (about 1080 × 2400 px, with Android status and gesture bars as safe areas). Audience: adult casual puzzle players. English text.
>
> Players control traffic signals in a stylized miniature-city diorama: warm daylight, soft shadows, tactile painted materials, compact buildings, chunky rounded vehicles, clean road markings. Use a stable three-quarter top-down camera. The intersection, its routes, and its signals are always the visual hero.
>
> This is a calm thinking puzzle, not a reflex game. No timers, no countdowns, no urgency. Each signal is binary: GO or STOP. Show every signal state with a color, an icon, and a text label, never color alone: GO = green with an up arrow and "GO"; STOP = red with a solid bar and "STOP"; BLOCKED = amber with a slashed circle and "BLOCKED"; DISABLED = grey with a dashed outline.
>
> Use these colors: text #202B36, muted text #5E6B76, background #F5F2E9, cards #FFFFFF, raised panels #FFF9ED, primary action #276B67 (pressed #1D514E), stars #F2C45C, success #247A55, warning #8B5A12, danger #B33D3D, borders #D8D8CF, focus #1E5CC6. One clean sans-serif typeface. 4 dp spacing grid. Corner radius 12 dp for controls, 18 dp for cards, 24 dp for dialogs. Touch targets at least 48 × 48 dp.
>
> Every screen has exactly one primary action. Text never sits directly on busy 3D imagery without a solid panel. Never cover roads, signals, vehicles, routes, or destinations with UI.
>
> Do not include ads, purchases, coins, gems, currency, energy, lives, daily rewards, notifications, or account sign-in. No lorem ipsum.
>
> Deliver visual screen designs with component states and short interaction notes. These are proposals for human review.

## Screen prompt order (P1-02 to P1-04)
Run these after the master prompt, one at a time, and review each before the next.
1. **Gameplay, READY** (P1-03): "Level 3 of World 1, frozen before start. One four-way junction, two signal groups, four small cars waiting. Route arrows and destinations visible. Objective at top: 'Get all 4 cars home safely.' Pause button top-right. Signal controls next to their roads. Start button as the primary action."
2. **Gameplay, RUNNING with BLOCKED feedback** (P1-03): "Same level running. One car waiting at a GO signal because its exit is full; show the BLOCKED state and the short reason 'Exit full.'"
3. **Failure** (P1-04): "Two cars frozen in the junction, highlighted. Message: 'Car 4 entered while Car 2 was still crossing.' Retry is primary; Level Select is secondary. Calm, not alarming."
4. **Results, 3 stars** (P1-04): "Level complete. Three stars, flow score 850, optional Perfect Flow badge. Next Level is primary; Replay and Level Select are secondary."
5. **Results, 1 star** (P1-04): "Level complete with one star. Still celebratory. Show 'Fewer waits earn more stars' as a hint."
6. **Main menu** (P1-02): "Miniature-city hero image, title, one Play/Continue button, small progress line, Settings and Level Select as secondary."
7. **Level select** (P1-04): "World 1 grid of 10 levels: completed with stars, current, and locked states, each distinguishable without color."
8. **Pause, Settings, Tutorial overlay** (P1-04): "Pause sheet with Resume primary. Settings with independent Music, Sound Effects, Haptics toggles, plus Help, Privacy, Credits. Tutorial overlay: one short instruction pointing at one signal, never covering its road."

Gameplay comes first because it is the hardest screen and sets the rules for everything else.

## Screens and acceptance
1. Main menu: city hero, Play/Continue, progress, map/settings; one primary action.
2. Gameplay: route previews, signals/conflicts, objective/pause, large controls; ready/running/selected/invalid/blocked/progress states; no intrusive timer/ad/store.
3. Tutorial: three contextual overlays, one rule at a time, no countdown, never cover referenced route/control.
4. Pause: freeze puzzle; Resume primary, Restart/Exit with confirmation.
5. Results: short stars, optional score details, Next Level primary, one/two/three-star and improved-replay states.
6. Failure: explain conflict/deadlock, Retry primary, no forced ad.
7. Level select: readable progress; grid/list fallback if 3D map harms usability.
8. Settings: independent Music/SFX/Haptics, Help, Accessibility, Privacy, Credits/Licenses.
9. Optional monetization only after approval: clear reward/opt-in and unavailable/cancelled/pending/success/failure/restore states.

## DESIGN.md
Define semantic colors; type scale; spacing/radii/elevation; button/signal/card/dialog/toast/progress/star/toggle states; motion/reduced motion; icon/touch-target rules; responsive/safe-area rules; contrast/localization; Godot theme mapping. Tokens are not approved until actual Stitch output is reviewed.

## Flow
Main Menu → Level Select → Level Intro → Gameplay → Results → Next Level. Gameplay → Pause → Resume/Restart/Map confirmation. Gameplay → Failure → Retry. Settings from menu and optionally pause. Monetization never blocks core play.

## Handoff/QA
For each screen record reference image, hierarchy, tokens, states, transitions, responsive behavior, accessibility, assets and approved deviations. Confirm consistent visual direction, color-independent signal states, safe areas, no dead ends, persistent settings, exported references and human approval before Godot implementation. If a design cannot be implemented without harming usability/performance, ask for a decision.
