# Stitch UX Workflow — Signal Shift: Tiny City
**Status:** Prompt/handoff plan only. Screens are not claimed generated or approved. Tool: https://stitch.withgoogle.com/

## Design brief
Android phone, portrait-first pending testing; casual traffic-logic puzzle; miniature-city diorama; calm, clever, tactile, charming and legible. Core action: tap a signal to control vehicle movement. Age target undecided. Avoid generic dashboards, clutter, fake currency, false urgency, tiny controls, unreadable roads and decorative elements that look interactive.

## Master prompt
> Design a premium Android casual puzzle game called “Signal Shift: Tiny City” (working title). Players control traffic signals in a stylized miniature city. Use polished 3D diorama visuals, expressive small vehicles, clean road markings, compact buildings, warm daylight, soft shadows, tactile materials and restrained accents. Intersection and routes are the visual hero.
>
> Create a cohesive game UI, not a generic app dashboard. Use hierarchy, generous spacing, readable typography, clear touch targets and restrained motion. Never rely on red/green alone; pair colors with icons/shapes, labels or animation. Use stable three-quarter/isometric top-down framing.
>
> Design connected screens/states: main menu, world/level select, level intro, gameplay ready/running, pause, star results, failure/retry, settings, tutorial, no-network information and save recovery. Optional monetization only if separately approved; never interrupt tutorial or active play.
>
> Main menu has one dominant Play/Continue. Gameplay prioritizes road readability, places controls near their movements, shows objective/pause, avoids excessive counters. Results celebrate briefly and make Next Level primary.
>
> Include reusable tokens/components for type, spacing, color, radii, elevation, icons and motion. Design narrow Android phones and safe areas; adapt to other ratios. Include pressed/disabled/loading/error/confirmation states. No lorem ipsum, unexplained currency, fake notifications or inert controls.
>
> Deliver visual screens, components, interaction annotations and design-system notes reproducible in Godot. Visual design—not generated code—is the primary deliverable.

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
