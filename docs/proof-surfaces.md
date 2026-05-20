# Proof Surfaces

*A claim without evidence is a rumor. A proof surface makes it a fact.*

## What Is a Proof Surface?

A **proof surface** is the collection of evidence that backs a specific claim about a software system.

If you claim "the auth module handles token refresh correctly," your proof surface might include:
- Passing unit tests for the refresh flow
- A runtime log showing a successful refresh
- A screenshot of the refresh endpoint returning 200
- A reproducible script that exercises the refresh path

A claim without a proof surface is not actionable. It is a rumor.

## The Proof Surface Contract

Every release claim must point to a proof surface. Every proof surface must be:

1. **Stated plainly** — What exactly does this prove?
2. **Environment-recorded** — Where was this tested?
3. **Versioned** — What commit, build, or date?
4. **Reproducible** — Can someone else run the same steps?
5. **Captured** — Are logs, screenshots, or artifacts linked?
6. **Limited** — What does this *not* prove?
7. **Freshness-marked** — Is this current, stale, or superseded?

## What Counts as Evidence?

### Strong Evidence

| Type | Example | Reproducible? |
|------|---------|---------------|
| Passing tests | `pytest tests/auth/ -v` output | Yes |
| Runtime logs | Log output from staging environment | With access |
| Command output | `curl` response, `ls` listing | Yes |
| Screenshots | UI state captured during test | Manual |
| Linked commits/PRs | Git history showing changes | Yes (immutable) |
| Reproducible scripts | `./verify-auth.sh` | Yes |

### Weak Evidence

| Type | Example | Why Weak |
|------|---------|----------|
| Code review | "I read the code and it looks right" | No execution |
| Agent claim | "The tests pass" (no output shown) | Unverified |
| Old proof | Test output from last month | Possibly stale |
| Synthetic proof | Generated mock data | Not runtime |

### What Is NOT Evidence

- An agent's assertion that something works
- A plan or design document
- Code that "should" work
- A passing test from a different version
- "It works on my machine"

## Proof Freshness States

Every proof must be marked with one of these states:

| State | Meaning | Action |
|-------|---------|--------|
| **Live** | Captured from current runtime, current version | Safe to rely on |
| **Stale** | Captured from current runtime, superseded version | Re-prove before relying |
| **Synthetic** | Generated from mock data or simulation | Useful but not sufficient alone |
| **Superseded** | Replaced by newer proof | Archive, do not use |

## The Receipt Format

Every proof should be captured as a receipt:

```md
# Receipt: [Claim]

## Claim
[What this proves.]

## Environment
- Host: [where]
- Version/commit: [hash]
- Date: [ISO date]
- Dependencies: [versions if relevant]

## Steps
1. [Command or action]
2. [Command or action]

## Observed Result
[Actual output.]

## Evidence
- [Link to log]
- [Screenshot]
- [Test output]

## Limits
- [What this does not prove]
- [Known gaps]

## Freshness
- Status: Live / Stale / Synthetic / Superseded
- Supersedes: [link to prior receipt, if any]
- Superseded by: [link to newer receipt, if any]
```

See the full template: [`receipts/template.md`](../receipts/template.md)

## Proof Surface Checklist

Before accepting any claim:

- [ ] Claim is stated plainly
- [ ] Environment is recorded
- [ ] Version/commit/date is recorded
- [ ] Steps are reproducible
- [ ] Output is captured
- [ ] Logs/screenshots/artifacts are linked
- [ ] Limits are stated
- [ ] Freshness status is marked
- [ ] Related docs were updated or flagged stale

See the full template: [`templates/proof-surface-checklist.md`](../templates/proof-surface-checklist.md)

## What Must Not Be Claimed Without Proof

| Do not claim... | Without... |
|-----------------|------------|
| Runtime support | Runtime proof (not just code changes) |
| Release readiness | Current proof + updated docs |
| Current-state truth | Current-state doc aligned with proof |
| User-visible behavior | Runtime proof in the target environment |
| Context availability | The context actually containing the material |

## Reproducibility Helpers

When a proof requires multiple steps, provide a helper script. But the script should **reproduce the proof**, not redesign the behavior.

```bash
#!/bin/bash
# verify-auth-refresh.sh
# Proves: Auth token refresh works in staging
# Environment: staging, commit abc123, 2026-05-19

echo "=== Step 1: Get initial token ==="
TOKEN=$(curl -s -X POST https://staging.example.com/auth/login ...)
echo "Token: $TOKEN"

echo "=== Step 2: Wait for expiry window ==="
sleep 5

echo "=== Step 3: Call protected endpoint ==="
curl -s -H "Authorization: Bearer $TOKEN" https://staging.example.com/api/protected
echo ""

echo "=== Proof complete ==="
```

## Next

→ [`docs/documentation-drift.md`](documentation-drift.md)
