# 00 — Start Here

Welcome to The Prompt-nomicon. This is the entry point.

## What You'll Learn

By the time you finish this guide, you will know how to:

1. Write a prompt that defines a **bounded task** a coding agent can actually complete
2. **Separate planning from implementation** so you don't get "vibe-coded" changes without review
3. Require **proof surfaces** — reproducible evidence — before accepting any claim
4. Structure your repo so **decisions, receipts, and current state** stay aligned
5. Detect and prevent **documentation drift** as code and proofs evolve

## The Discipline in One Sentence

**Prompt → Task → Spec → Execution → Receipt → Drift Review.**

Every step leaves a durable artifact. No step claims the authority of a later step.

## How to Read This Repo

| If you want to... | Read... |
|-------------------|---------|
| Understand the methodology | [`docs/methodology.md`](methodology.md) |
| Get a coding agent to do a task safely | [`templates/coding-agent-task.md`](../templates/coding-agent-task.md) |
| Plan architecture without touching code | [`templates/architecture-planning-prompt.md`](../templates/architecture-planning-prompt.md) |
| Record a decision | [`templates/adr-prompt.md`](../templates/adr-prompt.md) |
| Verify a claim has real evidence | [`docs/proof-surfaces.md`](proof-surfaces.md) |
| Check if your docs are stale | [`templates/documentation-drift-review.md`](../templates/documentation-drift-review.md) |
| See a worked example | [`examples/tiny-cli-refactor/`](../examples/tiny-cli-refactor/) |
| Launch a multi-step project | [`campaigns/TEMPLATE/`](../campaigns/TEMPLATE/) |

## The Five Truth Surfaces

Every claim about a software system fits into exactly one of these surfaces:

1. **Plan** — "This is what we intend to do." Safe claim: "Proposed."
2. **Implementation** — "We changed the code." Safe claim: "Implemented, not yet proven."
3. **Test evidence** — "Automated checks passed." Safe claim: "Tested under these conditions."
4. **Runtime proof** — "We observed it working." Safe claim: "Demonstrated in this environment."
5. **Release promise** — "Users can use it now." Only valid with current proof and updated docs.

**If you remember one thing:** never let a lower-numbered surface claim the authority of a higher-numbered one. A plan is not an implementation. Passing tests is not runtime proof. Yesterday's proof is not today's release promise.

## Your First Session

1. Open [`templates/coding-agent-task.md`](../templates/coding-agent-task.md)
2. Fill it out for something small — a bug fix, a doc update, a single script
3. Hand it to your coding agent
4. When it's done, fill out [`receipts/template.md`](../receipts/template.md)
5. Run [`templates/documentation-drift-review.md`](../templates/documentation-drift-review.md) to find stale docs

That's the loop. Do it once and you've already improved on "the agent said it works."

## Next

→ [`docs/methodology.md`](methodology.md)
