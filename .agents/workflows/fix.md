---
description: Diagnose and fix a bug with root-cause analysis.
---
# /fix Workflow

This workflow uses the `development` skill.

## Steps
1. Read the instructions in the [development skill](../skills/development/SKILL.md).
2. Execute the `/fix` command flow:
   - Read `.agent/memory/issues.md` and related source files for context.
   - Diagnose the bug by tracing the root cause through the code.
   - Apply the minimal correct fix following project conventions.
   - Verify the fix resolves the issue without regressions.
   - Auto-update memory if allowed: mark issue resolved in `issues.md`, log fix in `history.md`.
