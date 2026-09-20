# Testing Guide — دليل الاختبار

## Principle | المبدأ

Test the behavior and risk that changed. Do not run a huge suite blindly when a targeted test is enough, and do not run only a tiny test when the blast radius is broad.

## Suggested Order

1. **Reproduce/characterize** the original behavior when fixing a bug.
2. **Targeted tests** for the changed unit/component/service.
3. **Integration tests** when boundaries changed.
4. **E2E/user-flow tests** when end-user workflow changed.
5. **Broader regression suite** when shared/core behavior changed.
6. **Static checks**: typecheck/lint/build where applicable.
7. **Production-like verification** for migrations, deployment, configuration, or external integrations where material.

## Real User Verification on Localhost | تحقق فعلي كمستخدم

When a change affects a user-visible screen, workflow, permission, integration boundary, or end-to-end outcome, automated tests alone may not prove that the assembled system works.

When feasible and authorized:

1. Start the actual application locally using the project's documented setup.
2. Use the project's designated **non-production test user** with the relevant role and safe test data.
3. Execute the changed flow through the real browser UI on localhost, including the material happy path and risk-relevant failure/permission states.
4. Confirm relevant persistence or side effects through the UI, API, database, logs, or another authoritative surface as appropriate.
5. Record the URL/route, test role or test-user identifier, steps, observed result, date/environment, and concise retained evidence.

Never use a real customer's account, production credentials, or production mutations merely to satisfy this check. Never create undocumented shared credentials. Prefer reproducible seeded or isolated test users defined by the project.

Localhost verification is required when it is the relevant acceptance evidence and the environment is available. It is not ritualistically required for documentation-only changes, pure libraries with no user flow, or changes whose risk is fully covered at a lower layer. If it is required but blocked, report the blocker and do not claim complete end-to-end verification.

A manual localhost pass complements automated regression coverage; it does not replace it.

## Evidence Record | سجل الدليل

For each material acceptance criterion, capture:

| Field | Record |
|---|---|
| Claim | What is being proven |
| Source | Test, browser, log, query, diff, or runtime surface |
| Execution | Exact command or manual steps |
| Environment | Local/test/staging and relevant identity/role |
| Result | Pass/fail plus concise observed output |
| Limits | Skips, mocks, warnings, blockers, or unverified assumptions |

Evidence must be attributable to the current code/ref and relevant environment. Stale screenshots, an old CI run, documentation text, or an agent's confidence cannot prove the current result.

## Test Integrity — نزاهة الاختبارات

Never:
- delete a failing test just to make CI green;
- weaken an assertion without a justified behavior change;
- change fixtures so the bug disappears artificially;
- replace necessary real verification with mocks that hide the failure;
- mark tests skipped and then claim completion.

## What to Ask the Agent

```text
For every relevant check, tell me:
- what you ran;
- why it is relevant;
- whether it passed;
- what failed/skipped;
- what was not possible to run;
- whether the changed user flow was exercised with the designated test user on localhost, when relevant;
- which evidence maps to each material acceptance criterion.

Do not paste massive logs unless needed; include enough output to prove the result.
```

## Edge Cases

Consider only those relevant to the domain, for example:
- missing/null;
- zero/negative;
- min/max boundary;
- duplicate request;
- retry;
- partial failure;
- concurrent update;
- stale state;
- authorization mismatch;
- unexpected external response;
- unit/currency/timezone mismatch.
