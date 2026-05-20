# Glossary

*Key terms used throughout The Prompt-nomicon.*

## Core Terms

### Prompt
The initial framing that defines mode, scope, allowed operations, and expected output *before* a model acts. A prompt without a mode declaration is ambiguous.

### Task
A scoped, bounded unit of work derived from a prompt. Tasks define what is in scope, what is forbidden, and what constitutes completion.

### Spec
An evidence-bound analysis that defines what must be true before, during, and after execution. Specs reason within provided evidence and do not invent details.

### Execution
The bounded implementation step: code changes, config updates, script runs. Execution must preserve idempotency and avoid scope creep.

### Receipt
A durable artifact recording what was attempted, what happened, and what remains uncertain. A receipt is not "success" — it is honesty.

### Drift Review
A systematic check that documentation, proofs, and claims still align after changes.

## Truth Surfaces

### Plan
Intended path or proposed approach. Safe claim: "Proposed."

### Implementation
Code that was changed. Safe claim: "Implemented in code, not yet proven."

### Test Evidence
Automated checks that passed. Safe claim: "Tested under these conditions."

### Runtime Proof
Observed working behavior in a real or representative environment. Safe claim: "Demonstrated in this environment."

### Release Promise
User-facing availability claim. Only valid with current proof and updated docs.

## Evidence Terms

### Evidence
Anything that supports or refutes a claim. Includes: passing tests, runtime logs, screenshots, command output, proof artifacts, reproducible scripts, linked commits or PRs, explicit negative findings.

### Proof Artifact
A reproducible record of verification. Should include environment, steps, observed result, and limits.

### Proof Surface
The collection of evidence that backs a specific claim. A release claim must point to a proof surface.

### Stale Proof
Evidence that predates later changes and may no longer be valid. Must be marked as such.

### Synthetic Proof
Generated or simulated evidence. May be useful but must be distinguished from runtime proof.

## Agent Terms

### Coding Agent
An AI system that can read, write, and modify code in a repository. Examples: Codex, Copilot, Cursor agent mode.

### Vibe Coding
The practice of prompting an agent, accepting its output, and moving on without verification. The Prompt-nomicon exists to replace this.

### Context Window
The total input a model can process in one call. Treated as a scarce resource in the Prompt-nomicon methodology.

### Hallucination
When a model generates plausible but false information — invented APIs, files, components, or architecture claims not present in the provided evidence.

## Documentation Terms

### Current-State Doc
A document that describes the system as it is right now. Must be updated when the system changes.

### ADR (Architecture Decision Record)
A document capturing a specific architecture decision, its context, consequences, and relationship to broader docs.

### Campaign
A multi-step project derived from audit severity and core-loop relevance. Structured as brief → scope → work orders → validation → proof → rollout.

### Audit Snapshot
A point-in-time assessment. Useful as context but must be marked as frozen — not treated as current state.

## Process Terms

### Idempotency
The property that running an operation multiple times produces the same result as running it once. Required for all coding-agent tasks.

### Blast Radius
The scope of change — how many files, systems, or behaviors are affected. Minimize blast radius.

### Scope Creep
When a task expands beyond its original boundaries without explicit approval. Forbidden in the Prompt-nomicon discipline.
