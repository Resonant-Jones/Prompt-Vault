# The Prompt-nomicon

*A discipline for AI-assisted coding that leaves receipts instead of fog.*

## What This Is

The Prompt-nomicon is a public guidebook for developers who use AI coding agents — and want to do it without collapsing into "the agent said it works" theater.

It is **not** a collection of "prompt hacks." It is a methodology for turning fuzzy goals into bounded tasks, separating plans from implementations from proofs from promises, and building repo structures that preserve decisions and evidence.

## Who It's For

- Developers using coding agents (Codex, Copilot, Cursor, etc.) who want **receipts, not vibes**
- Teams adopting AI-assisted workflows who need **proof surfaces** before release claims
- Tool builders designing agent protocols who want **evidence-bound reasoning** as a first-class contract

## The Core Loop

```
Prompt → Task → Spec → Execution → Receipt → Drift Review
```

1. **Prompt** — Define mode, scope, constraints, and output contract *before* the model acts.
2. **Task** — Separate planning from implementation. Planning prompts forbid file mutation.
3. **Spec** — Reason within evidence. No hallucinated APIs, files, or components.
4. **Execution** — Make the smallest coherent change. Prefer scripts for repetition.
5. **Receipt** — Capture what was attempted, what happened, and what remains uncertain.
6. **Drift Review** — Check whether docs, proofs, and claims still align.

## Quickstart

1. Read [`docs/00-start-here.md`](docs/00-start-here.md)
2. Use [`templates/coding-agent-task.md`](templates/coding-agent-task.md) for your next coding-agent session
3. Run through the [toy example](examples/tiny-cli-refactor/)
4. Write a receipt using [`receipts/template.md`](receipts/template.md)
5. Write an ADR using [`adr/template.md`](adr/template.md)
6. Run a drift review using [`templates/documentation-drift-review.md`](templates/documentation-drift-review.md)

## Templates

| Template | Use When |
|----------|----------|
| [Coding-Agent Task](templates/coding-agent-task.md) | Assigning a bounded implementation task to a coding agent |
| [Architecture Planning](templates/architecture-planning-prompt.md) | Evaluating architecture without touching code |
| [ADR](templates/adr-prompt.md) | Recording an architecture decision |
| [Proof-Surface Checklist](templates/proof-surface-checklist.md) | Verifying a claim has evidence |
| [Validation Checklist](templates/validation-checklist.md) | Checking implementation completeness |
| [Documentation Drift Review](templates/documentation-drift-review.md) | Finding stale docs after changes |
| [Research-to-Spec Packet](templates/research-to-spec-packet.md) | Converting research into implementable spec |
| [Campaign/Spec Directory](templates/campaign-spec-directory.md) | Launching a multi-step project campaign |

## Evidence Discipline

The Prompt-nomicon distinguishes five truth surfaces:

| Surface | Meaning | Safe Claim |
|---------|---------|-------------|
| Plan | Intended path | "Proposed." |
| Implementation | Code changed | "Implemented in code, not yet proven." |
| Test evidence | Automated checks passed | "Tested under these conditions." |
| Runtime proof | Observed working behavior | "Demonstrated in this environment." |
| Release promise | User-facing availability | Only valid with current proof and updated docs. |

**No release claim without a proof surface. No implementation claim without a diff or artifact. No runtime claim without runtime evidence.**

## Anti-Hallucination Rules

1. Reason only within evidentiary space.
2. Do not use external facts unless explicitly allowed.
3. Do not invent APIs, files, or components.
4. Cite the supporting evidence for each reasoning step.
5. Mark uncertainty explicitly.
6. Separate source facts from inferred patterns from recommendations.

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## License

MIT — see [`LICENSE`](LICENSE).
