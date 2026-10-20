# AI Agent Playbook

## Contract
Read README and relevant docs. Work only on assigned task ID. Do not expand scope or begin the next phase. Ask David when requirements conflict, design/decision is missing, credentials are needed, licensing is unclear or acceptance cannot be met.

## Token-efficient loop
1. Read README, task and only relevant docs/files.
2. Before edits report assumptions, files, dependencies, risks and verification.
3. Implement one small slice; avoid broad refactors.
4. Run targeted tests then broader checks; never invent output.
5. Review diff for scope creep, secrets, licenses, broken references and debug code.
6. Report files, exact commands/results, limitations and next proposed task.
7. Stop for explicit approval at every phase gate.

## Required report
\`\`\`text
Task ID:
Summary:
Files changed:
Design/architecture references:
Tests/commands run:
Results (pass/fail/not run):
Device/build evidence:
Known issues/risks:
New dependencies/assets/licenses:
Acceptance criteria satisfied:
Next task proposed (not started):
Approval required:
\`\`\`

## Task prompt
> Implement only [TASK-ID and acceptance criteria] for Signal Shift: Tiny City. Read README and relevant docs. Before editing, state assumptions, files, dependencies, risks and verification. Follow approved Stitch designs/interfaces. Keep code focused, typed and testable; add/update tests. Check compatibility, maintenance, privacy, licensing and performance before dependencies. Never commit secrets or unlicensed assets.
>
> After editing, run available verification and report exact commands/results; mark checks not run. Do not claim device/build/Play success without evidence. Update checklists only when acceptance criteria have evidence. Stop at phase gate.

## Ownership
Gameplay: simulation/gameplay/tests. Content: level data/validator. UX: approved UI scenes. Art: assets/pipeline, no rule changes. Audio: audio/settings. QA: tests/reports, no silent rule changes. Release: build/store docs; no secrets. Parallel work only after interfaces/file ownership agreed.

## Rules
No monolithic scripts/god objects; deterministic simulation separate from rendering; stable IDs and one canonical level format; never disable tests to pass CI; mock assets marked development-only; small diffs; record licenses; no unapproved analytics/permissions/network/SDKs; never commit keys, keystores, passwords, personal data or credentials.

## Definition of done
Acceptance evidenced, tests added/updated, unrelated changes absent, docs updated for interface changes, limitations listed, human approval requested at gates. If a task depends on unapproved design/decision, stop and ask.
