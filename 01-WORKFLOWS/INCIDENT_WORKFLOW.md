# Production Incident Workflow — مسار Incident

## Order Matters | الترتيب مهم

`CONTAIN → PRESERVE EVIDENCE → DIAGNOSE → RECOVER → FIX ROOT CAUSE → VERIFY → POSTMORTEM`

Do not start with broad refactoring.

## Immediate Questions

- What user/business impact is happening now?
- Is data still being corrupted/lost?
- Can we safely contain or disable the failing path?
- What evidence/logs/metrics must be preserved?
- What was the last known-good state/change?

## Agent Prompt

```text
INCIDENT ANALYSIS.

Priority order:
1. Contain ongoing damage safely.
2. Preserve evidence.
3. Establish the actual failure path.
4. Identify the safest recovery option.
5. Only then propose the permanent root-cause fix.

Distinguish confirmed facts from hypotheses.
Do not make destructive data corrections without a validated recovery/reconciliation plan.
Do not broaden scope into unrelated cleanup.
```

## Postmortem

Record:
- impact;
- timeline;
- root cause;
- contributing factors;
- detection gap;
- recovery;
- prevention;
- specific action items with owners if applicable.
