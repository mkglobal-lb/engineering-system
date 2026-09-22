# Investigation & Documentation Audit Workflow

Use this workflow before substantial or risky implementation when the task depends on understanding the existing repository, or when a documentation audit is explicitly requested.

Do **not** turn every small change into a repository-wide audit. Investigation depth must scale with scope and risk.

---

## 1. When to Use This Workflow

Use it when one or more apply:

- the task is R2/R3 or cross-cutting;
- requirements or current behavior are ambiguous;
- architecture, APIs, data, permissions, finance, migrations, or external contracts may be affected;
- documentation appears contradictory, stale, duplicated, or incomplete;
- a large implementation session is about to begin;
- the owner explicitly requests a documentation/repository audit.

For R0/R1 work, inspect only the instructions and documentation relevant to the touched area unless evidence expands the scope.

---

## 2. Establish Authority Before Reading Everything

Before editing code:

1. Identify the task objective, approved scope, risk level, and acceptance criteria.
2. Read project-level agent/developer instructions first, such as:
   - `AGENTS.md`, `agents.md`;
   - `CLAUDE.md`, `claude.md`;
   - `README.md`, `CONTRIBUTING.md`;
   - architecture or project-specific source-of-truth files referenced by those instructions.
3. Identify the authoritative source for each material question:
   - approved business requirement;
   - code/schema/API contract;
   - tests;
   - configuration;
   - runtime/production evidence when relevant;
   - durable project documentation.
4. Do not assume that a document is authoritative merely because it is newer, longer, or more detailed.

If two authoritative-looking sources conflict and the correct behavior cannot be established from evidence, stop and surface the conflict instead of silently choosing.

---

## 3. Documentation Discovery

### Normal implementation task

Discover documentation proportionate to the touched area:

- root instructions and project map;
- relevant `docs/`, `documentation/`, `doc/` paths;
- files linked from those documents;
- relevant architecture, API, schema, operations, security, release, or module guides;
- active execution plan/handoff if the work spans sessions.

Do **not** recursively read every Markdown file by default.

### Explicit full documentation audit

When the task is specifically to audit documentation:

1. Build an inventory of documentation files and classify each by purpose.
2. Read the highest-level sources first.
3. Follow references and cross-links systematically.
4. Compare documentation with the actual repository, tests, configuration, and contracts.
5. Record files that were not fully verified and why.

A file inventory is not proof that every statement in every file was validated.

---

## 4. Audit Dimensions

For each relevant document, check the following.

### Accuracy and authority

- Does it match current code, schema, configuration, API contracts, and approved requirements?
- Does it claim behavior that is not supported by evidence?
- Does another source contradict it?
- Is its authority and intended audience clear?

### Structure and discoverability

- Is the file in the correct location?
- Is its name descriptive?
- Is it linked from the appropriate index?
- Is content duplicated without a clear reason?
- Would merging or splitting materially improve maintainability?

### Lifecycle and maintainability

- Is the content durable knowledge, temporary execution context, a requirement, a handoff, or a historical record?
- Does it have a clear lifecycle?
- Is an old date merely old, or is the content actually obsolete?
- Are TODOs still valid and attributable?

### Technical consistency

When relevant, verify:

- API routes/contracts;
- environment variables and setup;
- dependency/tool versions;
- auth/authz behavior;
- database/migration behavior;
- deployment and rollback instructions;
- diagrams and examples;
- internal links and referenced paths.

Do not claim an example or diagram was tested if it was only read.

---

## 5. Classify Findings Before Fixing

Classify each material finding:

- **Incorrect** — contradicted by authoritative evidence.
- **Conflicting** — two sources disagree and authority must be resolved.
- **Superseded** — replaced by a newer authoritative source with no remaining active role.
- **Duplicated** — same guidance exists in multiple places without justified ownership.
- **Missing** — an important durable contract or workflow is undocumented.
- **Misplaced** — useful content is in the wrong location.
- **Unclear** — wording or ownership creates ambiguity.
- **Historical** — no longer active, but useful as retained decision/history.
- **Unverified** — could not be confirmed against actual implementation or runtime evidence.

Severity should be based on impact, not document age.

---

## 6. Automatic Documentation Fix Policy

### Safe to fix automatically when in scope

Examples:

- typos and grammar that do not alter meaning;
- broken internal links with an unambiguous correct target;
- stale file/path names proven by the repository;
- duplicated headings or formatting defects;
- missing index links;
- wording that clearly misstates a mechanically verifiable fact;
- consolidation that preserves all unique authoritative content and links.

### Do not silently auto-decide

Require evidence or an owner/authority decision when the change would alter:

- business rules;
- finance/accounting meaning;
- security or permission boundaries;
- data retention/destructive behavior;
- public API contracts;
- migration strategy;
- architecture ownership;
- operational/release policy.

Documentation must record the decision; it must not manufacture it.

### Deletion rule

**Never delete a document because it is older than an arbitrary time threshold.**

Delete only when all are true:

1. it is demonstrably superseded, duplicated, invalid, or temporary;
2. it contains no unique active requirement, decision, contract, evidence, or operational knowledge;
3. inbound links/references are updated;
4. Git history is sufficient for historical recovery, or the project has another approved archive;
5. deletion does not remove information still required by active work or compliance.

If historical context remains useful, archive or mark it superseded instead of deleting it.

---

## 7. CURRENT_STATE and HANDOFF Rules

Do not create new state/handoff files automatically in every project or session.

### CURRENT_STATE

Update an existing `CURRENT_STATE` or equivalent only when durable project/module state materially changes, such as:

- architecture or ownership;
- active contracts or integration behavior;
- durable operational state;
- material dependency/configuration requirements;
- accepted business behavior that future work must know.

It is not a session diary.

Create a new `CURRENT_STATE` only when the project genuinely needs a durable state document and no equivalent source already exists.

### HANDOFF / execution plan

Use an existing handoff/execution plan when work is substantial, unfinished, or spans sessions.

Update it with verified:

- completed work;
- remaining scope;
- decisions;
- blockers/risks;
- verification;
- next step.

Do not create a new handoff file for every session. Reuse the active one unless the project intentionally starts a new workstream.

Project naming conventions take precedence over generic names such as `docs/00-CURRENT_STATE.md` or `docs/01-HANDOFF.md`.

---

## 8. Pre-Code Investigation Report

Before implementation on a substantial task, report concisely:

```markdown
## Investigation Report

### Scope and authority
- Objective:
- Risk level:
- Sources of truth:
- Relevant instructions/docs read:

### Findings
| Severity | Finding | Evidence | Action |
|---|---|---|---|

### Documentation changes
- Updated:
- Created:
- Moved/renamed:
- Deleted/archived:
- Deferred because a decision is required:

### Implementation readiness
- Confirmed scope:
- Invariants:
- Risks/blockers:
- Planned files/modules:
```

Do not state "all documentation issues resolved" unless the audit scope and evidence actually support that claim.

---

## 9. Implementation Boundary

Documentation cleanup must not silently expand a feature task.

Before coding:

- fix documentation defects that are directly relevant, low-risk, and evidenced;
- record unrelated documentation debt separately;
- stop on unresolved material conflicts that affect implementation;
- proceed when the relevant source of truth is sufficiently established.

A repository does not need to be documentation-perfect before every code change.

---

## 10. Post-Code Verification

After implementation:

1. verify the code against acceptance criteria;
2. verify any documentation changed as part of the task;
3. update diagrams/contracts/examples only when the implementation changed them;
4. update handoff/current state according to the rules above;
5. review the final diff for accidental documentation scope;
6. report what was verified and what remains unverified.

Use the project Definition of Done and relevant verification workflow.

---

## 11. Stop Conditions

Stop and surface evidence if:

- authoritative sources conflict on required behavior;
- a documentation "fix" would actually decide an unapproved business or architecture rule;
- a proposed deletion may remove unique knowledge;
- required verification cannot be performed;
- implementation would exceed approved scope materially;
- documentation and code disagree in a way that changes risk or acceptance criteria.

The goal is not maximum document churn. The goal is trustworthy, navigable, evidence-based project knowledge.
