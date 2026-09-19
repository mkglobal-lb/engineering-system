# Long-Running Code Agent Workflow — استمرارية العمل بين Sessions

Use this workflow when one engineering task spans multiple Code Agent sessions or context windows.

استخدم هذا المسار عندما يستمر نفس العمل عبر أكثر من session، أو عندما يصبح الـ context مزدحمًا ويبدأ استمرار نفس المحادثة بخفض الكفاءة أو الوضوح.

Do **not** use it to turn every small task into a heavyweight process.

---

## 1. Core Principle | القاعدة الأساسية

**AI session lifecycle is not Git lifecycle.**

Starting a fresh Agent session does not by itself require:
- a new branch;
- a new pull request;
- a new handoff file;
- declaring the feature complete.

The durable engineering state must live outside chat.

**Chat is temporary context. Git and project evidence are durable context.**

---

## 2. Authority and Sources of Truth | مصادر الحقيقة

Use the right source for the right question:

1. **This Engineering Playbook** — canonical source for cross-project engineering process and Code Agent working practices.
2. **The project repository** — authoritative for project-specific code, schema, tests, configuration, approved requirements, and durable project documentation.
3. **Runtime / production evidence** — authoritative for observed deployed behavior when relevant.
4. **Active project handoff / execution plan + Git history** — continuity record for unfinished multi-session work.
5. **Pull request** — review, discussion, CI, and cumulative-diff surface; not proof that the implementation is correct.
6. **Agent chat history** — temporary working context only.

If documentation conflicts with code, tests, data, an approved business rule, or production evidence, surface the conflict. Do not silently treat a stale handoff as truth.

Project-specific handoffs belong in the project repository, not in this central playbook.

---

## 3. When to Start a Fresh Session

Use judgment. A new session is appropriate when one or more of these are true:

- the Agent starts repeating investigation or losing track of prior decisions;
- context has become noisy enough that relevant facts are hard to recover;
- the Agent contradicts established project evidence or earlier verified decisions;
- continuing the same session is materially inefficient in context/token usage;
- a natural implementation checkpoint has been reached;
- a tool/session limit or interruption requires continuation elsewhere;
- the work is intentionally being handed to another Agent or developer.

Do not use a provider-specific usage percentage as the only engineering rule. The signal is loss of efficiency, clarity, or continuity.

---

## 4. End-of-Session Checkpoint

Before leaving a substantial unfinished task:

### A. Re-establish actual state

Inspect:
- current branch;
- `git status`;
- relevant diff;
- recent Git history;
- the active plan/handoff;
- relevant tests or verification evidence.

Do not rely on memory of the conversation.

### B. Leave a coherent state

Prefer a natural checkpoint where:
- the current change is understandable;
- unrelated working behavior is not knowingly broken;
- relevant verification has been run where practical;
- incomplete or failing behavior is stated explicitly.

Avoid arbitrary mid-edit snapshots when a coherent checkpoint can be reached safely.

### C. Update the existing project-local handoff or execution plan

Do **not** create a new handoff file every session.

Record only verified information:
- objective / current scope;
- completed work;
- remaining work;
- material decisions and why;
- known risks, blockers, or failures;
- verification actually run and its result;
- the next concrete step.

Update `CURRENT_STATE` or equivalent durable project documentation only when the durable project/module state changed. Do not use it as a session diary.

### D. Commit and push

Create a descriptive checkpoint commit and push the **same feature branch**.

A checkpoint commit means:

> this progress is intentionally preserved and recoverable.

It does **not** mean:

> the feature is complete or ready to merge.

If the checkpoint is knowingly incomplete, make that clear in the commit/PR context rather than pretending it is finished.

---

## 5. When to Use a Draft Pull Request

A fresh Agent session does **not** automatically require a pull request.

Use a **Draft PR** when it adds real engineering value, for example:
- substantial or cross-cutting changes;
- multiple commits or multiple sessions;
- backend + frontend or multi-repository coordination;
- early review is useful;
- CI/checks should run against the cumulative branch;
- the full branch diff needs a stable review surface;
- another developer/Agent needs visibility into work in progress.

A Draft PR is a collaboration and review checkpoint. It is not evidence of correctness and it is not permission to merge.

Small, isolated work may use:

`checkpoint commit → push → fresh session`

Substantial multi-session work usually benefits from:

`verify → update handoff → checkpoint commit → push → Draft PR → fresh session`

Continue on the same branch while the scope remains the same.

---

## 6. Starting the Fresh Session

The new Agent must get its bearings **before editing**.

Recommended order:

1. Read the project's Agent/developer instructions.
2. Read the active handoff / execution plan.
3. Inspect `git status`, current branch, recent `git log`, and relevant diff.
4. Inspect the Draft PR when one exists.
5. Read only the relevant durable project documentation such as `CURRENT_STATE`.
6. Run a small baseline verification appropriate to the touched area.
7. Continue the existing scope without rewriting working code unnecessarily.

### Resume prompt

```text
RESUME the current work from repository state.

The repository and verified project evidence are authoritative.
Do not rely on previous chat history.

Before editing:
1. read the active handoff/execution plan and relevant project instructions;
2. inspect the current branch, git status, recent git history, and relevant diff;
3. inspect the Draft PR if one exists;
4. read only the relevant durable project documentation;
5. run the appropriate baseline verification.

Then report:
- confirmed completed state;
- remaining scope;
- blockers or contradictions;
- the next implementation step.

Continue on the current feature branch unless the scope has materially changed.
Do not redo verified working behavior without evidence.
```

---

## 7. Checkpoint Prompt

```text
CREATE A CLEAN ENGINEERING CHECKPOINT for continuation in a fresh session.

Do not declare the feature complete unless the acceptance criteria and Definition of Done are actually satisfied.

Before ending:
1. inspect the actual branch, git status, diff, recent history, implementation, and relevant tests;
2. update the existing project-local handoff/execution plan — do not create duplicate handoff files;
3. record only verified completed work, remaining work, decisions, risks/blockers, verification results, and the next concrete step;
4. update durable CURRENT_STATE/project documentation only if durable system state materially changed;
5. leave the implementation in the cleanest coherent state practical;
6. create a descriptive checkpoint commit and push the current feature branch;
7. if the work is substantial and the project uses pull requests, create or update a Draft PR; do not mark it ready merely because the session is ending.

Report anything incomplete or unverified explicitly.
```

---

## 8. Completion Is Separate

Session rollover and feature completion are different events.

A feature becomes ready for review/merge only after:
- acceptance criteria are satisfied;
- required verification is complete;
- the final cumulative diff is reviewed;
- remaining risks are explicit;
- the project's Definition of Done is satisfied;
- the PR is moved from Draft to Ready only when the work is actually review-ready.

Then follow the project's normal review and merge policy.

---

## 9. Evidence Basis | أساس هذه القاعدة

This workflow is based on:
- **Anthropic — Effective harnesses for long-running agents:** recommends incremental progress, descriptive Git commits, progress artifacts, Git history, clean session handoffs, and fresh-session orientation.
  https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents
- **OpenAI — Harness engineering: leveraging Codex in an agent-first world:** treats repository knowledge as the system of record, uses versioned active/completed execution plans, and favors progressive disclosure over one giant instruction manual.
  https://openai.com/index/harness-engineering/
- **GitHub Docs — Writing code for a project / Pull requests:** pull requests collect commits, discussion, review, and checks; Draft PRs are explicitly for work in progress and early feedback/checks.
  https://docs.github.com/en/pull-requests/concepts/writing-code-for-a-project
  https://docs.github.com/en/pull-requests/reference/pull-requests

These references support the operating principles. Project-specific branch, review, CI, and release rules still take precedence inside each project.
