# Git & Delivery — Git وطريقة التسليم

## Commits

Prefer commits that are:
- coherent;
- reviewable;
- scoped to one logical change;
- described by intent, not only file names.

Avoid mixing:
- feature + unrelated refactor;
- bug fix + formatting sweep;
- migration + unrelated cleanup.

## Branching

Use the branching model appropriate to the team/project. The universal rule is:
- protect production/mainline appropriately;
- keep work attributable and reviewable;
- avoid parallel agents modifying the same files/area without coordination.

## Pull Requests / Reviews

If the project uses PRs:
- state objective;
- explain material design decisions;
- list verification;
- call out migrations/security/risks;
- keep the diff reviewable.

## Delivery

Before production:
- know configuration/secrets requirements;
- know migration order;
- know rollback/recovery for material risk;
- monitor the changed behavior after deployment.

Passing local tests is not proof of successful production rollout.
