# Refactor Workflow — مسار Refactor

## Rule | القاعدة

**Refactor = improve internal structure without intentionally changing externally observable behavior.**

## 1. Establish Baseline

Before changing:
- What behavior must remain identical?
- What tests prove it?
- What is the specific maintainability/problem being improved?
- What is explicitly out of scope?

## 2. Prompt

```text
REFACTOR SAFELY.

Objective:
[why the refactor is needed]

Behavior that must remain unchanged:
[list]

First inspect the code and identify:
1. The structural problem.
2. The smallest refactor that improves it.
3. Existing tests that protect behavior.
4. Missing characterization/regression tests needed before refactoring.
5. Risks of changing shared abstractions or public contracts.

Then implement only the justified refactor.
Do not mix unrelated feature changes or behavior changes into this work.
Run relevant tests before and after, and report evidence.
```

## 3. Stop

Stop if the refactor requires changing business behavior. That becomes a separate feature/bug decision.
