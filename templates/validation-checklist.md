# Validation Checklist

Use this checklist to assess the completeness of a feature, task, or system component.

---

## Feature/Task: [Name]

### Loop Status

- [ ] **Loop closed** — Feature works end-to-end, all acceptance criteria met
- [ ] **Partially implemented** — Some criteria met, known gaps remain
- [ ] **Missing / critical gap** — Core functionality absent or broken

### Evidence by Layer

#### Unit Tests
- [ ] Happy path tested
- [ ] Error path tested
- [ ] Edge cases tested
- [ ] Test output captured and linked

#### Integration Tests
- [ ] Component integrates with dependencies
- [ ] Contract boundaries verified
- [ ] Test output captured and linked

#### Runtime Proof
- [ ] Feature demonstrated in a running environment
- [ ] Logs show expected behavior
- [ ] Performance is within acceptable limits (if applicable)

#### Manual Verification
- [ ] UI/UX verified (if applicable)
- [ ] Error messages are clear and actionable
- [ ] Documentation matches observed behavior

#### Negative Cases
- [ ] Invalid input handled gracefully
- [ ] Missing dependencies handled gracefully
- [ ] Timeout/network failure handled gracefully
- [ ] Concurrency/race conditions considered

### Claims Audit

- [ ] No release claim without runtime proof
- [ ] No implementation claim without diff or artifact
- [ ] No runtime claim without runtime evidence
- [ ] No current-state claim without aligned docs
- [ ] No "complete" claim with known gaps unstated

### Safety Checks

- [ ] No secrets or credentials in code
- [ ] No sensitive data logged
- [ ] Error messages do not leak internal state
- [ ] Permissions/access control verified

### Documentation

- [ ] Current-state docs updated
- [ ] ADRs written (if architecture changed)
- [ ] Receipt written and linked
- [ ] Drift review completed

### Sign-Off

- [ ] All acceptance criteria verified
- [ ] Known limitations stated
- [ ] Next steps defined
