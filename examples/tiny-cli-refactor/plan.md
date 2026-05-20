# Plan: Tiny CLI Refactor

*Planning mode analysis before implementation.*

## Current State
`greet.py` prints a hardcoded "Hello, World!" with no argument handling.

## Desired State
`greet.py` accepts an optional `--name` flag. Without the flag, it prints "Hello, World!" (backward compatible). With the flag, it prints "Hello, {name}!". Missing value triggers a usage error.

## Options Considered

### Option A: argparse
- **Pros:** Standard library, handles `--name` with and without value, generates help text
- **Cons:** Heavier than needed for a single flag

### Option B: sys.argv manual parsing
- **Pros:** Minimal, no imports beyond sys
- **Cons:** Error-prone, no built-in help, harder to extend

### Option C: click library
- **Pros:** Elegant, great for CLIs
- **Cons:** External dependency — overkill for one flag

## Recommended Option
**Option A (argparse)** — Standard library, clean error handling, no external dependencies.

## Migration Path
1. Import argparse
2. Add `--name` argument with `nargs='?'` for optional value
3. Default to "World" when not provided
4. Show usage error when `--name` is given without a value
5. Add tests for all three cases

## Proof Surface Required
- Terminal output showing all three acceptance criteria met
- Test output showing all tests pass
