# Loop Status Rubric

*How to determine whether a feature, task, or system is truly "done" — not just "the agent said so."*

## The Three Statuses

### Loop Closed ✅
The feature works end-to-end. All acceptance criteria are met. Evidence exists at every required tier.

**Minimum requirements for "Loop Closed":**
- [ ] All acceptance criteria verified
- [ ] Unit tests pass (happy path + error path + edge cases)
- [ ] Integration tests pass (if applicable)
- [ ] Runtime proof captured (Tier 1)
- [ ] Receipt written
- [ ] Drift review completed
- [ ] Docs updated or flagged stale

**Safe claim:** "Demonstrated working in [environment] on [date]. All acceptance criteria met."

---

### Partially Implemented ⚠️
Some criteria are met. Known gaps exist and are documented.

**Characteristics:**
- [ ] Core path works
- [ ] Acceptance criteria partially met
- [ ] Known gaps are documented as work orders
- [ ] Evidence exists for what works
- [ ] Limits are clearly stated

**Safe claim:** "Core path works. Known gaps: [list]. Not ready for release."

**Required artifact:** A list of remaining work orders with priorities.

---

### Missing / Critical Gap 🔴
Core functionality absent or broken. Cannot proceed.

**Characteristics:**
- [ ] Critical acceptance criterion not met
- [ ] Core path broken or absent
- [ ] No runtime proof exists
- [ ] Evidence of failure (not just absence of evidence)

**Safe claim:** "Not working. Critical gap: [describe]."

**Required artifact:** An issue filed with severity and category (see [`issue-taxonomy.md`](issue-taxonomy.md)).

---

## Status Determination Flow

```
Do all acceptance criteria pass?
├── YES → Do we have runtime proof?
│   ├── YES → Are docs updated?
│   │   ├── YES → LOOP CLOSED ✅
│   │   └── NO  → PARTIALLY IMPLEMENTED ⚠️ (docs stale)
│   └── NO  → PARTIALLY IMPLEMENTED ⚠️ (no runtime proof)
└── NO  → Is the core path working?
    ├── YES → PARTIALLY IMPLEMENTED ⚠️
    └── NO  → MISSING / CRITICAL GAP 🔴
```

## Red Flags That Signal "Not Really Closed"

- **"All tests pass"** — but no runtime proof
- **"It works on my machine"** — but no environment record or reproducible steps
- **"The code looks correct"** — code is not evidence of behavior
- **"The agent confirmed it's done"** — agent assertions are Tier 5 (weakest)
- **"We'll verify in production"** — production is not a test environment
- **"The docs are mostly right"** — "mostly" means stale

## Transitioning Between Statuses

| From | To | What's Needed |
|------|----|---------------|
| Missing | Partial | Core path working, evidence captured |
| Partial | Closed | Remaining criteria met, runtime proof, docs updated |
| Closed | Closed (stale) | Evidence older than 1 month or version changed — re-prove |
| Any | Missing | Regression broke something — file new issue, investigate |

## Campaign-Level Loop Status

For multi-step campaigns:

| Campaign Status | Meaning |
|-----------------|---------|
| **Not started** | No work orders completed |
| **In progress** | Some work orders done, gates being passed |
| **Implementation complete** | All work orders done, campaign-level validation pending |
| **Loop closed** | All work orders done, campaign proof captured, drift review done |
| **Released** | Rolled out, monitoring confirms stability |
