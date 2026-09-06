# Security Workflow — مسار الأمان

Use this for auth, authorization, sensitive data, secrets, suspicious exposure, or security-sensitive changes.

## Prompt

```text
SECURITY REVIEW.

Review the relevant change/flow for:
1. Authentication: who is the caller?
2. Authorization: are they allowed to perform this exact action on this exact resource?
3. Input validation and unsafe parsing.
4. Sensitive data exposure in UI/API/logs/errors.
5. Secrets, tokens, credentials, or keys.
6. Injection or unsafe command/query construction.
7. Cross-tenant / cross-user data access.
8. Dangerous defaults and fail-open behavior.
9. Abuse/rate-limit concerns where material.
10. Auditability for security-sensitive actions.

Use actual code evidence.
Do not report "secure" as a blanket statement.
List what you checked, findings, severity, and remediation.
```

## Rule

Never "fix" a security finding by merely hiding the UI if the backend permission boundary remains open.
