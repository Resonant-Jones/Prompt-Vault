# Architecture Decision Records

ADRs capture significant architecture decisions, their context, consequences, and relationship to the broader documentation corpus.

## What Makes a Good ADR

An ADR should:
- Describe a specific, consequential decision
- Explain the context that forced the decision
- State the options considered and why they were rejected
- Record both positive and negative consequences
- Link to the evidence that supports the decision
- Identify which current-state docs depend on or relate to this decision
- Define what future changes would make the ADR stale

## ADRs vs. Architecture Docs

**ADRs sit beside, not above, the main architecture corpus.** They capture *decisions*. Architecture docs capture *the system as it is*. An ADR says "we chose X because Y." An architecture doc says "the system uses X in this way."

When they conflict, the architecture doc should be updated — not the ADR. The ADR is a historical record of the decision. If the decision was wrong, write a new ADR that supersedes it.

## ADR Lifecycle

```
Proposed → Accepted → Superseded / Deprecated
```

- **Proposed:** Under discussion. Not yet agreed upon.
- **Accepted:** Agreed and implemented (or planned for implementation).
- **Superseded:** Replaced by a newer ADR. Link to the replacement.
- **Deprecated:** The decision is no longer relevant (e.g., the system it applied to was removed).

## Index

See [`index.md`](index.md) for the list of all ADRs.

## Template

See [`template.md`](template.md) for the ADR template.
