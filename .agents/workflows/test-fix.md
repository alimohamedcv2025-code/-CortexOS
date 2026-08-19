---
description: Diagnose and fix failing tests with root-cause analysis.
---
# /test-fix Workflow

This workflow uses the `testing` skill.

## Steps
1. Read the instructions in the [testing skill](../skills/testing/SKILL.md).
2. Execute the `/test-fix` command flow:
   - Identify the failing test(s) by running the suite or using user input.
   - Diagnose: is the test wrong (outdated assertion, bad setup) or is the implementation wrong (regression)?
   - Apply the appropriate fix: update the test or fix the source code.
   - Re-run the fixed test(s) to confirm they pass.
   - Auto-update `issues.md` if a bug was discovered and resolved, and auto-write is allowed.
