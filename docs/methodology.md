# Methodology

*The Prompt-nomicon methodology: how to turn fuzzy goals into bounded, evidence-backed agent tasks.*

## The Core Loop

```
Prompt → Task → Spec → Execution → Receipt → Drift Review
```

Each stage produces a durable artifact. No stage claims the authority of a later stage. This is the backbone of the discipline.

### 1. Prompt

**What it is:** The initial framing that defines mode, scope, allowed operations, and expected output *before* the model acts.

**Key rule:** A prompt that doesn't specify mode is ambiguous. The model may plan, implement, or hallucinate — and you won't know which.

**Artifact:** A mode-tagged prompt document (see [`templates/coding-agent-task.md`](../templates/coding-agent-task.md)).

### 2. Task

**What it is:** The scoped, bounded unit of work derived from the prompt.

**Key rule:** Separate plan from implementation. Planning prompts should explicitly forbid file mutation and code generation. If the task is analytical, the agent should not touch the repo.

**Artifact:** A task definition with scope boundaries, constraints, and acceptance criteria.

### 3. Spec

**What it is:** The evidence-bound analysis that defines what must be true before, during, and after execution.

**Key rule:** Reason only within evidentiary space. No hallucinated APIs, files, or components. Every claim must be traceable to a provided source or a planned verification step.

**Artifact:** A spec document or ADR (see [`templates/adr-prompt.md`](../templates/adr-prompt.md)).

### 4. Execution

**What it is:** The bounded implementation step. Code changes, config updates, script runs.

**Key rules:**
- Make the smallest coherent change.
- Preserve idempotency.
- Prefer deterministic scripts for repetitive work.
- Do not invent files, APIs, or components.
- Do not commit secrets.
- Check for security and privacy issues after the diff.

**Artifact:** A diff, a set of changed files, and a validation report.

### 5. Receipt

**What it is:** A durable artifact that records what was attempted, what happened, and what remains uncertain.

**Key rule:** A receipt is not "success." A receipt is honesty. Record the environment, the steps, the observed result, the evidence, and the limits.

**Artifact:** A receipt document (see [`receipts/template.md`](../receipts/template.md)).

### 6. Drift Review

**What it is:** The check that docs, proofs, and claims still align after changes.

**Key rule:** Every doc should reveal whether it is current, stale, or superseded. Do not let documentation become "marketing memory foam."

**Artifact:** A drift review document (see [`templates/documentation-drift-review.md`](../templates/documentation-drift-review.md)).

## Foundational Patterns

### Evidence-Bounded Reasoning

**Problem:** AI agents invent APIs, files, components, or "probably true" architecture.

**Solution:** Restrict reasoning to supplied evidence. Forbid external facts unless allowed. Require citations for reasoning steps.

**Principle:** "No uncited implementation claim may be treated as true."

### Proof Surface Before Promise

**Problem:** Teams claim "done" based on code changes rather than demonstrated behavior.

**Solution:** Require a proof artifact, current-state update, and optionally a minimal reproducibility helper before any release claim.

**Principle:** "A release claim must point to a proof surface."

### Plan / Implement / Prove / Promise Separation

**Problem:** AI-assisted coding blurs intent, execution, validation, and marketing claims.

**Solution:** Planning prompts forbid repo mutation. Proof notes distinguish live evidence, stale proof, code-level fixes, and re-proof needs.

**Principle:** "Do not let a plan pretend to be an implementation."

### Context Budgeting

**Problem:** Agents drown in irrelevant files, schemas, examples, and tool output.

**Solution:** Treat context as a scarce systems resource. Load only what materially improves execution.

**Principle:** "Every included context item must earn its place."

### Procedural Work Escalation

**Problem:** Models simulate repetitive operations badly (looping, filtering, aggregation, formatting over many records).

**Solution:** For repetitive work, the model should write or trigger procedural execution instead of doing it manually in prose.

**Principle:** "Use the model for judgment; use code for repetition."

### Stability Graduation

**Problem:** Repeated ad hoc prompts remain fragile forever.

**Solution:** Successful repeated workflows graduate into scripts, skills, or first-class services.

**Principle:** "If you do it three times, template it; if it runs unattended, script it."

### Drift-Aware Documentation

**Problem:** Docs lag implementation, proofs, or release reality.

**Solution:** Dev logs and drift reviews explicitly mark stale current-state docs, old audit snapshots, and missing fresh test runs.

**Principle:** "Every doc should reveal whether it is current, stale, or superseded."

## The Anti-Vibe-Coding Contract

"Vibe coding" is when you prompt an agent, accept the output, and move on without verification. The Prompt-nomicon replaces vibe coding with a contract:

1. **You** define the scope and acceptance criteria.
2. **The agent** implements within the scope and reports evidence.
3. **You** verify the evidence against the criteria.
4. **Both** update the docs to reflect what was actually proven.

If any step is skipped, the loop is broken and you're vibe coding again.

## Next

→ [`docs/truth-surfaces.md`](truth-surfaces.md) (if it exists) or [`docs/ai-assisted-coding.md`](ai-assisted-coding.md)
