---
description: Show recent commit history.
---
# /git-log Workflow

This workflow uses the `git-operations` skill.

## Steps
1. Read the instructions in the [git-operations skill](../skills/git-operations/SKILL.md).
2. Execute the `/git-log` command flow:
   - Run `git log --oneline --graph -n 20` (or user-specified count).
   - Present the log in a readable format.
   - If the user asks for details on a specific commit, show full info with `git show <hash>`.
