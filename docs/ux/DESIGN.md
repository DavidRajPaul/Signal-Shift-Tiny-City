# Design System — Signal Shift: Tiny City

**Path:** `docs/ux/DESIGN.md`  
**Version:** 0.1  
**Status:** Proposed; requires human approval before production UI implementation. Phase 0 decisions applied 25 Oct 2026 (see §16).  
**Platform:** Android mobile game, Godot 4. Portrait-first is a working assumption, not an approved decision.

This document defines reusable interface rules. `docs/ART_BIBLE.md` governs 3D world art; `docs/GAME_DESIGN_DOCUMENT.md` governs gameplay and screen intent. Open product decisions remain open—agents must not silently decide them.

## 1. Design intent

Build a polished, welcoming interface for a premium-feeling miniature-city traffic puzzle. The city and intersection are the stars. UI must help players understand the puzzle, make confident decisions, and feel rewarded without obscuring roads, signals, vehicles, routes, conflict zones, or destinations.

Principles:
1. **Readability before decoration.** Gameplay information must be legible at a glance on a phone.
2. **One dominant action.** Each screen has one clear primary action.
3. **Warm, tactile, precise.** Pair the miniature-diorama world with clean, high-contrast UI.
4. **Never color-only.** Add labels, icons, shapes, patterns, or motion to color-coded states.
5. **Fast and respectful.** Acknowledge input immediately; keep transitions brief and skippable.
6. **Honest rewards.** Explain stars and scores; no fake currency, fake scarcity, or manipulative prompts.
7. **Accessible by default.** Respect safe areas, text scaling, contrast, touch targets, reduced motion, and localization.
8. **No unfinished states.** Loading, empty, error, pause, success, and failure states need intentional design.

## 2. Visual language

- **World:** stylized 3D miniature-city diorama, warm daylight, controlled materials, soft shadows, readable roads and vehicles.
- **Interface:** clean surfaces, generous spacing, restrained highlights, rounded geometry, crisp typography.
- **Mood:** charming, optimistic, clever, calm, satisfying. Avoid casino styling, aggressive neon, clutter, or generic dashboard visuals.
- **Hierarchy:** the intersection remains the focal point during play. UI chrome recedes when not needed.
- Do not place text over busy 3D imagery without an opaque or sufficiently solid backing panel.
- Reserve saturated accents for actions, selection, and important states.

## 3. Proposed color tokens

These are initial values for mockups and usability testing. Contrast ratios below were computed from the hex values (WCAG 2.x relative luminance). They must be re-checked on rendered screens before release.

| Pair | Ratio | Status |
|---|---:|---|
| `ink` on `canvas` | 12.85:1 | Pass, body text |
| `ink` on `surface-raised` | 13.71:1 | Pass, body text |
| `ink-muted` on `canvas` | 4.88:1 | Pass, body text (AA) |
| `ink-muted` on `surface` | 5.47:1 | Pass, body text (AA) |
| `white` on `primary` | 6.20:1 | Pass, button label |
| `white` on `primary-pressed` | 8.98:1 | Pass, button label |
| `ink` on `accent-gold` | 8.78:1 | Pass, star label |
| `success` / `warning` / `danger` on `surface` | 5.26 / 5.88 / 5.75:1 | Pass, text |
| `primary` on `canvas` | 5.54:1 | Pass, text |
| `focus` on `canvas` | 5.52:1 | Pass, focus ring (3:1 required) |
| `outline` on `surface` | 1.43:1 | **Decorative only.** Never the sole boundary of a control or input (3:1 non-text required) |
| `accent-coral` on `surface` | 3.46:1 | **Not for text.** Passes 3:1 for non-text graphics only |

| Token | Hex | Use |
|---|---|---|
| `color.ink` | `#202B36` | Primary text |
| `color.ink-muted` | `#5E6B76` | Secondary text; verify contrast |
| `color.canvas` | `#F5F2E9` | Warm background |
| `color.surface` | `#FFFFFF` | Cards and dialogs |
| `color.surface-raised` | `#FFF9ED` | Highlighted panels |
| `color.primary` | `#276B67` | Primary action, selected navigation |
| `color.primary-pressed` | `#1D514E` | Pressed primary action |
| `color.accent-gold` | `#F2C45C` | Stars and earned highlights |
| `color.accent-coral` | `#D96855` | Warm accent |
| `color.success` | `#247A55` | Success plus icon/label |
| `color.warning` | `#8B5A12` | Warning plus icon/label |
| `color.danger` | `#B33D3D` | Failure/destructive state plus icon/label |
| `color.outline` | `#D8D8CF` | Borders and dividers |
| `color.focus` | `#1E5CC6` | Focus indicator |

Rules: never rely on red/green alone; gold is not a default button color; validate contrast in actual states before release. Add a dark theme only if approved as a product requirement. Pressed and disabled states need their own contrast checks.

## 4. Typography

Choose one highly legible sans-serif family with suitable commercial-use rights and reliable glyph coverage. Record its name and license before shipping.

| Token | Proposed size | Weight | Use |
|---|---:|---|---|
| `type.display` | 30–34 sp | Bold | Main title / major result |
| `type.title` | 24–28 sp | Bold | Screen titles |
| `type.section` | 18–20 sp | Semibold | Section headings |
| `type.body` | 16 sp | Regular | Instructions and body copy |
| `type.body-emphasis` | 16 sp | Semibold | Important text |
| `type.label` | 14 sp | Medium | Buttons and metadata |
| `type.caption` | 12–13 sp | Medium | Nonessential secondary hints |

These are starting points. Test compact phones, large system text, and all supported languages. Essential instructions must not depend on caption-sized text. Avoid long all-caps labels and decorative fonts that reduce readability.

## 5. Spacing, shape, and elevation

Use a 4 dp base grid.

| Token | Value | Use |
|---|---:|---|
| `space.1` | 4 dp | Micro-gap |
| `space.2` | 8 dp | Tight related items |
| `space.3` | 12 dp | Compact spacing |
| `space.4` | 16 dp | Standard padding/gap |
| `space.5` | 20 dp | Group separation |
| `space.6` | 24 dp | Card padding / major gaps |
| `space.8` | 32 dp | Section separation |
| `space.10` | 40 dp | Large layout break |

- `radius.control`: 12 dp; `radius.card`: 18 dp; `radius.modal`: 24 dp.
- Use pill shapes only for chips, tags, and compact counters.
- Keep elevation to a few levels: flat, card, floating control, modal.
- Prefer subtle borders and shadows over heavy blur/glass effects.
- Keep corner radii consistent; avoid making every surface look inflated or toy-like.

## 6. Layout and safe areas

- Portrait is the working assumption until Phase 0 approval and gameplay tests.
- Respect Android status/navigation bars, cutouts, rounded corners, gesture areas, and display scaling.
- Use responsive anchors/containers, not coordinates tuned to one screenshot.
- Keep critical controls and text away from screen edges.
- The playfield receives the largest practical share of the gameplay viewport.
- Never cover signal heads, vehicle paths, conflict zones, routes, or destinations with overlays.
- Use a clear 2D level grid/list if a 3D map harms usability or performance.
- Test compact and tall phones, supported aspect ratios, lifecycle interruptions, and large text.

## 7. Component rules

### Primary button
Use for the single most important action: **Play**, **Continue**, **Next Level**, or **Retry**. High-contrast filled treatment, concise verb-first label, immediate pressed feedback. States: default, pressed, focused, disabled, loading.

### Secondary button
Use for alternatives such as **Settings**, **Help**, **Resume**, and **Level Select**. Lower visual weight than the primary action, but equally readable and tappable.

### Icon button
Use for pause, close, sound, music, and haptics. Give it a meaningful accessible name. Minimum interactive area should be 48 × 48 dp even if the visible icon is smaller.

### Card / panel
Group related information; do not put every item in a card. Use consistent padding and heading hierarchy. Gameplay panels over the 3D world need a solid enough backing for legibility.

### Signal control
Binary signals are approved for v1 (see §16). Proposed state mapping. Every state uses a token, an icon or shape, and a text label:

| State | Color token | Icon / shape | Label |
|---|---|---|---|
| Go (green phase) | `color.success` | Up arrow | "GO" |
| Stop (red phase) | `color.danger` | Solid bar | "STOP" |
| Blocked / rejected tap | `color.warning` | Circle with slash | "BLOCKED" + reason |
| Disabled / locked | `color.ink-muted` | Dashed outline | Reason shown on tap |

Signal states are a proposal. Confirm them with the Art Bible's signal-head design before implementation.

Show state with **color plus a distinct icon/shape/label or pattern**. Distinguish active, changing, blocked/invalid, and disabled states. Make controls comfortably tappable without hiding movements. Acknowledge taps immediately, including rejected transitions. UI must reflect authoritative simulation rules; visual effects must not imply a movement is legal when it is not.

### Route and queue indicators
Use consistent arrows, endpoint markers, and selected-route emphasis. Route previews must differ from road markings and decoration. Show queue/downstream-capacity information when relevant, not as permanent clutter. Avoid continuous pulsing.

### Stars and score
Differentiate earned from unearned stars. Explain scoring criteria in plain language. A one-star clear must feel like success; Perfect Flow is an optional mastery target unless explicitly approved otherwise. Do not style earned progress like currency or loot boxes.

### Modal / dialog / bottom sheet
Use for pause, settings, confirmations, and results. State the purpose, provide concise supporting copy, and emphasize one primary action. Confirm restart/exit when meaningful progress could be lost. Back/outside-tap behavior must be predictable and must not silently discard important progress.

### Toast / hint / feedback banner
Use for brief non-blocking feedback. Essential instructions and failure explanations must remain visible until understood; do not put them only in transient toasts. Pair status icons with text.

### Toggle / slider
Use for Music, Sound Effects, Haptics, and approved accessibility options. Show state/value clearly, apply changes immediately, and persist settings locally. Music and SFX controls remain independent.

## 8. Screen patterns

These are layout contracts, not finished mockups.

### Loading / first launch
Show the approved mark and restrained miniature-city imagery. Show progress only when actual progress is available—never fake percentages. Provide retry for load failure. Core play must not require a network.

### Main menu / city hub
Use a city hero, game title, and one dominant **Play** or **Continue** action. Show progress unobtrusively. Keep Level Select, Settings, Help, Credits secondary. No fake currency, forced ad, or purchase prompt on first launch.

### World / level select
Make unlocked, completed, current, and locked states distinguishable by more than color. Show level number and stars. Explain unlock requirements without false urgency. Preserve selection/scroll position on return. Use a grid/list fallback if a 3D map is unclear.

### Level intro / objective
State the goal in one short sentence. Introduce only the mechanic needed. Let the player begin when ready; early levels should not use countdown pressure.

### Gameplay HUD
- **Top:** concise objective/progress and pause.
- **Main:** intersection, vehicles, routes, signals, destinations.
- **Action area:** signal controls near their movements without obscuring the board.
- **Feedback:** contextual hint or state explanation only when useful.
Avoid permanent counters that do not help a decision. Undo appears only if the feature is approved.

### Pause
Freeze simulation first. **Resume** is primary; Restart and Exit to Level Select are secondary. Confirm destructive actions as needed. Resume must not duplicate movement or inputs.

### Success
Persist result before navigation. Show a brief, skippable star reveal and clear result sentence. **Next Level** is primary when available; Replay and Level Select are secondary. Never force the player to watch an animation.

### Failure
Explain the real cause in understandable language, using simulation data. **Retry** is primary. No forced ad or purchase prompt. Never blame the player for ambiguous rules or an unvalidated level.

### Settings
Provide independent Music, SFX, and Haptics controls; Help, accessibility, Privacy, Credits, and Licenses as appropriate. Apply changes immediately and persist them.

### Tutorial / help
Teach one rule at a time with concise contextual copy and visual guidance. Never require first-action failure to teach. Allow tutorial replay. Use visuals alongside text where they improve comprehension.

## 9. Motion and input

Motion should explain state, confirm input, or celebrate a meaningful result—not block decisions or determine gameplay outcomes.

| Interaction | Starting duration | Rule |
|---|---:|---|
| Button feedback | 80–140 ms | Immediate acknowledgement |
| Panel transition | 160–240 ms | Short fade/slide |
| Signal transition | Simulation-defined | UI follows authoritative game state |
| Hint emphasis | 180–300 ms | Brief, not continuous |
| Star reveal | 250–450 ms per beat | Skippable |
| Screen transition | 160–260 ms | Avoid unnecessary camera motion |

These timings require prototype testing. Simulation must be independent of animation and render frame rate. Reduced-motion mode removes nonessential scaling, repeated pulses, and long celebrations without removing essential state feedback.

Input rules:
- Acknowledge taps immediately.
- Do not silently ignore unavailable actions; explain why.
- Prevent duplicate actions only while a real transition is underway.
- Keep Back/pause behavior consistent.
- Handle Android background/resume safely according to approved gameplay rules.

## 10. Accessibility and localization

- Never communicate signal, route, success, failure, or lock state through color alone.
- Aim for touch targets of at least 48 × 48 dp.
- Measure text/icon contrast in actual screens; do not claim compliance without testing.
- Support system font scaling without clipping essential copy or primary actions.
- Externalize strings for translation; do not bake UI text into textures.
- Provide visual equivalents for essential audio cues.
- Haptics must be optional and independently disabled.
- Avoid rapid flashing and unnecessary motion.
- Test color-vision deficiency simulations, large text, compact displays, and TalkBack where applicable.
- English is the initial working language (confirmed 25 Oct 2026). India is the test market. Any Tamil or other localization requires font, layout, and text-expansion testing before it is advertised.

## 11. Audio and haptics

Coordinate with `docs/AUDIO_BIBLE.md`:
- UI press: short, quiet acknowledgement.
- Legal signal change: clear, restrained cue.
- Rejected action: distinct but non-punitive cue plus visual explanation.
- Safe passage: subtle confirmation without excessive repetition.
- Success/unlock: warm, short reward.
- Failure: calm and informative, not alarm-like.
Music, SFX, and haptics are independent settings. Essential information is never audio-only. Record commercial-use rights for all assets and review loudness in-game.

## 12. Monetization guardrails

Monetization remains conditional on gameplay validation, business review, and policy review; this document does not authorize implementation.
- No ads during an active puzzle, tutorial, pause, or failure explanation.
- No forced ad between every level.
- Rewarded ads, if approved, are optional and disclose the reward before opt-in.
- Never disguise ads as gameplay buttons or use misleading close controls.
- A remove-ads purchase must state exactly what it removes.
- No paid randomized rewards, pressure timers, fake scarcity, or manipulative prompts.
- Core play and owned progress remain usable offline; provider-dependent actions fail gracefully.
- Use approved platform billing and test purchase flows separately.
- Remove monetization from v1 if it harms trust, usability, or compliance.

## 13. Godot implementation guidance

This is a design contract, not permission to start production UI before phase approval.
- Create reusable scenes/components for buttons, cards, modals, toggles, banners, stars, and level tiles.
- Centralize tokens in a theme/resource structure; avoid scattered hard-coded values.
- Separate UI state from authoritative simulation state.
- Use responsive containers/anchors and meaningful control names.
- Define default, focused, pressed, disabled, loading, error, success, and failure states as applicable.
- Keep UI animations skippable and independent of simulation decisions.
- Record licensing, maintenance, size, and platform implications before adding UI plugins.
- A screenshot or placeholder scene is not evidence that a production UI is implemented.
- Choose exact Godot resource format/folder locations during approved technical setup and document them in `docs/TECHNICAL_ARCHITECTURE.md`.

Suggested token namespaces: `color.*`, `type.*`, `space.*`, `radius.*`, `elevation.*`, `motion.*`, `size.touch-min`.

## 14. Stitch / design-generation workflow

1. Read this file, `docs/ART_BIBLE.md`, and screen requirements in `docs/GAME_DESIGN_DOCUMENT.md`.
2. Generate one screen at a time, starting with gameplay HUD and main menu.
3. Specify device class, safe areas, primary action, hierarchy, state, and prohibited elements.
4. Request consistent use of the approved tokens and reusable components.
5. Review readability, accessibility, and consistency with the miniature-city direction.
6. Reject invented currencies, unapproved monetization, color-only signals, unreadable text, and controls covering roads.
7. Record accepted reference, version/date, and rationale in the design review log.
8. Treat generated screens as proposals, not approved implementation or licensed production art.
9. Obtain human approval before using a design as implementation source of truth.
10. Verify the implemented result on device; desktop mockup fidelity alone is insufficient.

### Prompt template

> Design the **[screen/state]** for *Signal Shift: Tiny City*, a premium-feeling, offline-first Android traffic-logic puzzle. Follow `docs/ux/DESIGN.md`, `docs/ART_BIBLE.md`, and `docs/GAME_DESIGN_DOCUMENT.md`. Use the proposed design tokens and a warm, restrained, high-contrast UI complementing a tactile miniature-city diorama. The user goal is **[goal]** and primary action is **[action]**. Respect Android safe areas and scalable layouts. Never obscure roads, signal controls, vehicles, routes, or destinations. Do not rely on color alone, invent currencies, add unapproved monetization, or create unsupported mechanics. Show **[default/loading/disabled/error/success/failure]** state. Treat this as a proposal for human review, not final approval.

## 15. Design QA checklist

- [ ] One clear primary action and predictable navigation.
- [ ] Readable on a compact phone and with larger system text.
- [ ] Comfortable touch targets and spacing.
- [ ] Safe areas/system bars respected.
- [ ] No state communicated through color alone.
- [ ] Roads, signals, vehicles, routes, destinations, and conflict cues remain visible.
- [ ] Relevant loading, disabled, error, pause, success, and failure states defined.
- [ ] Motion is useful, short, skippable, and reduced-motion aware.
- [ ] Essential audio has visual equivalents.
- [ ] Responsive layouts tested at supported aspect ratios.
- [ ] Strings externalized; no text overflow.
- [ ] No unapproved monetization, fake currency, or manipulative prompt.
- [ ] Font/icon/texture/illustration/audio rights recorded.
- [ ] Design reference/version and reviewer decision recorded.
- [ ] Actual-device review completed; mockup alone is not release evidence.

## 16. Decisions

### Approved (25 Oct 2026)
- Working title: Signal Shift: Tiny City (trademark and package-ID check pending).
- Audience: general casual players, not child-directed.
- Languages and markets: English first; India as test market.
- Orientation: portrait-first, pending UX testing.
- Signal model: binary only in v1.
- Undo: not in v1.
- Monetization: none in v1; revisit after validation.
- Device class: mid-range Android (about 4 GB RAM), to be confirmed by profiling.

### Still open
Do not silently decide: final logo and package ID; age rating; launch regions beyond the test market; final palette, font, and icon family; dark-mode requirement; scoring formula; 3D map vs grid/list; performance budget.

**Approval gate:** Phase 1 UI production begins after the open decisions above that affect layout and gameplay controls are approved (scoring formula and 3D map vs grid/list). Until then, use this as a proposal and label mockups accordingly.
