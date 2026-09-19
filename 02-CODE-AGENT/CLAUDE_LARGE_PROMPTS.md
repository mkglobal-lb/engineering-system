# Handling Large Prompts with Claude Code

## Rule

**Never paste large prompts directly into the chat session.**

Instead:
1. Save the large prompt as a file in your project (e.g., `docs/REQUIREMENTS.md`, `docs/BRIEF.md`)
2. Reference the file in your session: "Read docs/REQUIREMENTS.md"
3. Ask Claude to work with the file content

## Why?

### Token Consumption

When you paste a large prompt into the chat:
- The entire text becomes part of the session context
- **Every new message pulls the full prompt again** into the model's context window
- This burns tokens rapidly, even if you only pasted it once

When you save it as a file and reference it:
- Claude reads the file once on demand
- The content is **not repeatedly pulled** with each message
- Significant token savings, especially for prompts with thousands of words

### Context Management

- Chat history accumulates — large pasted content stays in context for the entire session
- File references keep the session clean and focused
- You can use `/clear` between tasks without losing the source material

## When to Use Files vs. Chat

| Prompt Size | Where to Put It |
|-------------|-----------------|
| Small (<500 words) | Chat is fine (one-time paste) |
| Medium (500-2000 words) | Prefer a file |
| Large (>2000 words) | **Always use a file** |

## Workflow

```bash
# 1. Create the file
docs/REQUIREMENTS.md  # or docs/BRIEF.md, docs/PROMPT.md

# 2. In your Claude Code session
"Read docs/REQUIREMENTS.md and ask me clarifying questions"

# 3. After clarification
"Now write a full spec in docs/SPEC.md based on REQUIREMENTS.md"

# 4. Review the spec, then
"Convert SPEC.md into an implementation plan in docs/PLAN.md"

# 5. Execute tasks from PLAN.md one by one
# Use /clear between major tasks
```

## Example File Structure

```
project/
├── docs/
│   ├── REQUIREMENTS.md    # Your large prompt / brief
│   ├── SPEC.md            # Claude's spec (after clarification)
│   └── PLAN.md            # Implementation plan (phases, tasks)
├── CLAUDE.md              # Permanent project rules
└── src/
```

## Common Mistakes

❌ **Pasting 5000+ words directly in chat**
   - Burns tokens on every message
   - Makes session hard to navigate
   - Context becomes bloated

✅ **Saving as `docs/REQUIREMENTS.md` and referencing it**
   - One-time read by Claude
   - Clean session context
   - Easy to update without re-pasting

---

**Last Updated**: 2026-09-19
**Source**: Professional Claude Code Workflow Best Practices
