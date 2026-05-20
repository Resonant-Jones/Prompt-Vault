# Issue Taxonomy

*How to classify problems found during validation — so they get the right response.*

## Severity Levels

### Critical
**Definition:** Core functionality broken. System unusable. Data loss or corruption.

**Response:** Drop everything. Fix before any other work.

**Examples:**
- Auth flow broken — no one can log in
- Data corruption on write
- Security vulnerability with known exploit

---

### High
**Definition:** Major feature broken. Significant user impact. No workaround available.

**Response:** Fix in current sprint. Escalate if not resolved within 24 hours.

**Examples:**
- Token refresh fails intermittently
- Search returns incomplete results
- API returns 500 for valid requests

---

### Medium
**Definition:** Feature partially broken. Workaround exists. Moderate user impact.

**Response:** Schedule in current or next sprint.

**Examples:**
- UI renders incorrectly on one browser
- Optional feature times out under load
- Error message is unhelpful but the operation still works

---

### Low
**Definition:** Cosmetic issue. Edge case. Minimal user impact.

**Response:** Backlog. Fix when convenient.

**Examples:**
- Typo in a log message
- Missing hover state on a button
- Unused import in a module

---

## Issue Categories

| Category | Description | Example |
|----------|-------------|---------|
| **Correctness** | Code produces wrong results | Auth allows login with wrong password |
| **Reliability** | Code fails under certain conditions | Race condition causes intermittent 500s |
| **Performance** | Code is too slow or uses too many resources | API endpoint takes 5 seconds to respond |
| **Security** | Vulnerability or unsafe practice | SQL injection, exposed secrets |
| **Boundary** | Separation line violated | Frontend directly accesses database |
| **Drift** | Docs don't match reality | README references removed endpoint |
| **Completeness** | Missing functionality | Feature advertised but not implemented |
| **Idempotency** | Operation not safe to repeat | Running migration twice corrupts data |

## Validation Loop Status

| Status | Meaning | Action |
|--------|---------|--------|
| **Loop Closed** | Feature works end-to-end, all criteria met | Move to proof surface |
| **Partially Implemented** | Some criteria met, known gaps exist | Create work orders for gaps |
| **Missing / Critical Gap** | Core functionality absent or broken | Escalate, do not ship |

## Risk Matrix Derivation

When multiple issues are found, group them by:

1. **Severity** — Critical → High → Medium → Low
2. **Likelihood** — Will users hit this? Often / Sometimes / Rarely
3. **Core-loop relevance** — Does this affect the primary user workflow?
4. **Existing control** — Is there already a safeguard or workaround?

Derive campaigns from high-severity, high-likelihood clusters that affect the core loop and lack existing controls.

**Principle:** Group work by risk and loop impact, not by whatever file screamed loudest.
