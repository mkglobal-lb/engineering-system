# Feature Workflow — مسار Feature جديدة

## 1. Define | عرّف المطلوب

قبل الكود:
- Business problem | ما المشكلة التي نحلها؟
- User | من المستخدم؟
- Desired outcome | ما النتيجة؟
- Source of truth | من أين تأتي الـ business rule؟
- Scope | ما داخل المطلوب؟
- Out of scope | ما ليس مطلوباً؟
- Acceptance criteria | كيف نعرف أنها نجحت؟
- Risk level | R0–R3.

## 2. Investigate Existing System

```text
PLAN THIS FEATURE BEFORE IMPLEMENTING.

Feature:
[describe]

Business rule / source of truth:
[describe or point to the authoritative source]

Acceptance criteria:
[list]

Inspect the existing codebase and report:
1. Existing components, services, APIs, data models, and patterns this feature should reuse.
2. The simplest design that satisfies the requirement without overengineering.
3. Required changes across data/backend/API/frontend/UI/tests, but only where actually needed.
4. Security, permission, data-integrity, financial, and backward-compatibility implications.
5. Edge cases and failure modes.
6. Scalability or operational risks that are material now.
7. What should explicitly remain out of scope.

Do not implement yet if the design or business rule is materially ambiguous.
```

## 3. Implement

```text
IMPLEMENT the approved feature scope.

Constraints:
- preserve existing working behavior unless change is explicitly required;
- reuse canonical data and existing patterns;
- avoid duplicated business logic;
- keep responsibilities in the correct layer;
- add appropriate tests for business-critical behavior;
- do not add speculative infrastructure for hypothetical future needs;
- update documentation only where the change creates a new durable rule or contract.

Then run relevant verification and report evidence.
```

## 4. Verify

Check:
- acceptance criteria;
- happy path;
- relevant edge cases;
- failure behavior;
- permissions;
- data integrity;
- regression around touched flows;
- build/type/static checks as appropriate.

Then use Definition of Done.
