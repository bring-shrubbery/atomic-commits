---
name: atomic-commits
description: Enforces atomic commit workflow — breaks implementation into small, self-contained units and commits after each one. Use when implementing features, fixing bugs, or making any multi-step code changes.
---

# Atomic Commits Workflow

You MUST follow an atomic commit workflow for the current task. This means:

## Planning Phase

Before writing any code, break the task into the smallest possible **atomic units of work**. Each unit should be:

- A single logical change (one concern, one purpose)
- Self-contained — the codebase should build and pass tests after each commit
- Small enough to review in isolation

Write out your plan as a numbered list of atomic steps before starting.

## Implementation Phase

For **each** atomic unit, follow this cycle:

1. **Implement** the single atomic change
2. **Verify** the change works (run relevant tests, type-checks, or linters if available)
3. **Commit** immediately with a clear, descriptive message

### Commit Guidelines

- Commit after every atomic unit — do NOT batch multiple logical changes
- Use conventional commit style: `type: short description`
  - Types: `feat`, `fix`, `refactor`, `test`, `docs`, `chore`, `style`, `perf`
- The commit message should explain **what** changed and **why** (if not obvious)
- Stage only the files relevant to that atomic change — do not use `git add -A` blindly
- Never skip git hooks (no `--no-verify`)

### What counts as one atomic unit

- Adding a single function or method
- Renaming a variable/function across the codebase
- Adding or updating a single test case
- Extracting a component or module
- Fixing a single bug
- Adding a single dependency
- Updating a single configuration
- Adding types/interfaces for a single feature

### What is NOT atomic

- Implementing a feature AND writing its tests in one commit
- Renaming something AND changing its behavior
- Adding a dependency AND using it
- Fixing a bug AND refactoring surrounding code

## Example

Task: "Add email validation to the signup form"

Plan:
1. Add email validation utility function
2. Add tests for email validation
3. Integrate validation into signup form component
4. Add error message display for invalid email

Each step gets its own commit:
```
feat: add email validation utility function
test: add tests for email validation
feat: integrate email validation into signup form
feat: display error message for invalid email input
```

## Important

- If you realize mid-implementation that a step should be split further, split it
- If a step turns out to be trivial (e.g., a one-line change), it still gets its own commit
- Never amend a previous atomic commit to add more changes — make a new commit instead
- If tests fail after a change, fix them in the same commit as the change (the unit isn't complete until it works)
