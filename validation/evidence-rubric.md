# Evidence Rubric

*How to grade evidence — from "live runtime proof" to "someone said it works."*

## Evidence Tiers

### Tier 1: Live Runtime Proof (Strongest)
Evidence captured from a running system at the current version.

**Characteristics:**
- Reproducible steps
- Actual output (not a summary)
- Version/commit recorded
- Environment recorded
- Date recorded
- Can be reproduced by another person with the same steps

**Examples:**
- `curl` output from a staging endpoint
- Test suite output with timestamp and commit hash
- Screenshot of UI with visible version number
- Terminal recording of a workflow

**Safe claim:** "Demonstrated in this environment on this date."

---

### Tier 2: Automated Test Evidence
Evidence from automated checks that pass consistently.

**Characteristics:**
- Tests are version-controlled
- Output includes pass/fail for each case
- Tests cover both happy paths and error paths
- Tests can be run with a single command

**Examples:**
- `pytest -v` output
- CI pipeline logs
- Linter output

**Safe claim:** "Tested under these conditions."

**Limitation:** Tests alone do not prove runtime behavior in a real environment.

---

### Tier 3: Code-Level Evidence
Evidence that code was changed but not yet verified at runtime.

**Characteristics:**
- A diff exists
- The code compiles/parses
- No runtime behavior has been observed

**Examples:**
- Git diff
- Pull request
- Code review approval

**Safe claim:** "Implemented in code, not yet proven."

**Limitation:** Code can compile and still be wrong. Code-level evidence is not proof of behavior.

---

### Tier 4: Synthetic Evidence
Evidence generated from mock data, simulations, or test doubles.

**Characteristics:**
- Does not use real data or real dependencies
- May not reflect production behavior
- Useful for early validation but insufficient alone

**Examples:**
- Mock-based unit tests
- Simulated load test data
- Generated screenshots

**Safe claim:** "Demonstrated with synthetic data."

**Limitation:** Synthetic evidence must be supplemented with runtime proof before release claims.

---

### Tier 5: Assertion (Weakest)
A statement without supporting evidence.

**Characteristics:**
- No output captured
- No reproducible steps
- No environment or version recorded

**Examples:**
- "I tested it and it works"
- "The code looks correct"
- "The agent said it's done"

**Safe claim:** None. Assertions are not evidence.

---

## Evidence Sufficiency Rules

| Claim Type | Minimum Evidence Tier Required |
|------------|-------------------------------|
| "I have a plan" | Tier 5 (Assertion) — a plan is a proposal |
| "I changed the code" | Tier 3 (Code-Level) — a diff |
| "The tests pass" | Tier 2 (Test Evidence) — test output |
| "It works in staging" | Tier 1 (Runtime Proof) — runtime output |
| "It's ready for production" | Tier 1 + updated docs + drift review |
| "Users can use it now" | Tier 1 + current docs + monitoring |

## Evidence Freshness Decay

| Age | Status | Action |
|-----|--------|--------|
| < 1 week, same version | Fresh | Reliable |
| < 1 month, same version | Probably fresh | Quick verification recommended |
| > 1 month, or version changed | Possibly stale | Re-prove before relying |
| Version unknown | Unreliable | Do not use |
