---
description: Create or run unit tests for specified code.
---
# /test-unit Workflow

This workflow uses the `testing` skill.

## Steps
1. Read the instructions in the [testing skill](../skills/testing/SKILL.md).
2. Execute the `/test-unit` command flow:
   - Read `conventions.md` for test patterns and naming.
   - If creating tests: identify the target function(s)/module(s), generate test cases (happy path, edge cases, error cases, boundaries), place files per project conventions.
   - If running tests: execute only the specified unit test file(s) and report results.
   - Conditionally auto-update `conventions.md` if new test patterns were established and auto-write is allowed.
