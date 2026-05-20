# Codex Workflows

*A guide to using the Prompt-nomicon discipline with coding agents like Codex.*

## The Coding-Agent Contract

When you hand a task to a coding agent, you are entering a contract:

1. **You** provide: goal, scope, constraints, acceptance criteria, validation commands.
2. **The agent** provides: plan, diff, test results, evidence, risks, follow-up plan.
3. **You** verify: evidence matches criteria, no secrets, no scope creep, docs updated.

If either side breaks the contract, the loop is broken and you're vibe coding.

## Task Prompt Structure

Every coding-agent task should follow this structure:

```md
# Coding-Agent Task

## Goal
[What should change? One clear sentence.]

## Mode
[Implementation allowed / Planning only / Research only]

## Scope
Allowed:
- [Area A]
- [Area B]

Forbidden:
- Secrets or credentials
- Unrelated refactors
- Unverified public claims
- Private/internal context leakage

## Inputs
- [Relevant files/docs]
- [Known constraints]
- [Acceptance criteria]

## Required Behavior
- Make the smallest coherent change.
- Preserve idempotency.
- Prefer deterministic scripts for repetitive work.
- Do not invent files, APIs, or components.

## Validation
Run:
- [Command 1]
- [Command 2]

## Final Report
- Summary
- Files changed
- Tests/checks run
- Evidence
- Known limitations
- Follow-up
```

See the full template: [`templates/coding-agent-task.md`](../templates/coding-agent-task.md)

## Planning vs. Implementation

**Never mix planning and implementation in the same prompt.** If you're still figuring out the approach, use planning mode:

```md
## Mode
Planning only. Do not modify files. Do not generate patches.
```

If you've decided on an approach and want code changes, use implementation mode:

```md
## Mode
Implementation allowed. Only modify files within the approved scope.
```

## Handling Agent Output

### Red Flags

- Agent claims completion but validation commands weren't run
- Agent changed files outside the approved scope
- Agent invented functions, APIs, or components not in the codebase
- Agent made claims about "how the system works" without citing a source
- Agent output contains secrets, tokens, or credentials

### Required Verification

For every agent output:

1. **Read the diff.** Don't trust the summary.
2. **Run the validation commands yourself.**
3. **Check for secrets:** `grep -r "SECRET\|password\|token\|key"` on the diff.
4. **Verify scope:** Did the agent touch only the files you allowed?
5. **Write a receipt.** Capture what was tried, what happened, and what's uncertain.

## Batch vs. Interactive

### Interactive Mode (Recommended for Complex Tasks)

- Prompt → Agent responds with plan → You review → Agent implements → You verify
- Gives you a checkpoint between planning and execution
- Prevents vibe coding on large changes

### Batch Mode (For Well-Defined Tasks)

- Prompt with full spec → Agent implements → You verify
- Only appropriate when:
  - The scope is crystal clear
  - You've done this exact workflow before
  - The acceptance criteria are machine-verifiable

## Common Workflows

### Bug Fix

1. Prompt: describe the bug, provide reproduction steps, define expected behavior
2. Scope: the file(s) containing the bug, plus tests
3. Validation: reproduction steps no longer produce the bug, existing tests still pass
4. Receipt: reproduction output before and after

### Feature Addition

1. Prompt: describe the feature, provide acceptance criteria, define scope
2. Scope: the module(s) where the feature belongs, plus tests
3. Validation: acceptance criteria met, edge cases handled
4. Receipt: test output, manual verification steps

### Refactor

1. Prompt: describe the target state, define what must not change
2. Scope: the module(s) being refactored
3. Validation: all existing tests pass, behavior unchanged
4. Receipt: test output, diff summary

### Architecture Audit

1. Prompt: planning mode only, provide current docs and code summaries
2. Scope: analysis, no file changes
3. Validation: identified risks, boundary violations, stale docs
4. Receipt: audit findings, drift review

## Graduating Workflows

If you find yourself running the same workflow repeatedly:

- **Three times:** Template it. Save the prompt as a template with placeholders.
- **Unattended:** Script it. Write a script that invokes the agent with the template and validates output.
- **Continuous:** Service it. Build a service that monitors for the trigger condition and runs the workflow.

## Next

→ [`docs/architecture-planning.md`](architecture-planning.md)
