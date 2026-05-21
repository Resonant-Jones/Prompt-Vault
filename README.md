# The Prompt-nomicon

## Vibe Coding Secrets from the Crypt 🕯️💻📜

*A field manual for surviving AI-assisted software development without summoning architectural horrors from beneath the repo floorboards.*

The Prompt-nomicon is a practical guide to working with coding agents, AI assistants, and prompt-driven development systems in ways that remain structured, testable, and sane. It focuses on the operational realities of AI-assisted engineering: task design, repo scaffolding, specification discipline, validation workflows, context preservation, and keeping your automation stack from free-climbing the cathedral walls at 2:13 AM.

This is not a collection of “one weird prompt tricks.”  
It is a methodology for building systems where evidence matters, decisions remain traceable, and implementation claims can survive contact with reality.

Yes, there are rituals.  
But the rituals mostly involve receipts, architecture notes, validation checklists, and refusing to let a coding agent rewrite your auth layer because it “felt cleaner.”

The Prompt-nomicon exists for developers working with:

- Coding agents (Codex, Cursor, Copilot, Claude Code, etc.)
- Repo-aware assistants
- Local LLM tooling
- Multi-agent workflows
- AI-assisted architecture and scaffolding pipelines
- Any environment where model quality depends heavily on the structure surrounding the model

Inside you'll find reusable templates, operational patterns, repo-hardening practices, task structures, proof surfaces, drift-detection habits, and anti-chaos containment wards for turning vague intent into implementation-ready execution.

Bring your own repo.  
The candles are optional. The git commits are not.

*A discipline for AI-assisted coding that leaves receipts instead of fog.*

---

## What This Is

The Prompt-nomicon is a public guidebook for developers who use AI coding agents and want outcomes grounded in evidence instead of “the model said it should work.”

It provides structured workflows for:

- Defining bounded implementation tasks
- Separating planning from execution
- Preserving architectural intent
- Reducing hallucinated assumptions
- Creating validation and proof surfaces
- Detecting documentation drift
- Turning research into implementable specifications

The goal is not to remove creativity from development.

The goal is to stop waking up inside a repo crypt where twelve unrelated files changed, the tests no longer pass, and the coding agent insists the situation is “probably fine.”

---

## Who It's For

- Developers using coding agents who want **receipts, not vibes**
- Teams adopting AI-assisted workflows who need **proof before release claims**
- Tool builders designing agent protocols around **evidence-bound reasoning**
- Researchers and tinkerers building local or hybrid AI development systems
- Anyone tired of debugging spectral architecture decisions made three prompts ago

---

## The Core Loop

```text
Prompt → Task → Spec → Execution → Receipt → Drift Review
```

### 1. Prompt
Define scope, constraints, operating mode, and output contracts *before* the model acts.

### 2. Task
Separate planning from implementation.  
Planning prompts do not mutate files.  
Execution prompts do not invent goals.

### 3. Spec
Reason within evidence.  
No hallucinated APIs. No imaginary components. No phantom infrastructure buried beneath the floorboards.

### 4. Execution
Make the smallest coherent change possible.  
Prefer repeatable scripts over manual ritual sacrifice.

### 5. Receipt
Capture:
- what was attempted
- what changed
- what succeeded
- what failed
- what remains uncertain

Because memory fades. Git history lies. Receipts endure.

### 6. Drift Review
Check whether:
- docs still match implementation
- tests still validate claims
- architecture still reflects intent
- the repository has quietly become haunted

---

## Quickstart

1. Read [`docs/00-start-here.md`](docs/00-start-here.md)

2. Use [`templates/coding-agent-task.md`](templates/coding-agent-task.md) during your next coding-agent session

3. Walk through the [toy example](examples/tiny-cli-refactor/)

4. Write a receipt using [`receipts/template.md`](receipts/template.md)

5. Record architectural decisions with [`adr/template.md`](adr/template.md)

6. Run a drift review using [`templates/documentation-drift-review.md`](templates/documentation-drift-review.md)

---

## Templates

| Template | Use When |
|----------|----------|
| [Coding-Agent Task](templates/coding-agent-task.md) | Assigning a bounded implementation task to a coding agent |
| [Architecture Planning](templates/architecture-planning-prompt.md) | Evaluating architecture without touching code |
| [ADR](templates/adr-prompt.md) | Recording an architecture decision |
| [Proof-Surface Checklist](templates/proof-surface-checklist.md) | Verifying a claim has evidence |
| [Validation Checklist](templates/validation-checklist.md) | Checking implementation completeness |
| [Documentation Drift Review](templates/documentation-drift-review.md) | Finding stale docs after changes |
| [Research-to-Spec Packet](templates/research-to-spec-packet.md) | Converting research into implementable specifications |
| [Campaign/Spec Directory](templates/campaign-spec-directory.md) | Coordinating large multi-step project efforts |

---

## Evidence Discipline

The Prompt-nomicon distinguishes five truth surfaces:

- **Intent** — What was requested
- **Spec** — What was planned
- **Implementation** — What actually changed
- **Validation** — What was proven
- **Claim** — What is being asserted publicly

Most AI-assisted engineering failures happen when these surfaces collapse into one another like damp cardboard tomb walls in a forgotten dungeon crawl.

This project exists to keep them separate.
