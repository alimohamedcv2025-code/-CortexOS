---
description: Make a targeted update to project memory.
---
# /memory-update Workflow

This workflow acts as a thin wrapper over the `/memory:update` command of the `project-memory` skill.

## Steps
1. Read the instructions in the [project-memory skill](../skills/project-memory/SKILL.md).
2. Execute the `/memory:update` command flow:
   - Inspect the recent code modifications or user-indicated changes.
   - Perform targeted updates on the affected memory categories (e.g., updating a feature logic in `features.md` or recording a bug fix in `issues.md`/`history.md`).
   - Do not edit or rewrite unrelated memory files.
