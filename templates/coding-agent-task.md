# Coding-Agent Task Prompt

Use this template when assigning a bounded implementation task to a coding agent.

---

## Mode
Implementation allowed. Only modify files within the approved scope.

## Goal
[Describe the user-visible or developer-visible outcome in one or two sentences.]

## Scope

**Allowed:**
- [Area A — file, module, directory, or subsystem]
- [Area B]

**Forbidden:**
- Secrets or credentials
- Unrelated refactors
- Unverified public claims
- Private/internal context leakage
- [Any additional restrictions]

## Inputs
- [Relevant files/docs the agent should read]
- [Known constraints — e.g., "must work with Python 3.10+"]
- [Acceptance criteria — e.g., "the endpoint returns 200 for valid input"]

## Constraints
- The task must be idempotent (running it twice produces the same result).
- Do not bind fixed ports without checking availability.
- Do not commit secrets or credentials.
- Keep generated artifacts in version control or timestamped artifact folders.
- Make the smallest coherent change — no unrelated refactors.

## Acceptance Criteria
- [ ] [Criterion 1 — specific and verifiable]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

## Validation
Run these commands and report the output:

```bash
# [Command 1]
# [Command 2]
```

## Required Final Report

The agent must provide:

1. **Summary** — What was done and why
2. **Files changed** — List of modified/created/deleted files
3. **Tests/checks run** — Command output
4. **Evidence** — Screenshots, logs, or other proof
5. **Known limitations** — What was not done or not proven
6. **Next-step plan** — What should happen next

## Safety Checks (Agent Must Perform)
- [ ] No secrets or credentials in the diff
- [ ] No files modified outside approved scope
- [ ] No hallucinated APIs, files, or components
- [ ] Idempotency verified (task can be re-run safely)
