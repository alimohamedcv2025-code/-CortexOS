---
description: Restructure code without changing behavior, following project patterns.
---
# /refactor Workflow

This workflow uses the `development` skill.

## Steps
1. Read the instructions in the [development skill](../skills/development/SKILL.md).
2. Execute the `/refactor` command flow:
   - Read `architecture.md` and `conventions.md` for current patterns.
   - Plan the refactoring scope: what changes, what stays the same.
   - Implement the refactoring while preserving external behavior.
   - Verify the refactored code produces the same results.
   - Auto-update memory if allowed: update `architecture.md`, `conventions.md`, log in `history.md`.
