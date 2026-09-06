# UI/UX Workflow — مسار UI/UX

## Goal | الهدف

تحسين usability وclarity بدون كسر business logic أو تحويل UI redesign إلى backend rewrite بلا سبب.

## 1. Audit First

```text
AUDIT THIS UI/UX BEFORE CHANGING IT.

Evaluate:
1. User goal and primary task.
2. Information hierarchy.
3. Navigation and flow.
4. Clarity of labels, states, actions, and feedback.
5. Error, empty, loading, success, and permission states.
6. Accessibility and keyboard/focus behavior where relevant.
7. Mobile/responsive behavior where relevant.
8. Consistency with the existing product design system/patterns.
9. Data shown: whether it is authoritative, stale, duplicated, misleading, or fake-defaulted.
10. Friction, unnecessary steps, and dangerous actions.

Separate:
- UX problems,
- visual/design problems,
- data/business-rule problems,
- implementation bugs.

Recommend the smallest coherent improvement scope. Do not implement yet.
```

## 2. Implement

```text
IMPLEMENT the approved UI/UX improvements.

Preserve business behavior unless the requirement explicitly changes it.
Do not invent new data or business rules to make the screen look complete.
Reuse existing components/design patterns where they are fit for purpose.
Make destructive or irreversible actions explicit and safe.
Handle loading, empty, error, disabled, and success states where relevant.

Verify the actual user flow after implementation.
```

## 3. Verify

- Primary user task can be completed.
- No regression in affected actions.
- Responsive behavior checked if relevant.
- Focus/keyboard checked for interactive forms where relevant.
- No fake/default data masking missing backend state.
- Error and empty states are clear.
