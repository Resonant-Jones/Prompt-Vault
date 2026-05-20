# Contributing to The Prompt-nomicon

## What Belongs Here

The Prompt-nomicon is an educational resource for disciplined AI-assisted coding. Contributions should:

- Teach a reusable pattern, not a one-off trick
- Be grounded in repeatable methodology, not "magic prompt" claims
- Distinguish plan / implementation / proof / promise as separate truth surfaces
- Include evidence or clear examples
- Avoid private implementation details, credentials, or proprietary material

## What Does Not Belong

- "Prompt injection" or jailbreak techniques
- Hype, "mind-blowing," or "secret trick" framing
- Unsubstantiated claims about any specific model's behavior
- Private repo paths, internal architecture, or identity-sensitive material
- Product-specific guidance that cannot be generalized

## How to Contribute

### Adding a Template

1. Place it in `templates/`
2. Follow the existing template format: Mode, Inputs, Rules, Output Contract
3. Add a row to the templates table in `README.md`

### Adding a Doc

1. Place it in `docs/`
2. Cross-reference related docs and templates
3. Use the drift-aware pattern: state whether the doc is current, stale, or superseded

### Adding an Example

1. Create a directory under `examples/`
2. Include: `task.md`, `plan.md`, `adr.md`, `proof.md`, `validation-log.md`, `drift-review.md`
3. Keep the example self-contained and reproducible

### Adding a Campaign

1. Create a directory under `campaigns/`
2. Follow the `TEMPLATE/` structure
3. Include receipts for each work order

## Style Guide

- Clear, educational, practical
- Prefer checklists and templates over prose walls
- Slightly literary is fine; mystical is not
- No hype. Receipts or it did not happen.
- Use `code` for commands and file paths
- Use **bold** for key principles

## Code of Conduct

Be direct, be evidence-bound, be kind. Assume good faith. Cite your sources.
