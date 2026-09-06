# Bug Workflow — مسار إصلاح Bug

## 1. Capture | وصف المشكلة

اكتب فقط:
- Where | أين تظهر؟
- Expected | ماذا يجب أن يحدث؟
- Actual | ماذا يحدث فعلياً؟
- Reproduction | كيف نعيدها؟
- Evidence | screenshot/log/error إن وجد.
- Impact | ما أثرها؟
- Unknowns | ما الذي لا تعرفه؟

## 2. Investigate | التحقيق

انسخ:

```text
INVESTIGATE ONLY. Do not modify code yet.

Bug:
[describe the bug]

Expected behavior:
[expected]

Actual behavior:
[actual]

Reproduction:
[steps, if known]

Investigate the actual codebase and report:
1. The confirmed or best-supported root cause.
2. The affected code/data flow.
3. The blast radius: other known or likely flows that may share the same cause.
4. Existing behavior and invariants that must be preserved.
5. Security, data, financial, permission, or backward-compatibility risks.
6. The smallest correct scope of change.
7. What you inspected and any limits to the investigation.

Do not guess. Distinguish evidence from assumptions.
Stop if the source of truth or required behavior is materially unclear.
```

## 3. Decide | القرار

إذا R0/R1 والسبب واضح والحل مباشر: يمكن المتابعة.

إذا R2/R3، أو يوجد destructive/data/security risk: راجع approach قبل التنفيذ.

اسأل:
- هل هذا root-cause fix أم workaround؟
- هل يوجد حل أبسط؟
- ماذا يمكن أن ينكسر؟
- هل نحتاج migration/rollback؟
- هل acceptance criteria واضحة؟

## 4. Implement | التنفيذ

```text
IMPLEMENT the confirmed fix.

Use the investigation findings as the source of truth.

Requirements:
- fix the root cause, not only the visible symptom;
- preserve unrelated working behavior;
- keep the change within the justified scope;
- follow existing project patterns unless there is a clear reason not to;
- add or update regression coverage for the original failure;
- do not weaken validation or tests to make the change pass;
- do not silently change business rules.

After implementation, run the relevant verification and report actual evidence.
```

## 5. Verify | التحقق

```text
VERIFY the fix with actual execution.

Report:
1. How the original failure was reproduced or traced.
2. The regression test or equivalent evidence proving the bug is fixed.
3. Commands/checks actually run.
4. Pass/fail results and relevant counts.
5. Any failures, skips, mocks, warnings, or checks not run.
6. Files changed and why.
7. Any remaining risk or assumption.

Never claim a check passed if it was not run.
```

## 6. Review + Close

Use:
- [`../03-VERIFICATION/CODE_REVIEW.md`](../03-VERIFICATION/CODE_REVIEW.md)
- [`../03-VERIFICATION/DEFINITION_OF_DONE.md`](../03-VERIFICATION/DEFINITION_OF_DONE.md)

**Done = evidence, not confidence.**
