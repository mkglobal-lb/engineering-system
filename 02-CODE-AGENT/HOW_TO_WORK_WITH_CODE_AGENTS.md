# How to Work With Code Agents — كيف تتعامل مع Code Agents

## Core Rule | القاعدة

Treat the agent as an engineering executor/reviewer, not an unquestioned authority.

تعامل مع الـ agent كمهندس ينفذ ويحلل، وليس كمصدر حقيقة نهائي.

## Good Task Contract | عقد المهمة الجيد

For non-trivial tasks, provide as many of these as are known:

1. **Objective** — what outcome is required.
2. **Source of truth** — business rule, code, schema, doc, API contract, production evidence.
3. **Current behavior** — what happens now.
4. **Expected behavior** — what should happen.
5. **Scope** — what is included.
6. **Out of scope** — what should not be changed.
7. **Risk level** — R0/R1/R2/R3.
8. **Invariants** — conditions that must remain true.
9. **Acceptance criteria** — measurable completion conditions.
10. **Verification** — what must be run/checked.
11. **Stop conditions** — when the agent must surface uncertainty instead of guessing.

You do not need all 11 for a typo. Use judgment.

## Evidence Discipline | انضباط الدليل

Ask for:
- files inspected/changed;
- actual commands run;
- actual pass/fail result;
- relevant test counts/output excerpts;
- diff summary;
- unverified assumptions;
- limits of investigation.

Do not require giant logs when a concise result is enough.

## Do Not Let the Agent

- invent business rules;
- change scope silently;
- delete/weaken tests to get green CI;
- hide missing data with fake defaults;
- treat compilation as complete verification;
- claim tests were run when they were not;
- mix unrelated refactors into a focused fix;
- make destructive changes without surfacing them.
