---
description: Safely remove code, files, or features with dependency analysis.
---
# /remove Workflow

This workflow uses the `development` skill.

## Steps
1. Read the instructions in the [development skill](../skills/development/SKILL.md).
2. Execute the `/remove` command flow:
   - Read `features.md` and `architecture.md` to understand dependencies.
   - Perform impact analysis: identify all references and affected files.
   - Remove the targeted code, files, or features.
   - Clean up orphaned imports, dead references, and unused variables.
   - Verify the project still works without the removed components.
   - Auto-update memory if allowed: archive in `features.md`, update `architecture.md`, log in `history.md`.
