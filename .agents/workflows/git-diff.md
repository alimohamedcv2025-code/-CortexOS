---
description: Show diffs of working, staged, or between branches.
---
# /git-diff Workflow

This workflow uses the `git-operations` skill.

## Steps
1. Read the instructions in the [git-operations skill](../skills/git-operations/SKILL.md).
2. Execute the `/git-diff` command flow:
   - Determine diff scope from user input: working directory, staged, between refs, or specific file.
   - Run the appropriate `git diff` command.
   - Present the diff with syntax context.
   - Summarize: files changed, insertions, deletions.
