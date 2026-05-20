# Rollout: [Campaign Name]

## Rollout Plan
1. **[Step 1]** — [e.g., "Deploy to staging environment"]
   - **Validation:** [What to check]
   - **Rollback:** [How to undo if this step fails]
2. **[Step 2]** — [e.g., "Run smoke tests in staging"]
   - **Validation:** [What to check]
   - **Rollback:** [How to undo]
3. **[Step 3]** — [e.g., "Gradual production rollout (10% → 50% → 100%)"]
   - **Validation:** [What to check at each percentage]
   - **Rollback:** [How to undo]
4. **[Step 4]** — [e.g., "Monitor for 24 hours"]
   - **Validation:** [What to check]
   - **Rollback:** [Trigger conditions for rollback]

## Rollback Triggers
- [Condition 1 — e.g., "Error rate exceeds 1%"]
- [Condition 2 — e.g., "P95 latency increases by > 50%"]
- [Condition 3 — e.g., "User-reported issues"]

## Rollback Procedure
1. [Step 1]
2. [Step 2]
3. [Step 3]

## Monitoring

| Metric | Baseline | Alert Threshold | Alert Channel |
|--------|----------|-----------------|---------------|
| [Metric A] | [Current value] | [When to alert] | [Where] |
| [Metric B] | [Current value] | [When to alert] | [Where] |
| [Metric C] | [Current value] | [When to alert] | [Where] |

## Communication
- **Stakeholders:** [Who needs to know]
- **Channel:** [Slack channel, email list, status page]
- **Pre-rollout notice:** [When and what to communicate before rollout]
- **Post-rollout notice:** [When and what to communicate after rollout]

## Rollout Log
| Date | Action | Result | Operator |
|------|--------|--------|----------|
| [YYYY-MM-DD] | [What was done] | [Outcome] | [Name] |
