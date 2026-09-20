# How to Work With Code Agents — كيف تتعامل مع Code Agents

## Core Rule | القاعدة

Treat the agent as an engineering executor/reviewer, not an unquestioned authority.

تعامل مع الـ agent كمهندس ينفذ ويحلل، وليس كمصدر حقيقة نهائي.

## Professional Operating Posture | مستوى الخبرة المطلوب

For substantial engineering work, instruct the agent to operate as a **professional senior full-stack developer and software engineer with the judgment associated with 15+ years of relevant experience and deep domain knowledge**.

This defines the expected breadth and standard of judgment across product, architecture, backend, frontend, data, security, testing, delivery, and operations. It is **not evidence of competence or correctness**. The agent must still inspect the repository, follow project-specific instructions, cite evidence, surface uncertainty, and verify its work.

Recommended wording:

```text
Act as a professional senior full-stack developer and software engineer with the judgment expected from 15+ years of relevant experience and deep expertise in this domain.

Work from the repository and authoritative project evidence. Think end to end across requirements, architecture, data, backend, APIs, frontend/UI, security, permissions, testing, delivery, rollback, and maintainability, but change only what the approved scope requires.

Do not rely on the role statement as proof. Distinguish facts from assumptions, surface conflicts and uncertainty, and support conclusions with actual evidence.
```

Do not repeatedly decorate every small command with seniority claims. Put this operating posture once in the task contract or project Agent instructions, then use precise objectives, constraints, acceptance criteria, and verification.

## Good Task Contract | عقد المهمة الجيد

For non-trivial tasks, provide as many of these as are known:

1. **Objective** — what outcome is required.
2. **Source of truth** — business rule, code, schema, doc, API contract, production evidence.
3. **Current behavior** — what happens now.
4. **Expected behavior** — what should happen.
5. **Scope** — what is included.
6. **Out of scope** — what should not be changed.
7. **Risk level** — R0/R1/R2/R3.
8. **Invariants** — conditions that must remain true.
9. **Acceptance criteria** — measurable completion conditions.
10. **Verification** — what must be run/checked.
11. **Stop conditions** — when the agent must surface uncertainty instead of guessing.

You do not need all 11 for a typo. Use judgment.

## Evidence Discipline | انضباط الدليل

Ask for:
- files inspected/changed;
- actual commands run;
- actual pass/fail result;
- relevant test counts/output excerpts;
- diff summary;
- unverified assumptions;
- limits of investigation.

Do not require giant logs when a concise result is enough.

For material work, require a concise evidence record containing:
- claim or acceptance criterion;
- evidence source;
- exact command/check or manual action;
- environment and test identity when relevant;
- observed result;
- limitation, failure, or unverified item.

Screenshots, logs, tests, browser behavior, database queries, and diffs are evidence only for what they directly demonstrate. Confidence, a green compile, a written handoff, or an agent saying "done" is not evidence by itself.

## Documentation and Conflict Discipline | انضباط التوثيق والتعارض

After a material change:
- update the active project handoff/execution plan when work is ongoing or spans sessions;
- update `CURRENT_STATE` or equivalent only when durable project/module behavior, architecture, contracts, dependencies, or operational state materially changed;
- update other authoritative documentation affected by the change;
- compare documentation against code, tests, approved requirements, data, and runtime evidence;
- resolve contradictions when the source of truth is clear;
- when it is not clear, stop, record the conflict and impact, and request a decision instead of silently choosing.

Documentation records verified state. It must never be used to manufacture evidence or overwrite a contradictory fact without resolution.

## Session Continuity | استمرارية الـ Sessions

For substantial work that spans sessions:

- treat chat as temporary working context, not durable project state;
- preserve progress in the project repository through Git plus the existing active handoff/execution plan;
- prefer a coherent checkpoint before changing sessions;
- continue the same feature branch while scope remains the same;
- use a Draft PR when it provides review, CI, cumulative-diff, or collaboration value — not merely because the Agent session changed;
- make the fresh Agent inspect repository state and baseline verification before editing;
- keep durable `CURRENT_STATE` documentation separate from session-by-session progress.

See [`LONG_RUNNING_AGENT_WORKFLOW.md`](../01-WORKFLOWS/LONG_RUNNING_AGENT_WORKFLOW.md).

## Do Not Let the Agent

- invent business rules;
- change scope silently;
- delete/weaken tests to get green CI;
- hide missing data with fake defaults;
- treat compilation as complete verification;
- claim tests were run when they were not;
- mix unrelated refactors into a focused fix;
- make destructive changes without surfacing them.
