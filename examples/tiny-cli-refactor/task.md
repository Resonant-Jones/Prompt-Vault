# Task: Tiny CLI Refactor

*A toy example demonstrating the full Prompt-nomicon loop.*

## Mode
Implementation allowed.

## Goal
Refactor `greet.py` — a tiny CLI script — to accept a `--name` flag and print a greeting. The script currently only prints "Hello, World!" with no arguments.

## Scope

**Allowed:**
- `greet.py`
- `test_greet.py` (create if needed)

**Forbidden:**
- Other files in the project
- Secrets or credentials
- Unrelated refactors

## Inputs

### Current `greet.py`
```python
#!/usr/bin/env python3
"""A tiny greeting CLI."""
print("Hello, World!")
```

### Acceptance Criteria
- Running `python greet.py` prints "Hello, World!" (backward compatible)
- Running `python greet.py --name Alice` prints "Hello, Alice!"
- Running `python greet.py --name` (missing value) prints a usage error
- The script is idempotent

## Validation
```bash
python greet.py
python greet.py --name Alice
python greet.py --name
python -m pytest test_greet.py -v
```

## Required Final Report
- Summary of changes
- Files changed
- Test output
- Evidence (terminal output)
- Known limitations
- Next-step plan
