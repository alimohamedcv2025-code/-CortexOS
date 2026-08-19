---
description: Show working tree status and staged changes.
---
# /git-status Workflow

This workflow uses the `git-operations` skill.

## Steps
1. Read the instructions in the [git-operations skill](../skills/git-operations/SKILL.md).
2. Execute the `/git-status` command flow:
   - Run `git status --porcelain` and `git status`.
   - Present results in a structured format: staged changes, unstaged modifications, untracked files.
   - Summarize: total files changed, additions, deletions.
