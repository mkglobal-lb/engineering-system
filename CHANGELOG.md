# Changelog

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
