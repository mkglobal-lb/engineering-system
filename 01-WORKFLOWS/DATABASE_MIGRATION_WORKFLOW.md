# Database & Migration Workflow — مسار قاعدة البيانات والـ Migration

Database changes are usually **R2 High Risk** unless clearly non-destructive and isolated.

## Before Implementation

Confirm:
- current schema/data reality;
- source of truth for the desired model;
- forward migration;
- backfill if needed;
- compatibility during deployment;
- data validation;
- recovery/rollback strategy;
- impact on old code/jobs/APIs;
- indexes/constraints where material.

## Prompt

```text
PLAN THE DATABASE CHANGE BEFORE APPLYING IT.

Desired change:
[describe]

Inspect the actual schema, migrations, code paths, and data assumptions.

Report:
1. Current state.
2. Target state.
3. Whether the change is additive, destructive, or data-rewriting.
4. Migration sequence.
5. Backfill requirements.
6. Compatibility risks during deployment.
7. Constraints/indexes/invariants affected.
8. Validation queries/checks proving success.
9. Recovery or rollback plan if the change fails.
10. Any irreversible step.

Do not apply destructive or irreversible changes until explicitly approved.
Do not assume production data matches the schema perfectly.
```

## Verification

After migration:
- migration applied successfully;
- expected columns/tables/constraints exist;
- data counts/critical invariants checked;
- application reads/writes work;
- old/null/legacy cases handled if required;
- rollback/recovery feasibility known;
- no silent data loss.
