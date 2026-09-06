# Engineering Decisions & ADRs — القرارات الهندسية

Not every choice needs an ADR. Use one for durable, consequential decisions.

## Use an ADR when the decision is:

- difficult/expensive to reverse;
- affects architecture across modules/services;
- changes a public contract;
- materially affects security/data consistency;
- likely to be questioned later ("why did we choose this?");
- has real trade-offs between valid alternatives.

## Minimal ADR Template

```markdown
# ADR-XXX: [Decision]

Status: Proposed | Accepted | Superseded | Rejected
Date: YYYY-MM-DD

## Context
What problem/constraint requires a decision?

## Decision
What are we choosing?

## Alternatives Considered
What reasonable alternatives were considered?

## Trade-offs
What do we gain and what do we accept?

## Consequences
What changes now and what becomes harder/easier later?

## Verification / Follow-up
How will we know the decision works?
```

## Decision Rule

Do not make architecture choices because they are fashionable.
Choose based on requirements, constraints, operational cost, risk, and reversibility.
