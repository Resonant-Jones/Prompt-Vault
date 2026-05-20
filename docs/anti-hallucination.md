# Anti-Hallucination

*Concrete rules to prevent AI coding agents from inventing reality.*

## What Hallucination Looks Like in Coding Agents

Hallucination isn't just "wrong facts." In the context of coding agents, it takes specific forms:

| Hallucination type | Example | Consequence |
|--------------------|---------|-------------|
| **Invented API** | Agent calls `db.connect_async()` — that function doesn't exist | Broken code |
| **Invented file** | Agent references `src/utils/helpers.py` — never created | Build failure |
| **Invented component** | Agent describes "the caching layer" — no such thing exists | Architecture fiction |
| **Invented behavior** | Agent claims "the queue retries on failure" — it doesn't | Runtime surprise |
| **Invented dependency** | Agent imports a library not in `requirements.txt` | Import error |
| **Invented config** | Agent references an env var that isn't defined | Silent failure |

## The Anti-Hallucination Rules

### Rule 1: Reason Within Evidentiary Space

The agent must restrict all reasoning to the evidence provided in the context. If something is not in the context, it does not exist for the purposes of this task.

### Rule 2: No External Facts Unless Allowed

General programming knowledge (language syntax, standard library functions) is acceptable. Domain-specific knowledge (your company's architecture, your team's conventions, your system's behavior) is not — unless you explicitly include it or allow it.

### Rule 3: Cite Every Claim

Every claim about the system must cite its source. Uncited claims are unverified claims.

### Rule 4: Mark Uncertainty

When evidence is incomplete, conflicting, or absent, the agent must say so. Confidence without evidence is the signature of hallucination.

### Rule 5: Separate Source Fact from Inference

"`src/auth/login.py` hashes passwords with bcrypt" is a source fact (if the file is in context).  
"The system probably uses secure password storage everywhere" is an inference.  
Inference must be labeled as inference.

### Rule 6: No Invented Files, APIs, or Components

If the agent needs a file, API, or component that doesn't exist, it must either:
- Ask for it to be created (and mark it as new)
- Work within what exists
- State the gap explicitly

### Rule 7: Silence Is Not Confirmation

If the agent doesn't find evidence of something, that means the evidence wasn't provided — not that the thing doesn't exist. The agent must say "not found in the provided context" rather than "does not exist."

## The Truth-Surface Stack

To prevent hallucination, separate every statement into its correct truth surface:

```
Source fact       → "The file says X"
Inferred pattern  → "This pattern suggests Y"
Public abstraction → "The general principle is Z"
Recommendation    → "I recommend W"
Release claim     → "W is live in production"  ← NEVER without runtime proof
```

Each layer depends on the layer below it. If a source fact is wrong, everything above it collapses. This is why citation matters.

## Red Flags in Agent Output

Watch for these hallucination signals:

- **"The system uses..."** — Where is this documented?
- **"As is standard practice..."** — Standard where? Cite it.
- **"This follows the existing pattern..."** — Show the existing pattern.
- **"The architecture naturally supports..."** — According to which doc?
- **"We can simply..."** — "Simply" is often a hallucination flag. What makes it simple?
- **"Obviously..."** — If it's obvious, it should be easy to cite.

## Prevention Checklist

Before handing a task to an agent:

- [ ] Did you include the specific files the agent needs? (Not the whole repo.)
- [ ] Did you explicitly state what external knowledge is allowed?
- [ ] Did you require citations for reasoning steps?
- [ ] Did you forbid inventing files, APIs, and components?
- [ ] Did you define the evidence boundary?

After receiving agent output:

- [ ] Are all claims cited?
- [ ] Do the citations point to real things in the context?
- [ ] Are inferences marked as inferences?
- [ ] Are gaps and uncertainties stated?
- [ ] Did the agent invent anything not in the evidence?

## Next

→ [`docs/proof-surfaces.md`](proof-surfaces.md)
