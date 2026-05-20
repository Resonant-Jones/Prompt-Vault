# Research-to-Spec Packet

Use this template to convert research findings into an implementable specification — without creating implementation files.

---

## Mode
Research and abstraction only. Do not create implementation files. Do not write code.

## Research Question
[What are we trying to extract, learn, or convert?]

## Sources

| Source | What it provides | Safety note |
|--------|-----------------|-------------|
| [Source A] | [Key contribution] | [Any redaction or caution needed] |
| [Source B] | [Key contribution] | [Any redaction or caution needed] |

## Grounding Rules
- Reason only within the provided sources unless explicitly allowed to search elsewhere.
- Do not assume missing implementation details.
- Do not invent APIs, files, components, claims, or release status.
- Cite every extracted pattern to its source.
- Mark uncertainty explicitly.
- Separate private source facts from public-safe abstractions.

## Extracted Patterns

| Pattern | Source | Public-safe abstraction |
|---------|--------|------------------------|
| [Pattern 1 — name and brief description] | [Source citation] | [How to express this without private details] |
| [Pattern 2 — name and brief description] | [Source citation] | [How to express this without private details] |

## Spec Recommendations

Based on the extracted patterns:

1. [Recommendation 1 — with rationale]
2. [Recommendation 2 — with rationale]
3. [Recommendation 3 — with rationale]

## Required Artifacts

- [ ] [Artifact type — e.g., "ADR for the new caching strategy"]
- [ ] [Artifact type — e.g., "Proof surface checklist for the migration"]
- [ ] [Artifact type — e.g., "Drift review of affected docs"]

## Redactions

What private details were removed or generalized?

| Removed/Generalized | Reason |
|---------------------|--------|
| [Item] | [Safety reason] |
| [Item] | [Safety reason] |

## Open Questions

- [Question 1]
- [Question 2]
- [Question 3]

## Handoff Brief for Coding Agent

[Compact instructions. Tell the agent: what to build, what sources to use, what to avoid, and what proof surface is required before claiming completion.]

```md
# Handoff

## Goal
[One sentence.]

## Sources
[Links to the spec and relevant docs.]

## Scope
[What to implement, what not to touch.]

## Proof Required
[What evidence proves this is done.]

## Safety
[Redactions, secrets, private details to avoid.]
```
