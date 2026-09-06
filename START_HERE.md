# Start Here — ابدأ من هنا

هذا هو الملف الوحيد الذي تحتاج أن تبدأ منه.

Choose what you are doing:

| I need to... | افتح |
|---|---|
| Fix a bug / أصلّح Bug | [`01-WORKFLOWS/BUG_WORKFLOW.md`](01-WORKFLOWS/BUG_WORKFLOW.md) |
| Build a feature / أبني Feature | [`01-WORKFLOWS/FEATURE_WORKFLOW.md`](01-WORKFLOWS/FEATURE_WORKFLOW.md) |
| Improve UI/UX | [`01-WORKFLOWS/UI_UX_WORKFLOW.md`](01-WORKFLOWS/UI_UX_WORKFLOW.md) |
| Refactor safely / Refactor بدون تغيير behavior | [`01-WORKFLOWS/REFACTOR_WORKFLOW.md`](01-WORKFLOWS/REFACTOR_WORKFLOW.md) |
| Change database/schema/data | [`01-WORKFLOWS/DATABASE_MIGRATION_WORKFLOW.md`](01-WORKFLOWS/DATABASE_MIGRATION_WORKFLOW.md) |
| Handle a security concern | [`01-WORKFLOWS/SECURITY_WORKFLOW.md`](01-WORKFLOWS/SECURITY_WORKFLOW.md) |
| Handle a production incident | [`01-WORKFLOWS/INCIDENT_WORKFLOW.md`](01-WORKFLOWS/INCIDENT_WORKFLOW.md) |
| Release/deploy | [`01-WORKFLOWS/RELEASE_WORKFLOW.md`](01-WORKFLOWS/RELEASE_WORKFLOW.md) |
| Know what to say to a Code Agent | [`02-CODE-AGENT/PROMPT_LIBRARY.md`](02-CODE-AGENT/PROMPT_LIBRARY.md) |
| Learn the agent command vocabulary | [`02-CODE-AGENT/AGENT_COMMANDS.md`](02-CODE-AGENT/AGENT_COMMANDS.md) |
| Test correctly | [`03-VERIFICATION/TESTING_GUIDE.md`](03-VERIFICATION/TESTING_GUIDE.md) |
| Review a change | [`03-VERIFICATION/CODE_REVIEW.md`](03-VERIFICATION/CODE_REVIEW.md) |
| Decide whether work is truly done | [`03-VERIFICATION/DEFINITION_OF_DONE.md`](03-VERIFICATION/DEFINITION_OF_DONE.md) |
| Review engineering principles | [`04-ENGINEERING/ENGINEERING_PRINCIPLES.md`](04-ENGINEERING/ENGINEERING_PRINCIPLES.md) |
| Understand architecture/design | [`04-ENGINEERING/ARCHITECTURE_AND_DESIGN.md`](04-ENGINEERING/ARCHITECTURE_AND_DESIGN.md) |
| Review security/data principles | [`04-ENGINEERING/SECURITY_AND_DATA.md`](04-ENGINEERING/SECURITY_AND_DATA.md) |
| Review Git/delivery habits | [`04-ENGINEERING/GIT_AND_DELIVERY.md`](04-ENGINEERING/GIT_AND_DELIVERY.md) |
| Understand a term like root cause/invariant/idempotency | [`05-LEXICON/ENGINEERING_TERMS.md`](05-LEXICON/ENGINEERING_TERMS.md) |
| Make an important technical decision | [`06-DECISIONS/ENGINEERING_DECISIONS_AND_ADRS.md`](06-DECISIONS/ENGINEERING_DECISIONS_AND_ADRS.md) |
| Save something new I learned | [`07-LEARNING/NEW_KNOWLEDGE_INBOX.md`](07-LEARNING/NEW_KNOWLEDGE_INBOX.md) |

---

# Risk Level — مستوى الخطورة

قبل أي تغيير، صنّفه بسرعة:

### R0 — Trivial
Documentation, typo, copy, safe visual spacing, non-functional cleanup.

**Flow:** `IMPLEMENT → VERIFY`

### R1 — Normal
Isolated bug, normal validation, ordinary UI behavior, small feature.

**Flow:** `INVESTIGATE → IMPLEMENT → VERIFY`

### R2 — High Risk
Finance, payments, auth/authz, customer balances, permissions, migrations, destructive operations, public API contract, sensitive data, cross-module behavior.

**Flow:** `INVESTIGATE → DECIDE → IMPLEMENT → VERIFY → REVIEW`

### R3 — Critical
Production incident, suspected corruption, security breach, major outage.

**Flow:** `CONTAIN → PRESERVE EVIDENCE → DIAGNOSE → RECOVER → FIX → VERIFY → POSTMORTEM`

---

# Stop Conditions — متى توقف الـ Agent

Tell the Code Agent to stop and surface the issue if:

- sources of truth conflict;
- required business behavior cannot be determined safely;
- the change could destroy or rewrite data unexpectedly;
- security/permission boundaries are unclear;
- migration safety cannot be established;
- existing tests contradict the requested behavior;
- verification cannot actually be performed;
- the requested fix requires materially expanding scope;
- real production/code evidence contradicts the assumptions.

لا تخليه يخترع قرار أو business rule ليكمل بسرعة.
