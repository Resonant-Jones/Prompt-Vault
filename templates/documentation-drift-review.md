# Documentation Drift Review

Use this template to check whether docs, proofs, and claims still align after changes.

---

## Review Metadata

- **Date:** [YYYY-MM-DD]
- **Trigger:** [Implementation task, new proof captured, release prep, audit finding]
- **Reviewer:** [Name or role]

## Changed Evidence

What new proof, implementation, or failure exists since the last review?

- [Change 1 — e.g., "Auth module refactored to use JWT"]
- [Change 2 — e.g., "Token refresh endpoint returns 401 under load"]

## Docs Checked

| Document | Status | Notes |
|----------|--------|-------|
| [Doc A] | Current / Stale / Superseded / Snapshot | [Brief note] |
| [Doc B] | Current / Stale / Superseded / Snapshot | [Brief note] |
| [Doc C] | Current / Stale / Superseded / Snapshot | [Brief note] |

## Drift Found

- [ ] **Current-state doc stale** — [Which doc? What's wrong?]
- [ ] **ADR stale** — [Which ADR? What changed?]
- [ ] **README stale** — [Which README? What's wrong?]
- [ ] **Proof superseded** — [Which proof? Replaced by what?]
- [ ] **Audit snapshot outdated** — [Which audit? What's changed since?]
- [ ] **No drift found** — All docs align with current evidence

## Required Updates

- [ ] [Action 1 — e.g., "Update architecture-overview.md to reflect new auth flow"]
- [ ] [Action 2 — e.g., "Mark ADR-003 as superseded by ADR-007"]
- [ ] [Action 3 — e.g., "Re-prove token refresh in staging with new JWT implementation"]

## Docs Marked Stale (Could Not Update Now)

| Document | Reason | Planned Update |
|----------|--------|----------------|
| [Doc] | [Why stale] | [When it will be updated] |

## Safe Claims After Review

Given the current evidence and updated docs, what can now be claimed?

- [Claim 1 — with evidence reference]
- [Claim 2 — with evidence reference]

## What Must NOT Be Claimed

- [Claim that lacks current proof]
- [Claim that predates a known change]

## Next Steps

- [ ] Complete required updates (link to task)
- [ ] Schedule next drift review (date or trigger condition)
- [ ] File tasks for any gaps found
