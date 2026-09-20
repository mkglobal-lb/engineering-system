# Definition of Done — متى نعتبر المهمة منتهية؟

A task is done when the **relevant** items below are satisfied.

- [ ] Requirement / acceptance criteria satisfied.
- [ ] Root cause addressed for bug work.
- [ ] Unrelated working behavior preserved.
- [ ] Business rules were not invented.
- [ ] Relevant tests/checks actually run.
- [ ] Changed user-facing/end-to-end flow verified on localhost with the designated non-production test user when relevant and feasible, or the blocker is explicit.
- [ ] Material acceptance criteria mapped to attributable evidence from the current code/ref and environment.
- [ ] Original failure has regression protection where appropriate.
- [ ] Relevant edge/failure cases handled.
- [ ] Security/authorization reviewed when relevant.
- [ ] Data integrity/migration verified when relevant.
- [ ] Build/type/static checks run where appropriate.
- [ ] No unexplained failures or skipped critical checks.
- [ ] Diff reviewed for unintended scope.
- [ ] Remaining assumptions/risks are explicit.
- [ ] Active handoff updated when work remains in progress or spans sessions.
- [ ] Durable CURRENT_STATE/related documentation updated when durable recorded state materially changed—not as a session diary.
- [ ] Conflicts among requirements, code, tests, data, runtime evidence, and documentation resolved or explicitly blocked/escalated.
- [ ] Durable documentation/ADR updated only if actually needed.

## Final Prompt

```text
Before marking this done, confirm the relevant Definition of Done items with evidence.
For any item that is not applicable, give a short reason.
If any material item is incomplete, do not call the task done.
```
