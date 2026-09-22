# Prompt Library — مكتبة Prompts

Use the workflow-specific prompts first. These are reusable building blocks.

For substantial tasks, place this once at the start of the task contract:

```text
Act as a professional senior full-stack developer and software engineer with the judgment expected from 15+ years of relevant experience and deep expertise in this domain.

Work from the repository and authoritative project evidence. Think end to end, remain within approved scope, distinguish facts from assumptions, surface conflicts, and prove conclusions through actual verification.
```

The role statement sets the expected standard; it never substitutes for repository inspection, domain evidence, or tests.

---

## Pre-Code Repository Investigation + Documentation Audit

For substantial, risky, cross-cutting, or documentation-sensitive work, use the dedicated copy-ready prompt:

[`INVESTIGATION_PROMPT.md`](INVESTIGATION_PROMPT.md)

It requires evidence-based discovery without forcing a repository-wide Markdown read for every task, and it prevents unsafe automatic deletion or silent business-rule decisions.

---

## Investigation Only

```text
INVESTIGATE ONLY. Do not modify code yet.

Inspect the actual code, data flow, tests, and relevant documentation.

Report:
- root cause or best-supported explanation;
- evidence;
- blast radius;
- invariants that must be preserved;
- risks;
- smallest correct scope;
- unresolved uncertainties.

Distinguish facts from assumptions.
Stop if required behavior cannot be determined safely.
```

## Implement

```text
IMPLEMENT the confirmed change.

Fix the root cause or satisfy the approved requirement.
Preserve unrelated working behavior.
Keep scope limited to what is justified.
Follow existing project patterns where appropriate.
Do not invent business rules.
Add/update relevant regression or feature coverage.
Then run the relevant verification and report actual evidence.
```

## Verify

```text
VERIFY with actual execution.

Report:
- commands/checks run;
- pass/fail results;
- relevant test counts/output excerpts;
- regression/acceptance evidence;
- skips, mocks, warnings, or checks not run;
- remaining risks or unverified assumptions.

For user-facing or end-to-end behavior, use the project's designated non-production test user on localhost when feasible and authorized. Verify the real flow in the browser against the local application and safe test data; do not use a real customer or production credentials. Record the route, role/test identity, actions, observed result, and retained evidence. If this cannot be done, state why and do not imply it was done.

Check authoritative documentation after verification. Update the active handoff for ongoing work and durable CURRENT_STATE/related docs only when their recorded state materially changed. Resolve evidence conflicts or stop and surface them.

Never claim a check passed if it was not run.
```

## Code Review

```text
REVIEW this change critically, point by point:

1. Correctness
2. Business-rule accuracy
3. Architecture/responsibility boundaries
4. Data integrity
5. Security and authorization
6. Backward compatibility
7. Error/partial-failure handling
8. Edge cases
9. Test quality and regression protection
10. Maintainability/complexity
11. Observability where material
12. Unintended scope or behavior changes

Support findings with code evidence.
Do not answer only "looks good".
```

## Final Completion Check

```text
FINAL COMPLETION CHECK.

Before calling this done, state with evidence:
1. Which acceptance criteria are satisfied.
2. What was actually tested/verified.
3. What relevant edge cases were handled.
4. Whether unrelated behavior changed.
5. Any assumption not verified against code/data.
6. Any migration, security, documentation, or operational follow-up still required.
7. Any remaining known risk.

If something is not complete, say so explicitly.
```
