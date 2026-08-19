---
description: Make a targeted code modification with minimal scope.
---
# /modify Workflow

This workflow uses the `development` skill.

## Steps
1. Read the instructions in the [development skill](../skills/development/SKILL.md).
2. Execute the `/modify` command flow:
   - Read relevant memory files for conventions and architecture context.
   - Confirm the scope of modification if ambiguous.
   - Apply the modification precisely with no side effects beyond the stated scope.
   - Verify the change works as intended.
   - Conditionally auto-update the relevant memory category if the change warrants it and auto-write is allowed.
