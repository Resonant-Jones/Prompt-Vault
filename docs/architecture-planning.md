# Architecture Planning

*How to evaluate architecture with a coding agent — without letting it touch the code.*

## The Planning-Only Contract

Architecture planning with a coding agent requires a hard boundary: **the agent must not modify files.** If the agent generates patches during planning, it has confused intent with implementation. You are now vibe coding.

Every architecture planning prompt must begin with:

```md
## Mode
Planning only. Do not modify files. Do not generate patches.
```

## When to Use Architecture Planning Mode

- You're considering a significant change and want to explore options
- You need to identify risks, boundaries, and migration paths
- You want the agent to reason about architecture using existing docs and code summaries
- You're preparing for an Architecture Decision Record (ADR)

## The Architecture Planning Prompt Structure

```md
# Architecture Planning Prompt

## Mode
Planning only. Do not modify files. Do not generate patches.

## Objective
[The architecture question you need answered.]

## Evidence Provided
- [Current-state docs]
- [Code summaries of relevant modules]
- [Existing ADRs]
- [Known failure modes]

## Analyze
1. Current state — what exists today
2. Desired state — what you want to achieve
3. Boundary changes — what separation lines shift
4. Risk areas — what could break
5. Migration path — how to get from current to desired
6. Validation plan — how to prove the migration worked

## Output Contract
- Architecture summary
- Decision options (at least two)
- Recommended option with tradeoffs
- Required ADRs
- Proof surface required before any release claim
```

See the full template: [`templates/architecture-planning-prompt.md`](../templates/architecture-planning-prompt.md)

## What Architecture Planning Must Do

### Distinguish Current from Desired

The agent must clearly separate:
- **Current state:** What the system actually does today (from docs and code)
- **Desired state:** What you want it to do
- **Gap:** The difference between them

### Identify Boundaries

Every architecture change shifts boundaries. The agent must identify:
- What modules/components are affected?
- What interfaces change?
- What separation lines are created or removed?

### Surface Risks

The agent must identify:
- What could break?
- What dependencies are affected?
- What assumptions are invalidated?
- What fallback patterns become dangerous?

### Propose Options, Not Just One Answer

Architecture is tradeoffs. The agent must present at least two options and explain the tradeoffs. A single recommendation without alternatives is a red flag.

## What Architecture Planning Must NOT Do

- Generate code or patches
- Modify files
- Claim a design is "correct" without evidence
- Invent components, APIs, or services not in the provided evidence
- Make release promises ("this will work in production")
- Skip the proof surface requirement

## Architecture Audits

An architecture audit is a special case of planning mode. It verifies:

- **Boundaries:** Are separation lines intact? Any leakage?
- **Dependencies:** Are dependency directions consistent with the architecture?
- **Fallbacks:** Are there dangerous fallback patterns?
- **Docs:** Do current-state docs match the code?

### Audit Prompt Structure

```md
## Mode
Planning only. Audit existing architecture.

## Verify
1. Boundary integrity
2. Dependency direction consistency
3. Fallback safety
4. Documentation alignment

## Evidence
[Current docs, code summaries, known issues]
```

## From Plan to ADR

After the planning session, convert the recommendation into an ADR:

1. State the decision context
2. Record the decision
3. Note the consequences (positive and negative)
4. Link to the planning evidence
5. Identify which docs must be updated

See: [`templates/adr-prompt.md`](../templates/adr-prompt.md)

## From ADR to Implementation

Only after the ADR is accepted should you open an implementation task:

1. Create a coding-agent task scoped to the ADR
2. Reference the ADR as the authoritative design
3. Require proof artifacts before closing
4. Run a drift review after implementation

## Next

→ [`docs/source-grounding.md`](source-grounding.md)
