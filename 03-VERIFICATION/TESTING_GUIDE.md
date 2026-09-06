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
- what was not possible to run.

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
