---
description: Create or run integration tests for component interactions.
---
# /test-integration Workflow

This workflow uses the `testing` skill.

## Steps
1. Read the instructions in the [testing skill](../skills/testing/SKILL.md).
2. Execute the `/test-integration` command flow:
   - Read `architecture.md` for component boundaries and integration points.
   - If creating tests: identify the integration boundary, generate tests verifying component interactions, include setup/teardown.
   - If running tests: execute integration test files and report results.
   - Conditionally auto-update `conventions.md` if new integration test patterns were established and auto-write is allowed.
