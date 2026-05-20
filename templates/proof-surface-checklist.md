# Proof-Surface Checklist

Use this checklist to verify that a claim has sufficient evidence before it is treated as fact.

---

## Claim

- [ ] The claim is stated plainly and is falsifiable
- [ ] The claim does not exceed what the evidence supports

## Environment

- [ ] Host/machine/environment is recorded
- [ ] Version, commit hash, or build number is recorded
- [ ] Date of verification is recorded
- [ ] Relevant dependency versions are recorded (if applicable)

## Reproducibility

- [ ] Steps are listed in order
- [ ] Steps are exact (commands, not descriptions)
- [ ] Another person could follow the steps and get the same result

## Evidence Capture

- [ ] Output is captured (not summarized)
- [ ] Logs are linked or attached
- [ ] Screenshots are linked or attached (if visual)
- [ ] Terminal recordings are linked (if interactive)

## Limits

- [ ] What this proof does NOT cover is stated
- [ ] Known gaps are listed
- [ ] Edge cases not tested are listed
- [ ] Negative cases are addressed (where relevant)

## Freshness

- [ ] Status is marked: Live / Stale / Synthetic / Superseded
- [ ] Superseded proofs are linked (if applicable)
- [ ] The proof is still reproducible (if marked Live)

## Documentation

- [ ] Related current-state docs were updated (or flagged stale)
- [ ] Related ADRs reference this proof (if applicable)
- [ ] The receipt is linked from the PR or release note

## Sign-Off

- [ ] Reviewer has independently verified the claim (if required)
- [ ] The claim is not a release promise without current proof + updated docs
