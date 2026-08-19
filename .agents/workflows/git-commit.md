---
description: Stage and commit changes with a conventional message.
---
# /git-commit Workflow

This workflow uses the `git-operations` skill.

## Steps
1. Read the instructions in the [git-operations skill](../skills/git-operations/SKILL.md).
2. Execute the `/git-commit` command flow:
   - Run `git status` to see what's changed.
   - Stage specified files, or present changes and confirm what to stage.
   - Generate a conventional commit message: `<type>(<scope>): <description>`.
   - Present the staged files and proposed message to the user for confirmation.
   - Execute `git commit -m "<message>"`.
   - Auto-update `history.md` if auto-write is allowed.
