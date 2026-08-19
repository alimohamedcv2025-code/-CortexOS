---
description: Show the current project memory summary, or initialize it if memory does not exist.
---
# /memory Workflow

This workflow acts as a thin wrapper over the `/memory` command of the `project-memory` skill.

## Steps
1. Read the instructions in the [project-memory skill](../skills/project-memory/SKILL.md).
2. Execute the `/memory` command flow:
   - Check if config file `.agent/memory/config.yml` exists.
   - If it does not exist, trigger `/memory-init` workflow.
   - If it exists, read the files in `.agent/memory/` and output a concise status summary (number of architectural decisions, implemented/backlog features, active issues, and last modified times).
