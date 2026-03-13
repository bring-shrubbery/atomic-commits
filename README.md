# atomic-commits

A Claude Code skill that enforces an atomic commit workflow. When active, Claude breaks implementation tasks into the smallest possible self-contained units and commits after completing each one.

## What it does

- Plans work as a numbered list of atomic steps before coding
- Implements one logical change at a time
- Commits immediately after each change with a clear conventional commit message
- Ensures the codebase builds and tests pass after every commit

## Install

```
/install-skill bring-shrubbery/atomic-commits
```

## Usage

The skill activates automatically when Claude detects implementation work (features, bug fixes, refactoring). You can also invoke it manually:

```
/atomic-commits
```

## Example output

For a task like "Add email validation to the signup form", Claude will produce:

```
feat: add email validation utility function
test: add tests for email validation
feat: integrate email validation into signup form
feat: display error message for invalid email input
```

Each commit is a single, reviewable, self-contained change.

## License

MIT
