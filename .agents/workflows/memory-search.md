---
description: Search project memory using fast keyword search followed by contextual reading.
---
# /memory-search Workflow

This workflow acts as a thin wrapper over the `/memory:search` command of the `project-memory` skill.

## Steps
1. Read the instructions in the [project-memory skill](../skills/project-memory/SKILL.md).
2. Execute the `/memory:search` command flow:
   - Search the files in `.agent/memory/` directory matching the user's keywords or query.
   - Navigate and read the relevant matched content chunk or sections to build context.
