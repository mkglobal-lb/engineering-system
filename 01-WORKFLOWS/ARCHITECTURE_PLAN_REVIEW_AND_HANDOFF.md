# Architecture Plan Review & Execution Handoff

## مراجعة الخطة المعمارية وتسليمها للتنفيذ

Use this workflow when a change needs deliberate architecture or cross-layer planning before implementation.

استخدم هذا المسار عندما يكون التغيير معماريًا، متعدد الوحدات، أو عالي الخطورة ويحتاج plan معتمدة قبل كتابة الكود.

Typical cases:
- R2 work: Finance, payments, authorization, migrations, sensitive data, or public contracts;
- cross-module or multi-repository changes;
- a large feature split into controlled phases;
- a proposed change to an existing approved plan.

Do not force this workflow on R0 work or every normal R1 task. The existing risk routing still applies.

---

## 1. Operating Model | توزيع المسؤوليات

This is the current tool assignment, not a universal claim that one model is always superior:

| Role | Current owner | Authority |
|---|---|---|
| Business owner | User / accountable owner | Approves business scope, priorities, and unresolved trade-offs |
| Architecture investigator and final plan owner | Claude Code | Inspects the project and produces the final implementation plan |
| Independent reviewer | ChatGPT | Challenges the draft and provides evidence-based recommendations |
| Implementation agent | Codex | Implements one approved phase at a time |
| Verification | Codex plus independent review where risk requires | Produces evidence that acceptance criteria are satisfied |

The responsibility boundaries remain valid even if the tools change later.

---

## 2. Source of Truth | مصدر الحقيقة

Separate desired behavior from current-system facts:

- Approved business requirements and accepted decisions define the intended behavior.
- Source code, schema, tests, configuration, and runtime evidence define the current implementation.
- An approved plan defines the authorized implementation scope.
- Chat responses and recommendations are advisory until incorporated into the final approved plan.

If these sources conflict, stop and surface the conflict. Do not silently choose one.

The approved worker order is fixed for execution, but it is not allowed to override contrary code, data, security, or production evidence. A material contradiction returns the work to planning.

GitHub is the source of truth for approved plans and worker orders. Chat or Notion may help discussion or visibility, but must not become a competing execution authority.

Project-specific plans belong in the actual project repository, using that project's established documentation location. Do not store project-specific worker orders in this central playbook.

---

## 3. Lifecycle | دورة الخطة

`DRAFT → INDEPENDENT REVIEW → FINALIZATION → APPROVED → IMPLEMENTING → VERIFIED → CLOSED`

Use `BLOCKED` whenever a stop condition prevents safe progress.

### Status meanings

- **DRAFT:** Open for architecture discussion. Not authorized for implementation.
- **INDEPENDENT REVIEW:** Being challenged for gaps, conflicts, and trade-offs.
- **FINALIZATION:** Review findings are being accepted, rejected, or resolved with evidence.
- **APPROVED:** Scope and decisions are frozen for the named phase.
- **IMPLEMENTING:** Codex is executing the approved phase.
- **VERIFIED:** Acceptance criteria have evidence.
- **CLOSED:** Review and documentation are complete.
- **BLOCKED:** Work stopped because a required decision, authority, dependency, or safe verification is missing.

Only the accountable owner may approve business scope. A plan author may finalize technical details that are already inside that scope.

---

## 4. Step 1 — Claude Code Architecture Draft

Claude Code must inspect the actual project before proposing architecture. The draft must distinguish confirmed facts, assumptions, and unresolved decisions.

### Draft prompt

```text
ARCHITECTURE INVESTIGATION AND DRAFT PLAN ONLY.
Do not modify code.

Objective:
[Describe the business and engineering outcome.]

Authoritative business rules / decisions:
[List or link the approved sources.]

Current proposal or previous plan:
[Paste or link it.]

Proposed changes:
[List each proposed change explicitly.]

Inspect the actual codebase, schema, APIs, UI flows, tests, configuration,
documentation, and relevant Git history.

Produce:
1. Current system facts with file/code evidence.
2. Current problems and root causes.
3. Architecture fit and responsibility boundaries.
4. Impacted data model, backend, API, frontend/UI, permissions, audit,
   finance/data integrity, migration, deployment, and rollback areas,
   but only where relevant.
5. Existing patterns to reuse and duplicated authority to avoid.
6. Alternatives considered and material trade-offs.
7. Risks, edge cases, compatibility concerns, and 10x-scale implications
   that are material rather than hypothetical.
8. Recommended target design.
9. Implementation phases, dependencies, and safe ordering.
10. Acceptance criteria and verification strategy per phase.
11. Explicit in-scope and out-of-scope items.
12. Confirmed facts, assumptions, open decisions, and blockers.

Do not implement.
Do not invent business rules.
Stop if the intended behavior cannot be determined safely.
```

---

## 5. Step 2 — ChatGPT Independent Review

Give ChatGPT the complete draft, proposed changes, and any necessary project evidence. The reviewer challenges the plan; it does not approve or rewrite it as if it were the plan owner.

### Independent review prompt

```text
INDEPENDENT ARCHITECTURE REVIEW ONLY.
Do not implement code and do not treat the plan as approved.

We have the following proposed changes to the previous plan:

[LIST THE PROPOSED CHANGES CLEARLY]

Previous plan:
[ATTACH OR LINK THE COMPLETE PREVIOUS PLAN]

Claude Code architecture draft:
[ATTACH OR LINK THE COMPLETE DRAFT]

Authoritative business rules and accepted decisions:
[LIST OR LINK THEM]

Review the proposal against the actual current project structure.

If repository access is available, inspect the relevant code, schema, APIs,
UI flows, tests, configuration, documentation, and Git history.
If repository access is unavailable, explicitly label code-level compatibility
as unverified and do not claim that the plan fits the codebase.

Answer point by point:

1. Does the proposal fit the current architecture and responsibility boundaries?
2. Which files, modules, data models, APIs, UI flows, permissions, tests,
   migrations, deployment steps, or operational processes are affected?
3. What are the advantages compared with the previous plan?
4. What are the disadvantages, new complexity, and long-term maintenance costs?
5. Are there conflicts with existing conventions, accepted decisions,
   business rules, sources of truth, or working behavior?
6. Does the plan create duplicated authority, hidden coupling, unsafe data
   transitions, finance/audit risk, security gaps, or compatibility problems?
7. Which assumptions are unsupported or require evidence?
8. Are the phases ordered safely and independently verifiable?
9. What must change before approval?
10. What is your final recommendation: accept, accept with required changes,
    or reject?

For every material finding provide:
- severity;
- evidence;
- impact;
- required correction.

Separate confirmed facts, assumptions, risks, and recommendations.
Do not expand scope merely to apply generic best practices.
Do not rewrite the final plan.
```

---

## 6. Step 3 — Claude Code Finalization

Return the independent review to Claude Code. Claude Code must evaluate every material finding rather than accepting it automatically.

### Finalization prompt

```text
FINALIZE THE ARCHITECTURE PLAN.
Do not implement code.

Inputs:
- previous plan;
- proposed changes;
- your architecture draft;
- the independent review;
- authoritative business decisions;
- actual project evidence.

For every material review finding, record:
- ACCEPTED, PARTIALLY ACCEPTED, REJECTED, or NEEDS OWNER DECISION;
- evidence and rationale;
- exact change to the plan, if any.

Then produce one internally consistent final plan:
1. objective and business outcome;
2. current system facts and root causes;
3. final architecture and ownership boundaries;
4. invariants and sources of truth;
5. in scope and out of scope;
6. impacted layers and contracts;
7. data/migration/backward-compatibility strategy;
8. permissions, audit, failure, and recovery behavior;
9. phased implementation order and dependencies;
10. acceptance criteria and verification per phase;
11. deployment/rollback requirements where relevant;
12. remaining assumptions, risks, blockers, and owner decisions.

Remove superseded alternatives and contradictory instructions.
Do not hide unresolved decisions inside implementation steps.
Do not mark a phase APPROVED until its business scope and material technical
decisions are resolved.
```

---

## 7. Step 4 — Approval and Phase Split

After owner approval, split the final plan into independently executable phase files inside the project repository.

Rules:
- one phase file = one coherent worker order;
- state dependencies explicitly;
- do not approve a later phase merely because an earlier phase is approved;
- avoid two agents changing the same files or responsibility area concurrently;
- give every phase objective acceptance criteria and executable verification;
- include migration, rollback, and production reconciliation only when relevant;
- record the exact approved commit/version of the plan when practical.

A phase may be **design-locked but not approved to code**. Do not confuse design completion with implementation authorization.

---

## 8. Approved Worker Order Template

```markdown
# Phase [NN] — [Name]

Status: APPROVED
Plan version / commit: [reference]
Approved by: [accountable owner]
Dependencies: [completed phases, decisions, or none]
Risk level: [R0 | R1 | R2 | R3]

## Role

You are the implementation agent for this phase.

## Authority

This document is the approved worker order, not a proposal.
The scope and recorded architecture decisions are fixed for this phase.

## Objective

[One measurable outcome.]

## Business Rules and Invariants

- [Authoritative rule that must remain true.]
- [Invariant that must not be broken.]

## Current-System Evidence

- [Relevant files, schema, tests, or runtime evidence.]
- [Known current behavior.]

## In Scope

- [Required change.]

## Out of Scope

- [Explicit exclusion.]

## Required Implementation

1. [Ordered implementation requirement.]
2. [Ordered implementation requirement.]

## Data / API / UI / Permission Impact

[Only the relevant impacts. Write "None" where confirmed.]

## Failure, Migration, and Rollback Requirements

[Relevant requirements or "Not applicable" with a short reason.]

## Acceptance Criteria

- [Observable criterion.]
- [Regression criterion.]

## Verification

- [Command/check and expected evidence.]
- [Manual or production reconciliation only when required.]

## Stop Conditions

Stop and report evidence if:
- this worker order conflicts with actual code, schema, tests, or data;
- a required business rule or permission boundary is unclear;
- implementation requires a material architecture or scope change;
- migration, destructive action, or rollback safety cannot be established;
- another active change makes the phase unsafe;
- required verification cannot be performed.

## Completion Report

Report:
- files changed;
- implementation summary;
- tests/checks executed and actual results;
- acceptance-criteria evidence;
- deviations: none, or explicit details;
- remaining risks, blockers, and follow-up.
```

---

## 9. Step 5 — Codex Execution Prompt

Attach or point Codex to exactly one approved phase file.

```text
IMPLEMENT the attached approved phase.

The document is the worker order, not a proposal.
The scope is already approved and fixed.

Mandatory rules:
- read the worker order and the relevant actual code before editing;
- implement the document exactly within its authorized scope;
- do not rewrite or re-plan the architecture;
- do not reopen recorded decisions;
- do not expand scope or perform unrelated refactors;
- preserve unrelated working behavior and project conventions;
- add or update relevant regression coverage;
- run the required verification and report actual evidence;
- never claim a check passed if it was not run.

You may choose minor implementation details only when they remain inside the
approved architecture, scope, invariants, and existing project patterns.

If the worker order conflicts with code, data, tests, security, permissions,
or a required business rule, STOP. Report the evidence and the smallest decision
needed. Do not silently choose a different architecture or force the plan through.
```

---

## 10. Change Control | ضبط التغييرات

During implementation:

- **No plan change:** naming, local code organization, or an equivalent minor detail that stays inside the approved design and does not alter behavior, contracts, data, security, scope, or acceptance criteria.
- **Plan amendment required:** any material change to business behavior, architecture, responsibility ownership, schema, public contract, permission boundary, migration strategy, scope, or acceptance criteria.
- **New phase required:** useful work that is valid but outside the approved phase.

When an amendment is required:
1. stop implementation;
2. record the conflicting evidence;
3. return the issue to the final plan owner;
4. obtain the required owner decision;
5. update/version the plan and worker order in Git;
6. resume only after the affected phase is approved again.

Do not silently edit an active worker order to make completed code appear compliant.

---

## 11. Verification and Closure

Implementation is not complete merely because the diff matches the worker order.

Before closing:
- verify every acceptance criterion with evidence;
- run the project's relevant tests, type/static checks, build, integration,
  browser/E2E, migration, security, and reconciliation checks as applicable;
- review the final diff for unintended scope;
- record skipped or impossible checks;
- perform independent review for R2/R3 or other material risk;
- update an ADR only when a durable consequential decision requires it;
- close the phase only when the Definition of Done is satisfied.

The final approved plan remains in the project repository. Claude Code remains the plan owner, while execution evidence stays with the implementation phase, commit, or PR.
