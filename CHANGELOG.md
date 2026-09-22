# Changelog

## v1.4.0 — 2026-09-22

- Added a risk-scaled pre-code repository investigation and documentation-audit workflow.
- Added a copy-ready Code Agent investigation prompt for substantial/risky work.
- Added cross-project documentation standards covering authority, lifecycle, CURRENT_STATE, handoffs, temporary prompts, consolidation, archival, and deletion.
- Explicitly rejected age-based document deletion and repository-wide Markdown reading as mandatory defaults.
- Clarified that documentation fixes must not silently decide business rules, finance semantics, security boundaries, API contracts, migrations, or architecture ownership.
- Clarified that CURRENT_STATE and HANDOFF artifacts are updated/created only when their durable purpose is justified, not automatically for every session.
- Clarified the lifecycle of large Claude/task input files and distinguished temporary working prompts from authoritative project documentation.
- Linked the new workflow and prompt from Start Here and the Prompt Library.

## v1.3.0 — 2026-09-20

- Added a reusable professional operating posture for substantial Code Agent work: senior full-stack/software-engineering judgment associated with 15+ years of relevant experience and deep domain expertise.
- Clarified that role and experience language sets an expectation but never proves correctness.
- Added evidence records that map material claims and acceptance criteria to current, attributable verification.
- Added real user-flow verification on localhost with designated non-production test users when relevant, feasible, and authorized.
- Prohibited using real customers, production credentials, production mutations, or undocumented shared credentials for localhost verification.
- Required active handoff updates for ongoing multi-session work and durable CURRENT_STATE/documentation updates only when durable state materially changes.
- Added explicit conflict-resolution and escalation rules across requirements, code, tests, data, runtime evidence, and documentation.

## v1.2.0 — 2026-09-19

- Added a general long-running Code Agent workflow for safe continuation across sessions/context windows.
- Defined the separation between AI session lifecycle, Git branch lifecycle, pull-request lifecycle, and feature completion.
- Established repository-backed handoffs and Git history as durable continuity, with chat treated as temporary context.
- Added evidence-based checkpoint, Draft PR, fresh-session resume, and source-of-truth rules.
- Clarified that this playbook is canonical for cross-project engineering process while each project repository remains authoritative for project-specific state.
- Added CHECKPOINT and RESUME Agent commands and linked the workflow from Start Here, Code Agent guidance, and Git/delivery guidance.
- Based the workflow on published guidance from Anthropic, OpenAI, and GitHub.

## v1.1.0 — 2026-09-19

- Added a risk-scaled architecture plan review and execution handoff workflow.
- Defined responsibilities for the owner, Claude Code, ChatGPT, Codex, and verification.
- Added copy-ready prompts for architecture drafting, independent review, finalization, and phase execution.
- Added an approved worker-order template, explicit lifecycle states, stop conditions, and plan change control.
- Clarified that GitHub is the source of truth for approved plans and that project-specific worker orders stay in their project repositories.

## v1.0.0 — 2026-09-06

Initial release.

- Central personal/professional engineering reference.
- No project integration or project dependency.
- Added Start Here routing.
- Added workflows for bugs, features, UI/UX, refactoring, database migrations, security, incidents, and releases.
- Added Code Agent command vocabulary and prompt library.
- Added testing, code review, and Definition of Done.
- Added engineering principles, architecture, security/data, and Git/delivery guidance.
- Added engineering lexicon, ADR guidance, and knowledge inbox.
- Bilingual Arabic/English usage model.
