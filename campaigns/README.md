# Campaigns

Campaigns are multi-step projects derived from audit severity and core-loop relevance.

## When to Create a Campaign

Create a campaign when:

- An audit surfaces a cluster of related risks
- An ADR requires coordinated multi-step implementation
- A regression matrix identifies systemic issues across components

Do **not** create a campaign for every task. Group work by risk and loop impact.

## Campaign Structure

```
CAMPAIGN_NAME/
  00-brief.md        — Why this campaign exists
  01-scope.md        — What's in and out of scope
  02-domain-model.md — Key concepts and relationships
  03-work-orders.md  — Ordered, dependent tasks
  04-validation.md   — How to verify each work order
  05-proof.md        — Campaign-level proof surface
  06-rollout.md      — Deployment and monitoring plan
  receipts/          — Receipts for each work order
```

## Derivation Rules

| Input | Campaign Trigger |
|-------|-----------------|
| Risk matrix (Severity × Likelihood) | High-severity, high-likelihood clusters |
| Audit findings | Related boundary violations or gaps |
| ADR with multi-step consequences | ADRs that can't be done in one task |
| Regression matrix | Risks spanning multiple platform areas |

## Active Campaigns

*None yet — this is a fresh repo. Create your first campaign from the `TEMPLATE/` directory.*

## Completed Campaigns

*None yet.*

## Template

See [`TEMPLATE/`](TEMPLATE/) for the campaign template directory.
