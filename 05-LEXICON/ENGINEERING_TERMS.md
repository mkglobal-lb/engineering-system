# Engineering Lexicon — قاموس المصطلحات

Use this file as your growing vocabulary. Add terms only when useful.

---

## Root Cause — السبب الجذري

**Meaning:** The underlying condition that produces the failure.  
**Use:** "Identify and fix the root cause, not only the visible symptom."

---

## Source of Truth — المصدر المعتمد

**Meaning:** The authoritative source from which a fact/rule should be derived.  
**Use:** "What is the source of truth for this business rule?"

---

## Blast Radius — نطاق التأثير

**Meaning:** Systems, users, data, flows, or components that may be affected by a change/failure.  
**Use:** "Assess the blast radius before implementation."

---

## Invariant — شرط يجب أن يبقى صحيحاً

**Meaning:** A condition that must always remain true.  
**Use:** "Identify the invariants this change must preserve."

---

## Regression — انتكاسة

**Meaning:** Previously working behavior breaks after a change.  
**Use:** "Add regression coverage for the original failure."

---

## Backward Compatibility — التوافق مع القديم

**Meaning:** Existing consumers/data/workflows continue to work after a change.  
**Use:** "Assess backward-compatibility impact."

---

## Idempotency — تكرار آمن

**Meaning:** Repeating the same operation does not create unintended additional effects.  
**Use:** Important for retries, payments, webhooks, jobs, APIs.

---

## Race Condition — مشكلة تزامن

**Meaning:** Result depends on timing/order of concurrent operations.  
**Use:** "Could concurrent updates produce a race condition?"

---

## Atomicity — الذرّية

**Meaning:** A multi-step operation succeeds as a unit or safely fails without partial inconsistent state.

---

## Rollback — رجوع

**Meaning:** Return code/config/schema to a previous safe state.

---

## Recovery — تعافي

**Meaning:** Restore correct service/data state after failure; may not mean reverting code.

---

## Migration — انتقال من حالة إلى أخرى

**Meaning:** Controlled change to schema/data/configuration/contracts.

---

## Observability — قابلية فهم ما يحدث في الإنتاج

**Meaning:** Ability to infer system behavior/failure from logs, metrics, traces, and events.

---

## Technical Debt — دين تقني

**Meaning:** A deliberate or accumulated trade-off that increases future engineering cost/risk.

---

## Coupling — ترابط

**Meaning:** Degree to which one component depends on another.

---

## Cohesion — تماسك

**Meaning:** How strongly related the responsibilities inside a component are.

---

## Contract — عقد تقني

**Meaning:** Expectations between components/users: API shape, events, validation, side effects, guarantees.

---

## Fail Closed / Fail Open

**Fail closed:** failure denies/blocks access or action.  
**Fail open:** failure permits it.  
Security-sensitive paths usually require deliberate fail-closed behavior.

---

## Reconciliation — مطابقة

**Meaning:** Compare records/sources to a canonical source and explain discrepancies.

---

## Characterization Test

**Meaning:** A test that records existing behavior before refactoring/repair when behavior is not already well specified.

---

## Acceptance Criteria — معايير القبول

**Meaning:** Observable conditions proving the requested outcome is complete.
