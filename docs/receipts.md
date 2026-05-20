# Receipts

*A receipt is not "success." A receipt is honesty — a durable record of what was attempted, what happened, and what remains uncertain.*

## Why Receipts Matter

Coding agents produce output. Humans verify output. But verification itself is an event that fades from memory. Without a receipt:

- You can't remember what you verified or how
- Team members don't know what was proven
- Future-you can't reproduce the proof
- Claims persist long after the evidence has rotted

A receipt captures the verification event as a durable artifact.

## What a Receipt Is

A receipt documents:

1. **What was claimed** — The specific assertion being verified
2. **What environment** — Where the verification happened
3. **What steps** — The exact commands or actions
4. **What happened** — The observed result
5. **What evidence** — Logs, screenshots, artifacts
6. **What's missing** — Limits and known gaps
7. **When and where** — Date, version, commit

A receipt does **not** need to show success. A receipt showing failure is valuable — it prevents someone else from repeating the same failed approach.

## Receipt Template

```md
# Receipt: [Short Title]

## Claim
[What this receipt proves or disproves, in one sentence.]

## Environment
- **Host:** [machine/environment name]
- **Version/commit:** [git hash or version]
- **Date:** [YYYY-MM-DD]
- **Dependencies:** [versions if relevant]

## Steps
1. [Command or action — be exact]
2. [Command or action — be exact]
3. [...]

## Observed Result
[What actually happened. Paste output, describe behavior, note surprises.]

## Evidence
- [Link to full log]
- [Screenshot]
- [Test output file]
- [Terminal recording]

## Limits
- [What this receipt does NOT prove]
- [Known gaps in coverage]
- [Edge cases not tested]

## Freshness
- **Status:** Live / Stale / Synthetic / Superseded
- **Supersedes:** [link to prior receipt, if any]
- **Superseded by:** [link to newer receipt, if any]
```

See the full template: [`receipts/template.md`](../receipts/template.md)

## Receipt Types

### Verification Receipt
Confirms that a specific behavior works. "Auth token refresh succeeds in staging."

### Failure Receipt
Documents a failed attempt. "Token refresh fails when the refresh token is expired — returns 401 instead of 400."

### Benchmark Receipt
Records performance data. "API responds in under 200ms with 100 concurrent users."

### Audit Receipt
Records findings from an audit or review. "Architecture audit: 3 boundary violations found, 0 secrets in codebase."

### Regression Receipt
Confirms a bug is fixed and won't return. "Issue #42: null pointer on empty input — fixed, test added."

## Receipt Storage

Store receipts in a `receipts/` directory. Link receipts from:

- PR descriptions
- Release notes
- ADRs (as evidence)
- Campaign proof sections
- Drift reviews

## The Receipt Discipline

For every implementation task:

1. **Before starting:** Create an empty receipt file with the claim you intend to prove.
2. **During verification:** Fill in the steps and observed result as you go.
3. **After verification:** Link evidence, mark limits, set freshness.
4. **In your PR:** Include a link to the receipt.

If you skip the receipt, you're vibe coding.

## Validating Receipts

A valid receipt:

- [ ] Has a clear, falsifiable claim
- [ ] Records the environment and version
- [ ] Lists exact, reproducible steps
- [ ] Shows actual output (not a summary)
- [ ] States what it does not prove
- [ ] Is marked with a freshness status
- [ ] Is linked from the relevant ADR, PR, or release note

## Next

→ [`templates/coding-agent-task.md`](../templates/coding-agent-task.md) — put this into practice
