# Handling Large Task Inputs with Claude Code

## Purpose

Use files for large task inputs when that improves navigation, reuse, reviewability, or session continuity.

Do not treat a large prompt file as permanent project documentation merely because it was useful during implementation.

## Practical Rule

- Small instruction: chat is usually fine.
- Larger requirement/review brief: a repository file is often easier to reference and version.
- Durable requirement or approved plan: store it in the project's canonical documentation location.
- Temporary one-off prompt/review input: mark its lifecycle and remove or archive it after its useful content has been integrated.

Exact context/token behavior varies by tool and provider. The engineering reason to prefer a file is maintainability and a stable source that can be re-read from repository state, not a guaranteed token-saving formula.

## Recommended Workflow

1. Classify the input:
   - durable requirement;
   - approved plan;
   - temporary working prompt;
   - investigation/review brief.
2. Save it only if a file improves the work.
3. Give it a clear name and location.
4. Tell the Agent whether the file is authoritative or only supporting input.
5. Produce the durable output in the correct canonical file/code.
6. At closure, decide whether the input should:
   - remain authoritative;
   - be archived/superseded;
   - be deleted because it is fully temporary and contains no unique knowledge.

## Example

```text
docs/requirements/FINANCE_RECONCILIATION_REQUIREMENTS.md
docs/plans/FINANCE_RECONCILIATION_PLAN.md
docs/work/FINANCE_RECONCILIATION_REVIEW_INPUT.md
```

In the Agent session:

```text
Read docs/requirements/FINANCE_RECONCILIATION_REQUIREMENTS.md as the approved requirement.
Read docs/work/FINANCE_RECONCILIATION_REVIEW_INPUT.md as supporting review input only.
Do not treat the review input as a source of truth when it conflicts with the approved requirement or actual repository evidence.
```

After the work is complete, the temporary review input should not remain indefinitely unless it still provides unique historical value.

## Avoid

- pasting very large repeated instructions into every message;
- keeping multiple "final", "final2", or duplicate prompt files;
- leaving temporary prompts beside durable requirements with no status distinction;
- converting AI-generated text into project truth without verification;
- deleting old files based only on age.

See:
- [`DOCUMENTATION_STANDARDS.md`](../04-ENGINEERING/DOCUMENTATION_STANDARDS.md)
- [`INVESTIGATION_AND_DOCUMENTATION_AUDIT.md`](../01-WORKFLOWS/INVESTIGATION_AND_DOCUMENTATION_AUDIT.md)
