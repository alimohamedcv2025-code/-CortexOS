---
description: Soft-delete a memory entry by archiving it, unless hard deletion is explicitly requested.
---
# /memory-forget Workflow

This workflow acts as a thin wrapper over the `/memory:forget` command of the `project-memory` skill.

## Steps
1. Read the instructions in the [project-memory skill](../skills/project-memory/SKILL.md).
2. Execute the `/memory:forget` command flow:
   - Soft-delete requested features, decisions, or issues by moving them to the `# History / Archive` section inside the respective markdown file.
   - Document a reason and timestamp when archiving.
   - Perform a hard delete only if the user explicitly specifies it.
