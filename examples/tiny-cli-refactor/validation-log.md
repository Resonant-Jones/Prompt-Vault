# Validation Log: Tiny CLI Refactor

## Feature: greet.py `--name` flag

### Loop Status
- [x] **Loop closed** — All acceptance criteria met

### Evidence by Layer

#### Unit Tests
- [x] Happy path tested — `test_default_greeting`
- [x] Named greeting tested — `test_named_greeting`
- [x] Error path tested — `test_missing_name_value`
- [x] Test output captured — see `proof.md`

#### Runtime Proof
- [x] Demonstrated in local environment — all three manual runs succeeded
- [x] Output captured in `proof.md`

#### Negative Cases
- [x] Missing `--name` value handled — argparse error message + non-zero exit
- [x] Backward compatible — no flag = default behavior preserved

### Claims Audit
- [x] No release claim without runtime proof
- [x] No implementation claim without diff
- [x] No "complete" claim with known gaps unstated — limits documented in `proof.md`

### Safety Checks
- [x] No secrets or credentials
- [x] No sensitive data

### Documentation
- [x] ADR written — `adr.md`
- [x] Proof captured — `proof.md`
- [x] Drift review completed — `drift-review.md`

### Known Limitations
- Not tested on Python 3.10 or 3.12
- Unicode names not tested
