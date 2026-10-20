# QA and Release Plan
**Status:** Proposal. No build or store submission is claimed complete.

## Principles
Use reproducible versioned builds. No known critical/high crash, data-loss, progression blocker or policy issue. Store creatives must represent actual gameplay. No secrets in repository history.

## Test layers
- **Unit:** signal transitions, conflicts, route connectivity, queue capacity, deterministic ordering, win/loss, score boundaries, save migrations and invalid data.
- **Integration:** load→act→simulate→result→persist→reload; pause/resume/restart and duplicate inputs.
- **Content:** validate every level plus human playtesting.
- **UI:** navigation, controls, settings persistence, dialogs, safe areas, touch targets, loading/error/disabled states, screenshot comparison.
- **Device:** choose exact matrix in Phase 2; include minimum-spec target, common mid-range phone and different viewport. Record device/OS/build/steps/results/evidence/defect ID.

## Regression checklist
- [ ] Fresh install/tutorial; all levels start/complete/retry.
- [ ] Stars/scores deterministic.
- [ ] Pause freezes; resume does not jump ahead.
- [ ] Background/foreground/process death preserves state.
- [ ] Progress/settings persist; corrupt save recovers.
- [ ] Offline first and repeat sessions work.
- [ ] Audio controls affect intended buses and persist.
- [ ] Touch/text work at supported aspect ratios/scaling.
- [ ] Low memory/storage/interruption handled.
- [ ] No debug menus, placeholders, test purchases, secrets or dev endpoints in release.
- [ ] Ads/billing (if included) handle unavailable/cancelled/pending/failure/restore/duplicate callbacks.
- [ ] Licenses, permissions, SDKs and disclosures audited.

## Performance
Set numeric startup/frame/memory/package/thermal budgets after device selection. Profile real hardware, not editor FPS. Record scene/device/duration/metrics. Optimize only with evidence and preserve readability.

## Store assets/policy
- [ ] Title/package ID/support contact approved.
- [ ] Icon/feature graphic meet current specs; screenshots/trailer use real build.
- [ ] Accurate descriptions/localization.
- [ ] Public privacy policy matches shipped SDKs.
- [ ] Content rating, target audience, ads declaration and Data safety accurate.
- [ ] Permissions minimized and justified.
- [ ] Asset/font/music/plugin/SDK licenses recorded.

## Signing and rollout
Pin engine/export templates/toolchain. Keep application ID stable after public release. Build signed AAB; never commit keystore/credentials. Securely back up signing material outside repo. Verify orientation/icons/manifest/permissions/version/signing/install. Complete internal/closed testing and account-specific requirements. Recheck current Play target API/testing requirements; obtain human sign-off. Roll out deliberately; verify listing/install/gameplay/save/audio after release. Monitor crashes/ANRs/reviews/support where lawful; maintain hotfix/rollback plan.

## Official references
- Play developer help: https://support.google.com/googleplay/android-developer/
- Target API: https://support.google.com/googleplay/android-developer/answer/11926878
- Testing: https://support.google.com/googleplay/android-developer/answer/14151465
- App Bundle: https://developer.android.com/guide/app-bundle
- Godot Android export: https://docs.godotengine.org/en/4.6/tutorials/export/exporting_for_android.html
