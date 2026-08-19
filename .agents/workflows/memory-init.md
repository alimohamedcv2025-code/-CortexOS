---
description: Initialize project memory by scanning the codebase.
---
# /memory-init Workflow

This workflow acts as a thin wrapper over the `/memory:init` command of the `project-memory` skill.

## Steps
1. Read the instructions in the [project-memory skill](../skills/project-memory/SKILL.md).
2. Execute the `/memory:init` command flow:
   - Create `.agent/memory/` directory if it does not exist.
   - Copy templates from `.agents/skills/project-memory/assets/templates/` to `.agent/memory/`.
   - Scan the codebase files (`index.html`, `script.js`, `style.css`) to retrieve the stack, flow, and conventions.
   - Populate `overview.md`, `architecture.md`, `conventions.md`, `features.md`, and `history.md` with verified project facts.
