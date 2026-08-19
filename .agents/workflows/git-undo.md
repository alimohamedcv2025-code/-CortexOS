---
description: Undo last commit, unstage files, or discard changes.
---
# /git-undo Workflow

This workflow uses the `git-operations` skill.

## Steps
1. Read the instructions in the [git-operations skill](../skills/git-operations/SKILL.md).
2. Execute the `/git-undo` command flow:
   - Determine the undo operation from user input: undo last commit (soft/hard), unstage files, or discard working changes.
   - **Safety check**: For destructive operations (`--hard`, discard), show what will be lost and require explicit user confirmation before executing.
   - Execute the appropriate git command.
   - Conditionally auto-update `history.md` for significant undos if auto-write is allowed.
