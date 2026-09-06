# Release Workflow — مسار Release

## Pre-Release

Confirm relevant items:
- intended changes are identified;
- tests/checks pass;
- migrations are ordered and understood;
- secrets/config are ready;
- feature flags if used are correct;
- monitoring/logging can detect failure;
- rollback/recovery path exists for material risk;
- known risks are explicit.

## Prompt

```text
RELEASE READINESS REVIEW.

For this release, report:
1. Included changes.
2. Required migrations/configuration.
3. Verification already completed.
4. Production-specific risks.
5. Backward-compatibility concerns.
6. Rollback/recovery approach.
7. What should be monitored immediately after release.
8. Any reason this release should be blocked.

Do not mark ready if a required check has not actually been run.
```

## After Release

Verify the real production behavior relevant to the change. Passing CI alone is not proof that deployment succeeded.
