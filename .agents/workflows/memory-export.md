---
description: Export project memory as either one consolidated Markdown file or a copy of the memory directory.
---
# /memory-export Workflow

This workflow acts as a thin wrapper over the `/memory:export` command of the `project-memory` skill.

## Steps
1. Read the instructions in the [project-memory skill](../skills/project-memory/SKILL.md).
2. Execute the `/memory:export` command flow:
   - Export memory as a single consolidated Markdown file compiling all memory categories, OR
   - Create a copy of the entire `.agent/memory/` configuration/schema folder at a target folder chosen by the user.
