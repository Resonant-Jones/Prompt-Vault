# Source Grounding

*How to keep AI reasoning anchored to evidence instead of drifting into plausible fiction.*

## The Grounding Problem

AI models are pattern-completion engines. Given a prompt about your codebase, they will complete it in the most statistically plausible way — which may have nothing to do with your actual code, docs, or runtime.

Without grounding rules, a coding agent will:

- Invent functions that "should" exist
- Describe architecture that "makes sense"
- Reference files that "would be" in a typical project
- Make claims about "how the system works" based on general knowledge, not your specific system

**All of these are hallucinations.** Plausible, confident, and wrong.

## The Grounding Contract

Every prompt that involves reasoning must include:

```md
## Grounding Rules
- Reason only within the provided evidence.
- Do not use external facts unless explicitly allowed.
- Do not invent APIs, files, components, or services.
- Cite the specific snippet or doc that supports each reasoning step.
- Mark uncertainty explicitly when evidence is incomplete.
```

## What Counts as Evidence

Evidence is anything provided in the prompt or context that the model can cite:

| Evidence type | Example | Strength |
|---------------|---------|----------|
| Provided code | A file you included in the prompt | Strong — directly citable |
| Provided docs | A spec or ADR you included | Strong — directly citable |
| Command output | `ls`, test results, logs you included | Strong — directly citable |
| Explicit instruction | "The auth module is in `src/auth/`" | Strong — user-provided fact |
| General recall | "Python has a `json` module" | Weak — may be outdated or wrong |
| Inference | "This pattern suggests..." | Weak — must be marked as inference |

**The strongest evidence is what you explicitly include in the context.** General knowledge is only allowed if you explicitly permit it.

## The Citation Rule

Every reasoning step that makes a claim about the system must cite its source:

```md
## Example: Grounded Reasoning

**Claim:** The auth module uses JWT tokens.  
**Source:** `src/auth/tokens.py` line 42 shows `jwt.encode()` being called.  

**Claim:** The token expiry is configurable.  
**Source:** `config/auth.yaml` line 15 defines `token_expiry_minutes: 30`.  

**Claim:** I'm not sure how token refresh works.  
**Source:** No refresh logic found in `src/auth/`. This is a gap.
```

If a claim has no citation, it must be marked as:

- **Inference:** "Based on the pattern in `src/auth/tokens.py`, the refresh flow *probably* lives in..."
- **Gap:** "No evidence of X was found. This needs investigation."
- **Assumption:** "Assuming the standard JWT flow applies..."

## The "Do Not Assume" Rules

### Do Not Assume Missing Implementation Details

If a function, file, or component is not in the provided evidence, it does not exist. Do not treat it as if it does.

### Do Not Assume Private History

Unless it appears in the current context bundle, do not claim knowledge of past decisions, discussions, or events.

### Do Not Collapse Retrieved Material into "The User Said"

If you retrieve information from a doc or file, cite it as that doc or file — not as something the user told you.

### Say When Evidence Is Incomplete

If the evidence doesn't cover something, say so. "The provided files don't show how X works" is honest. Guessing is not.

## The Context Interpretation Contract

When working with context that includes retrieved or historical material:

1. **Disclose the source** of every piece of information.
2. **Do not treat old docs as current intent.** A doc from last month may not reflect today's goals.
3. **Warn when evidence conflicts.** If file A says one thing and file B says another, flag the conflict.
4. **Mark freshness.** State when each piece of evidence was captured.

## Grounding in Practice

### Before the Agent Acts

- Include only the files and docs the agent needs. More context = more surface for hallucination.
- Explicitly state what the agent is allowed to assume.
- Mark any gaps you already know about.

### During Agent Reasoning

- Every claim must have a citation or be marked as inference/gap/assumption.
- If the agent wants to reference something not in the context, it must ask.

### After the Agent Acts

- Verify claims against the actual codebase.
- Check that citations point to real things.
- Flag any uncited claims as unverified.

## Next

→ [`docs/anti-hallucination.md`](anti-hallucination.md)
