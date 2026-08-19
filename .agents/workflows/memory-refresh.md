---
description: Re-scan the codebase and reconcile project memory with the current project.
---
# /memory-refresh Workflow

This workflow acts as a thin wrapper over the `/memory:refresh` command of the `project-memory` skill.

## Steps
1. Read the instructions in the [project-memory skill](../skills/project-memory/SKILL.md).
2. Execute the `/memory:refresh` command flow:
   - Perform a full recursive codebase scan (excluding `.agent` and `.agents`).
   - Detect any inconsistencies between source files and `.agent/memory/` records.
   - Update affected files. Reconcile contradictory state details using the archiving guidelines.
