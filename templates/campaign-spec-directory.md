# Campaign/Spec Directory

Use this template to launch a multi-step project campaign. Copy the `TEMPLATE/` directory, rename it, and fill in each file.

---

## Directory Structure

```
CAMPAIGN_NAME/
  00-brief.md
  01-scope.md
  02-domain-model.md
  03-work-orders.md
  04-validation.md
  05-proof.md
  06-rollout.md
  receipts/
    receipt-template.md
```

## File Contents

### 00-brief.md

```md
# Campaign Brief: [Campaign Name]

## Goal
[Outcome in one sentence.]

## Why Now
[Risk, severity, core-loop relevance — what makes this urgent or important?]

## Sponsor
[Who owns this campaign?]

## Timeline
[Target dates or milestones.]

## Success Criteria
- [Criterion 1]
- [Criterion 2]
```

### 01-scope.md

```md
# Scope: [Campaign Name]

## In Scope
- [Area A]
- [Area B]

## Out of Scope
- [Area X — explicitly excluded]
- [Area Y — explicitly excluded]

## Boundaries
- [What interfaces must not change?]
- [What contracts must be preserved?]

## Dependencies
- [Depends on: System A, Team B, Decision C]
```

### 02-domain-model.md

```md
# Domain Model: [Campaign Name]

## Key Concepts
- [Concept A]: [Definition]
- [Concept B]: [Definition]

## Relationships
- [A relates to B because...]

## State Transitions
- [From state X to state Y via operation Z]

## Invariants
- [Rule 1 — must always be true]
- [Rule 2 — must always be true]
```

### 03-work-orders.md

```md
# Work Orders: [Campaign Name]

## WO-01: [Title]
- **Priority:** Critical / High / Medium / Low
- **Depends on:** [WO-00 or none]
- **Scope:** [What to change]
- **Acceptance:** [How to verify]
- **Receipt:** [Link when done]

## WO-02: [Title]
- **Priority:** Critical / High / Medium / Low
- **Depends on:** [WO-01]
- **Scope:** [What to change]
- **Acceptance:** [How to verify]
- **Receipt:** [Link when done]
```

### 04-validation.md

```md
# Validation: [Campaign Name]

## Validation Strategy
[How will we prove each work order is done?]

## Per Work Order

### WO-01
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Runtime proof captured
- [ ] Receipt written

### WO-02
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Runtime proof captured
- [ ] Receipt written

## Campaign-Level Validation
- [ ] All work orders complete
- [ ] End-to-end proof captured
- [ ] No regressions detected
- [ ] Drift review completed
```

### 05-proof.md

```md
# Proof: [Campaign Name]

## Campaign Claim
[What does the completed campaign prove?]

## Proof Surface
- [Link to receipt WO-01]
- [Link to receipt WO-02]
- [Link to end-to-end proof]
- [Link to regression test results]

## Limits
- [What this campaign does NOT prove]
- [Known gaps]
- [Deferred work]

## Freshness
- **Status:** [Live / Stale / Synthetic]
- **Date:** [YYYY-MM-DD]
```

### 06-rollout.md

```md
# Rollout: [Campaign Name]

## Rollout Plan
1. [Step 1 — e.g., "Deploy to staging"]
2. [Step 2 — e.g., "Run smoke tests"]
3. [Step 3 — e.g., "Gradual production rollout"]
4. [Step 4 — e.g., "Monitor for 24h"]

## Rollback Plan
- [Trigger condition]
- [Rollback steps]

## Monitoring
- [Metric to watch]
- [Alert threshold]

## Communication
- [Who needs to know?]
- [What channel?]
```

---

## How to Use This Template

1. Copy the `TEMPLATE/` directory and rename it to your campaign name.
2. Fill in `00-brief.md` first — it defines why this campaign exists.
3. Work through the files in order. Each builds on the previous.
4. Create a receipt for every work order. Store receipts in `receipts/`.
5. When all work orders are done, complete `05-proof.md` and `06-rollout.md`.
6. Run a drift review when the campaign closes.

## Campaign Derivation Rule

Don't create a campaign for every task. Derive campaigns from:

- **Audit findings** — Group related risks by severity and core-loop relevance
- **Risk matrix** — Severity × Likelihood × Platform area = campaign priority
- **Architecture decisions** — ADRs that require coordinated multi-step implementation

Group work by risk and loop impact — not by whatever file screamed loudest.
