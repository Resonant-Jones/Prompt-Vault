# AI-Assisted Coding

*How to use coding agents without collapsing into "the agent said it works" theater.*

## The Problem

AI coding agents are powerful but ungrounded by default. Without explicit constraints, they will:

- Invent APIs, files, and components that don't exist
- Implement solutions without verifying they work
- Confuse planning with execution
- Treat their own output as evidence of correctness
- Make release claims based on code changes alone

The result: teams ship code the agent wrote but nobody verified, docs that describe what the agent intended rather than what exists, and a growing gap between claimed and actual system behavior.

## The Solution: Discipline Over Magic

The Prompt-nomicon replaces "agent magic" with a disciplined workflow. The agent becomes a tool you constrain, not an oracle you trust.

### Before the Agent Acts

1. **Define the mode.** Is this planning, implementation, research, or audit? Say so explicitly.
2. **Bind the scope.** What files/areas are in play? What is explicitly forbidden?
3. **Set acceptance criteria.** What does "done" look like? What validation commands prove it?
4. **Define the output contract.** What must the agent report back?

### While the Agent Acts

- The agent must reason within provided evidence, not external knowledge.
- The agent must not invent files, APIs, or components.
- The agent must cite sources for its reasoning steps.
- For repetitive work, the agent should write scripts, not simulate loops in prose.

### After the Agent Acts

1. **Verify.** Run the validation commands. Check the diff. Look for secrets or scope creep.
2. **Receipt.** Record what was attempted, what happened, and what remains uncertain.
3. **Drift check.** Update docs that are now stale. Mark proofs that are now superseded.

## The Five Truth Surfaces

Every claim falls into exactly one of these surfaces. A lower-numbered surface must never claim the authority of a higher-numbered one.

| # | Surface | Meaning | Example |
|---|---------|---------|---------|
| 1 | Plan | What we intend to do | "We'll refactor the auth module" |
| 2 | Implementation | Code we changed | "The auth module now uses tokens" |
| 3 | Test evidence | Automated checks passed | "Auth tests pass in CI" |
| 4 | Runtime proof | Observed working behavior | "Auth flow works in staging" |
| 5 | Release promise | Users can use it | "Token auth is live in production" |

## Agent Selection: When to Use What

### Use a Coding Agent When

- The task requires reading and modifying multiple files
- The task requires understanding repo structure and patterns
- The task has clear acceptance criteria you can verify
- You have bounded the scope to specific areas

### Use a Direct Tool/Script When

- The task requires only one or two operations
- The output is small and predictable
- No procedural looping is needed
- You need deterministic, repeatable behavior

### Use a Human When

- The decision requires judgment the agent cannot exercise
- The evidence is incomplete or conflicting
- The scope is unbounded or the goal is still forming

## The Context Budget

Context is scarce. Every included item must earn its place.

**Load context only when it materially improves execution.** This means:

- Don't dump the entire repo into every prompt.
- Don't include files "just in case" the agent might need them.
- If a workflow repeats, template it so context is predictable.
- If a workflow runs unattended, script it so context is irrelevant.

## Common Failure Modes

| Failure | Symptom | Fix |
|---------|---------|-----|
| Vibe coding | Accepting agent output without verification | Require receipts and validation |
| Phantom completion | Agent claims done but nothing works | Require runtime proof, not code claims |
| Scope creep | Agent refactors unrelated code | Bind scope explicitly in the prompt |
| Hallucinated APIs | Agent uses functions that don't exist | Require citation of existing code |
| Doc drift | Docs describe what was intended, not what is | Run drift reviews after every change |
| Proxy trust | "The tests pass" but tests test the wrong thing | Verify tests match acceptance criteria |

## Next

→ [`docs/vibe-coding-discipline.md`](vibe-coding-discipline.md)
