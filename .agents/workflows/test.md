---
description: Run the full test suite and report results.
---
# /test Workflow

This workflow uses the `testing` skill.

## Steps
1. Read the instructions in the [testing skill](../skills/testing/SKILL.md).
2. Execute the `/test` command flow:
   - Detect the test framework from config files (`jest.config.*`, `vitest.config.*`, `package.json` scripts, etc.).
   - Run the full test suite using the appropriate command.
   - Parse results: pass/fail counts, coverage if available, failure details.
   - Output a concise summary. For failures, include test name, error message, and code location.
