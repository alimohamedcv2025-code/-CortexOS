---
description: Pull, push, or sync with remote.
---
# /git-sync Workflow

This workflow uses the `git-operations` skill.

## Steps
1. Read the instructions in the [git-operations skill](../skills/git-operations/SKILL.md).
2. Execute the `/git-sync` command flow:
   - Determine the operation: pull, push, or full sync (pull then push).
   - **Pre-flight checks**: Check for uncommitted changes before pull. Verify the branch has an upstream remote.
   - Execute the operation: `git pull --rebase` (preferred) or `git push origin <branch>`.
   - **Handle conflicts**: If conflicts occur, list conflicted files and advise on resolution.
