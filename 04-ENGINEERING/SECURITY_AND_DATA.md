# Security & Data — الأمان والبيانات

## Security Baseline

For relevant systems, think about:
- authentication;
- authorization;
- input validation;
- output/data exposure;
- secrets;
- encryption where required;
- dependency/supply-chain risk;
- logging without sensitive leakage;
- secure defaults;
- audit trail for sensitive actions;
- recovery from misuse or compromise.

## Data Integrity

Define invariants for critical data.

Examples:
- a transaction is not counted twice;
- an order cannot reference a missing required parent;
- a balance is derived from an authoritative ledger, not manually synchronized copies;
- status transitions follow allowed paths.

## Destructive Changes

Before delete/rewrite/backfill:
- identify exact affected rows/resources;
- make selection deterministic;
- validate backups/recovery where material;
- preview/dry-run where practical;
- verify counts and invariants after execution.

## Permissions

Ask:
> "Can this actor perform this action on this specific resource?"

Not only:
> "Is the actor authenticated?"
