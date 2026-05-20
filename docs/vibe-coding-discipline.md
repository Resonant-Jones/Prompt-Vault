# Vibe Coding Discipline

*Vibe coding is what happens when you skip the loop. Here's how to stop.*

## What Is Vibe Coding?

**Vibe coding** = Prompt an agent → Accept output → Move on. No verification. No receipts. No drift check.

It's called "vibe coding" because you're navigating by feel, not by evidence. The agent said it works. The code looks plausible. Ship it.

The Prompt-nomicon exists to replace this with a discipline.

## Why Vibe Coding Is Dangerous

| Problem | Consequence |
|---------|-------------|
| Hallucinated APIs | Code references functions that don't exist |
| Phantom completion | Agent claims done, nothing actually works |
| Scope creep | Agent refactors code you didn't ask it to touch |
| Ghost features | Agent adds "nice to haves" that break things |
| Doc decay | Docs describe intent, not reality |
| Proof erosion | Yesterday's evidence doesn't apply to today's code |

## The Vibe Coding Checklist

If you answer "yes" to any of these, you're vibe coding:

- [ ] Did you accept the agent's output without running validation commands?
- [ ] Did you skip writing a receipt?
- [ ] Did you merge without checking for secrets in the diff?
- [ ] Did the agent change files outside the scope you defined?
- [ ] Did you treat the agent's claim of completion as proof?
- [ ] Did you skip the drift review?
- [ ] Did the agent add features you didn't ask for — and you kept them?

## The Antidote: The Full Loop

For every task, run the full loop:

```
Prompt → Task → Spec → Execution → Receipt → Drift Review
```

### 1. Prompt
Define mode, scope, constraints, and output contract. **Do not skip this.**

### 2. Task
Separate plan from implementation. If you're still figuring things out, the prompt should forbid file mutation.

### 3. Spec
Reason within evidence. No invented APIs, files, or components. Cite sources.

### 4. Execution
Smallest coherent change. Validate. Check for secrets.

### 5. Receipt
Record: what was attempted, what happened, what remains uncertain.

### 6. Drift Review
Find and flag stale docs, superseded proofs, outdated claims.

## Red Flags in Agent Output

Watch for these patterns — they signal the agent is vibing, not reasoning:

- **"This should work."** → Should? Prove it.
- **"The implementation is complete."** → Complete per what criteria?
- **"All tests pass."** → Which tests? Show the output.
- **"I've added support for..."** → Did you ask for that?
- **"The architecture naturally supports..."** → According to what docs?
- **"This follows the pattern used in..."** → Show me the existing pattern.

## When You Catch Yourself Vibe Coding

1. Stop. Don't merge. Don't ship.
2. Write the acceptance criteria you *should* have written.
3. Run the validation commands.
4. Write a receipt.
5. Run a drift review.
6. If the agent's output doesn't match, file a new bounded task to fix it.

## Making It Stick

- Keep the [`coding-agent-task.md`](../templates/coding-agent-task.md) template easily accessible.
- Require receipts in PR descriptions.
- Run drift reviews as part of your release checklist.
- If you do the same workflow three times, template it. If it runs unattended, script it.

## Next

→ [`docs/codex-workflows.md`](codex-workflows.md)
