# Definition of Done — متى نعتبر المهمة منتهية؟

A task is done when the **relevant** items below are satisfied.

- [ ] Requirement / acceptance criteria satisfied.
- [ ] Root cause addressed for bug work.
- [ ] Unrelated working behavior preserved.
- [ ] Business rules were not invented.
- [ ] Relevant tests/checks actually run.
- [ ] Original failure has regression protection where appropriate.
- [ ] Relevant edge/failure cases handled.
- [ ] Security/authorization reviewed when relevant.
- [ ] Data integrity/migration verified when relevant.
- [ ] Build/type/static checks run where appropriate.
- [ ] No unexplained failures or skipped critical checks.
- [ ] Diff reviewed for unintended scope.
- [ ] Remaining assumptions/risks are explicit.
- [ ] Durable documentation/ADR updated only if actually needed.

## Final Prompt

```text
Before marking this done, confirm the relevant Definition of Done items with evidence.
For any item that is not applicable, give a short reason.
If any material item is incomplete, do not call the task done.
```
