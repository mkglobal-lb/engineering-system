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

## Checkpoints and Agent Sessions

A new Code Agent session does not require a new branch. Keep the same feature branch while the scope remains the same.

For substantial unfinished work:
- prefer a coherent checkpoint over an arbitrary mid-edit snapshot;
- update the existing project-local handoff/execution plan with verified state;
- create a descriptive checkpoint commit and push it;
- do not confuse a checkpoint commit with feature completion.

Use a Draft PR when it adds review, CI, cumulative-diff, or collaboration value. Do not create one solely because the Agent context changed.

See [`LONG_RUNNING_AGENT_WORKFLOW.md`](../01-WORKFLOWS/LONG_RUNNING_AGENT_WORKFLOW.md).

## Pull Requests / Reviews

If the project uses PRs:
- state objective;
- explain material design decisions;
- list verification;
- call out migrations/security/risks;
- keep the diff reviewable;
- use Draft status for work in progress when early visibility/checks are useful;
- remember that a PR is a review surface, not proof of correctness.

## Delivery

Before production:
- know configuration/secrets requirements;
- know migration order;
- know rollback/recovery for material risk;
- monitor the changed behavior after deployment.

Passing local tests is not proof of successful production rollout.
