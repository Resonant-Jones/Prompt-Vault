# ADR: Use argparse for CLI argument handling

## Status
Accepted

## Context
The `greet.py` script needs to accept an optional `--name` flag. We considered manual `sys.argv` parsing, the `argparse` standard library, and the external `click` library.

## Decision
Use `argparse` from the Python standard library. Configure `--name` with `nargs='?'` so it accepts an optional value and produces a clear error when the value is missing.

## Consequences

**Positive:**
- No external dependencies
- Built-in error messages for missing values
- Easy to extend with additional flags later
- Standard pattern familiar to Python developers

**Negative:**
- Slightly more verbose than manual `sys.argv` for a single flag
- `nargs='?'` behavior (optional value with error on missing) is less common knowledge

## Evidence
- argparse is part of the Python standard library (no install needed)
- The `nargs='?'` pattern is documented in the [argparse docs](https://docs.python.org/3/library/argparse.html#nargs)

## Relationship to Architecture Docs
This is a leaf decision — no broader architecture docs are affected.

## Alternatives Considered

| Alternative | Why rejected |
|-------------|--------------|
| Manual sys.argv | Error-prone, no help text, doesn't scale |
| click library | External dependency, overkill for one flag |

## Drift Watch
- If the script grows to require subcommands, consider migrating to click or typer
- If Python removes argparse (extremely unlikely), revisit

## Docs to Update If Accepted
- [ ] Update `greet.py` docstring to document `--name` flag
- [ ] No other docs affected
