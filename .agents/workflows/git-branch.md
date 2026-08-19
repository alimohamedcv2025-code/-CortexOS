---
description: Create, switch, list, or delete branches.
---
# /git-branch Workflow

This workflow uses the `git-operations` skill.

## Steps
1. Read the instructions in the [git-operations skill](../skills/git-operations/SKILL.md).
2. Execute the `/git-branch` command flow:
   - Determine the operation from user input: list, create, switch, or delete.
   - **List**: Run `git branch -a` and display local/remote branches.
   - **Create**: Run `git checkout -b <name>` to create and switch.
   - **Switch**: Run `git checkout <name>` to switch to an existing branch.
   - **Delete**: Run `git branch -d <name>`. Use `-D` only with explicit user confirmation.
   - Present the result: current branch, list, or confirmation.
