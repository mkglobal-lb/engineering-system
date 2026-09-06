# Architecture & Design — العمارة والتصميم

## Decision Framework

Before introducing a new architecture/pattern, ask:

1. What concrete problem does it solve?
2. What is the simplest alternative?
3. What complexity does it add?
4. What are the operational consequences?
5. What are the data consistency consequences?
6. What is the failure mode?
7. What will be harder to change later?
8. Is the decision reversible?
9. Is the scale problem real, measured, or hypothetical?
10. Does the codebase already have a coherent pattern?

## Rules

- Do not default to microservices, event-driven systems, CQRS, caches, queues, or distributed locks without a concrete requirement.
- Do not force one database/framework across all projects.
- Prefer clear ownership of responsibilities.
- Keep domain/business rules out of presentation-only layers.
- Avoid creating multiple "sources of truth" for the same fact.
- Public contracts (API/events/data formats) need stronger compatibility discipline than internal code.
- Shared abstractions should be created from demonstrated commonality, not predicted commonality.

## Scale

"Works at 10×" does not mean design everything for 10× now. Identify the first real bottleneck and preserve sensible extension points where inexpensive.
