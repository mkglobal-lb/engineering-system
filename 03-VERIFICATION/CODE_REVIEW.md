# Code Review — مراجعة التغيير

Review in this order:

1. **Correctness** — Does it actually satisfy the requirement?
2. **Business rule** — Is the rule sourced, or assumed?
3. **Root cause** — For bugs, was the real cause fixed?
4. **Scope** — Any unrelated change?
5. **Architecture** — Is responsibility in the correct layer?
6. **Data integrity** — Could data become invalid, duplicated, orphaned, or inconsistent?
7. **Security & permissions** — Is exact authorization enforced?
8. **Backward compatibility** — Existing consumers/workflows protected?
9. **Failure behavior** — What if step 2 of 3 fails?
10. **Edge cases** — Relevant boundaries handled?
11. **Tests** — Do tests prove behavior rather than implementation trivia?
12. **Maintainability** — Is the code simpler/coherent enough?
13. **Observability** — Can material production failures be detected?
14. **Performance** — Only when the change materially affects scale/latency/cost.

## Prompt

```text
REVIEW the final diff against the review checklist.
For each material issue, give:
- severity;
- evidence;
- impact;
- recommended correction.

Also state what you checked and found acceptable.
Do not approve based only on passing tests.
```
