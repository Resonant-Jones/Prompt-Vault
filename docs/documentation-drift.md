# Documentation Drift

*Docs that lie are worse than no docs. Here's how to keep them honest.*

## What Is Documentation Drift?

**Documentation drift** is the gap between what docs say and what the system actually does. It happens because:

- Code changes but docs don't
- Proofs are captured but current-state docs aren't updated
- ADRs are written but never marked superseded
- READMEs describe intent, not reality

The result: developers trust docs that are wrong. Decisions are based on fiction. Proofs claim things that are no longer true.

## The Drift Prevention Contract

Every doc in your repo should reveal whether it is:

- **Current** — Matches the latest proof and implementation
- **Stale** — Predates changes that affect its claims
- **Superseded** — Replaced by a newer doc or decision
- **Snapshot** — Frozen point-in-time assessment, not living truth

If a doc doesn't state its freshness, assume it's stale.

## When to Run a Drift Review

Run a drift review:

1. **After every implementation task** — Code changed; do docs still match?
2. **After capturing new proof** — Proof changed; do docs reflect the new evidence?
3. **Before a release** — All docs must be current before claiming release readiness
4. **When you discover stale docs** — Flag them immediately; don't let them rot

## The Drift Review Process

### 1. Identify Changed Evidence

What new proof, implementation, or failure exists since the last review?

### 2. Check Affected Docs

For each doc that might be affected:

- Current-state docs — Do they describe the live system?
- ADRs — Are any decisions now outdated?
- READMEs — Are commands, paths, and claims still valid?
- Proof artifacts — Are they still reproducible?
- Audit snapshots — Are they marked as frozen?

### 3. Classify Drift

| Drift type | Example | Action |
|------------|---------|--------|
| **Current-state doc stale** | Architecture doc references removed module | Update or mark stale |
| **ADR stale** | Decision predates a conflicting newer decision | Mark superseded, link to replacement |
| **README stale** | Setup instructions fail | Update |
| **Proof superseded** | Test output from old version | Re-prove or archive |
| **Audit snapshot outdated** | Audit from before major refactor | Mark as snapshot only |

### 4. Apply Fixes

- Update the doc to match current evidence
- If you can't update it now, **mark it stale explicitly**
- Link to the reason it's stale (commit, issue, newer doc)
- Don't delete old docs — mark them superseded with a pointer

### 5. Record the Review

Use the drift review template to record what you checked and what you found.

## Drift Review Template

```md
# Documentation Drift Review

## Date
[ISO date]

## Trigger
[What changed? Implementation task, new proof, release prep?]

## Changed Evidence
- [New proof, implementation, or failure]

## Docs Checked
- [Doc A] — Status: Current / Stale / Superseded
- [Doc B] — Status: Current / Stale / Superseded
- [Doc C] — Status: Current / Stale / Superseded

## Drift Found
- [ ] Current-state doc stale — [which one?]
- [ ] ADR stale — [which one?]
- [ ] README stale — [which one?]
- [ ] Proof superseded — [which one?]
- [ ] Audit snapshot outdated — [which one?]

## Required Updates
- [ ] [Action item]
- [ ] [Action item]

## Safe Claim After Review
[What can now be claimed, given the evidence and updated docs?]
```

See the full template: [`templates/documentation-drift-review.md`](../templates/documentation-drift-review.md)

## Anti-Patterns

### "I'll Update the Docs Later"

Later never comes. If you can't update now, mark the doc stale with a date and reason. Stale is honest. Wrong is dangerous.

### "The Code Is the Documentation"

Code shows what *does* happen. Docs show what *should* happen and *why*. Both are necessary. Code without docs is archaeology.

### "It's Just a Small Change"

Small changes cause drift too. A one-line config change can invalidate an entire ADR. Run a quick drift check: "Which docs reference the thing I changed?"

### "The Old Doc Is Still Useful Context"

Then preserve it — but mark it as a snapshot, not as current truth. "This doc describes the system as of 2025-03. See [newer doc] for current state."

## Making Drift Reviews Routine

- Add a drift review step to your PR template
- Run a drift review as part of your release checklist
- If you find three stale docs, schedule a doc audit campaign
- Automate freshness checks where possible (e.g., last-modified dates vs. last-deploy dates)

## Next

→ [`docs/receipts.md`](receipts.md)
