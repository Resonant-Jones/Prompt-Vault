# Receipts

Receipts are durable artifacts that record what was attempted, what happened, and what remains uncertain.

## Why Receipts

A receipt is not "success." A receipt is honesty. It captures the verification event so that:

- You can remember what you verified and how
- Team members know what was proven
- Future-you can reproduce the proof
- Claims don't persist after evidence rots

## Receipt Storage

Store receipts here with descriptive filenames:

```
receipts/
  auth-token-refresh-staging-2026-05-19.md
  api-latency-benchmark-v2.1.md
  fix-null-pointer-issue-42.md
```

Link receipts from:
- PR descriptions
- Release notes
- ADRs (as evidence)
- Campaign proof sections
- Drift reviews

## Template

See [`template.md`](template.md) for the receipt template.
