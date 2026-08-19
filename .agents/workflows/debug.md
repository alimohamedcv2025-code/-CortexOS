---
description: Investigate an issue with structured debugging steps.
---
# /debug Workflow

This workflow uses the `development` skill.

## Steps
1. Read the instructions in the [development skill](../skills/development/SKILL.md).
2. Execute the `/debug` command flow:
   - Read relevant memory files and source code. Check `issues.md` for known problems.
   - Reproduce the issue and identify triggering conditions.
   - Isolate the problem to specific file(s), function(s), or line(s).
   - Identify and document the root cause with evidence.
   - Report findings and suggest a fix approach.
   - Conditionally auto-update `issues.md` if a confirmed bug is found and auto-write is allowed.
