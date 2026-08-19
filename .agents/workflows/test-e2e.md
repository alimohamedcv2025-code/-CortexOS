---
description: Create or run end-to-end tests for user flows.
---
# /test-e2e Workflow

This workflow uses the `testing` skill.

## Steps
1. Read the instructions in the [testing skill](../skills/testing/SKILL.md).
2. Execute the `/test-e2e` command flow:
   - Read `features.md` and `architecture.md` for user flows and entry points.
   - If creating tests: identify key user flows, generate e2e tests using the project's e2e framework (Playwright, Cypress, Puppeteer, etc.), cover critical paths.
   - If running tests: execute e2e tests and capture results with screenshots/traces if available.
   - Conditionally auto-update `conventions.md` if new e2e patterns were established and auto-write is allowed.
