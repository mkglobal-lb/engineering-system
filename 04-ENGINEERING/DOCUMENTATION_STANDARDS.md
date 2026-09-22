# Documentation Standards

Documentation is an engineering control surface. It should preserve durable knowledge, make authority clear, and remain cheap enough to maintain.

---

## 1. Document the Right Things

Prefer documentation for:

- business and system invariants;
- architecture and ownership boundaries;
- public/internal contracts;
- setup and operational procedures;
- security and permission rules;
- migration/release/recovery procedures;
- accepted decisions and their rationale;
- active multi-session execution state;
- requirements that remain authoritative.

Avoid documenting:

- obvious code line-by-line;
- transient chat history;
- duplicated instructions with no ownership;
- speculative future behavior presented as current fact;
- verification claims that were never executed.

---

## 2. Document Classes

Every substantial project document should have a clear role.

### Durable reference

Examples: architecture, API contracts, security model, operational runbooks.

Update when the durable system changes.

### Requirement / approved plan

Defines intended behavior or authorized implementation scope.

Keep until implemented, superseded, or intentionally archived according to project policy.

### CURRENT_STATE / status reference

Summarizes durable present state that is expensive to reconstruct.

Do not use as a daily/session log.

### Active handoff / execution plan

Tracks unfinished multi-session work.

Keep concise, verified, and updated at coherent checkpoints.

### Decision record / ADR

Captures consequential decisions, alternatives, rationale, and consequences.

Use for decisions worth preserving, not every implementation detail.

### Temporary working input

Examples: copied large prompts, raw investigation notes, one-off review briefs.

Give them an explicit lifecycle. After the work is integrated into authoritative docs/code:
- delete if fully superseded and no unique knowledge remains;
- archive if historical context has continuing value;
- promote durable content into the correct canonical document.

A temporary prompt file should not become permanent source-of-truth by accident.

---

## 3. Authority Must Be Explicit

A document should make clear, from context or content:

- what question it answers;
- whether it is authoritative, supporting, historical, or temporary;
- what higher-authority source takes precedence when applicable.

Newer is not automatically more authoritative.

When two sources conflict, resolve authority for the specific question and update stale documentation when evidence is sufficient.

---

## 4. Freshness Is Evidence-Based

Do not declare a document obsolete only because of age.

A document is stale when current authoritative evidence shows that its active claims are no longer valid.

Useful signals include:

- referenced paths no longer exist;
- documented API/schema differs from implementation;
- setup instructions fail;
- a decision was formally superseded;
- the document duplicates a newer canonical source;
- the project no longer uses the described workflow.

Dates can trigger review. They are not deletion criteria.

---

## 5. Create, Merge, Split, Move, or Delete with Purpose

### Create

Create a document only when it captures durable knowledge or an active work artifact that has no adequate existing home.

### Merge

Merge when:
- ownership and audience are the same;
- content is materially duplicated;
- one canonical file will be easier to maintain.

### Split

Split when:
- audiences or lifecycles differ;
- one file mixes unrelated authorities;
- navigation and ownership materially improve.

Do not split merely because a file is long.

### Move / rename

Move or rename when discoverability or ownership improves materially. Update all inbound links.

### Delete

Delete only when:
- the content is demonstrably superseded, duplicated, invalid, or temporary;
- no unique active knowledge remains;
- references are updated;
- retention/compliance rules allow it;
- historical recovery is available where needed.

Prefer archive/superseded markers when historical context remains valuable.

---

## 6. Naming and Location

Follow the project's existing conventions.

Prefer names that describe purpose, for example:

- `AUTHENTICATION.md`
- `PAYMENTS_ARCHITECTURE.md`
- `DEPLOYMENT_RUNBOOK.md`
- `CURRENT_STATE.md`
- `HANDOFF.md`

Avoid vague names such as `notes2.md`, `final-final.md`, or date-only files unless the project intentionally uses dated records.

Do not impose numeric prefixes universally. Use them only when the repository deliberately uses ordered navigation.

---

## 7. CURRENT_STATE and HANDOFF

### CURRENT_STATE

Include only durable facts worth carrying across future work:

- implemented capability;
- current architecture/ownership;
- material constraints;
- known durable limitations;
- deployment/migration state when relevant.

Exclude session narration and speculative plans.

### HANDOFF

For active unfinished work, include:

- objective and scope;
- verified completed work;
- remaining work;
- decisions and rationale;
- blockers/risks;
- verification performed;
- next concrete step;
- branch/PR/commit references when useful.

Reuse the active handoff. Do not create a new one per session unless a separate workstream begins.

---

## 8. Code Examples, Commands, Diagrams, and Links

A document must distinguish between:

- **verified now**;
- **illustrative example**;
- **not recently verified**.

When changing behavior represented by a diagram, contract, command, or example, update it in the same work when practical.

Do not claim "all examples tested" unless they were actually executed in the relevant environment.

Broken links and stale paths should be fixed when found and unambiguous.

---

## 9. Security and Sensitive Information

Documentation must not contain:

- real passwords or private keys;
- production secrets/tokens;
- customer-sensitive data not required for the document;
- unsafe instructions that bypass project controls.

Use placeholders and documented secret-management mechanisms.

Test credentials should follow the project's authorized non-production test-user policy and should not become undocumented shared secrets.

---

## 10. Change Discipline

Documentation changes should be reviewable like code:

- keep scope attributable;
- preserve authoritative content during consolidation;
- explain material deletions/moves;
- update indexes/links;
- verify mechanically checkable claims where feasible;
- separate unresolved assumptions from facts.

The goal is a smaller number of trustworthy documents, not a larger number of documents.
