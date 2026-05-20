# Architecture Planning Prompt

Use this template when evaluating architecture with a coding agent — without allowing code changes.

---

## Mode
Planning only. Do not modify files. Do not generate patches. Do not write code.

## Objective
[The architecture question you need answered. One clear sentence.]

## Evidence Provided
- [Current-state docs — e.g., architecture overview, module descriptions]
- [Code summaries of relevant modules — e.g., "the auth module handles login, token refresh, and session management"]
- [Existing ADRs — list titles and links]
- [Known failure modes — e.g., "token refresh sometimes returns 401 incorrectly"]

## Analyze

### 1. Current State
What does the system actually do today? (Based on provided evidence only.)

### 2. Constraints
What must not change? What are the hard boundaries?

### 3. Desired State
What do you want the system to do?

### 4. Boundary Changes
What separation lines shift? What new interfaces are needed?

### 5. Risk Areas
What could break? What dependencies are affected? What assumptions are invalidated?

### 6. Migration Path
How do you get from current to desired? What are the intermediate states?

### 7. Validation Plan
How will you prove the migration worked? What proof surface is required?

## Output Contract

The agent must provide:

1. **Architecture summary** — The recommended design in a few paragraphs
2. **Decision options** — At least two alternatives with tradeoffs
3. **Recommended option** — With rationale
4. **Tradeoffs** — What you gain and what you lose
5. **Required ADRs** — Which decisions need formal recording
6. **Proof surface required** — What evidence is needed before any release claim
7. **Stale docs identified** — Which current-state docs will need updating

## Rules (Agent Must Follow)
- Reason only within the provided evidence.
- Do not invent APIs, files, components, or services not in the evidence.
- Cite the specific source for each architectural claim.
- Mark uncertainty explicitly when evidence is incomplete.
- Do not claim a design is "correct" — only that it is "recommended given the evidence."
