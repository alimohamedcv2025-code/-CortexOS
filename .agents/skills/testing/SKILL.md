---
name: testing
description: Test authoring, execution, and debugging workflows covering unit, integration, e2e, and test-fix operations.
---

# Testing Skill

Provides structured workflows for creating, running, and fixing tests. Detects existing test frameworks and follows project conventions for test patterns.

## Memory Integration

This skill is a **read-write** consumer of `.agent/memory/`.

Before any auto-write to memory:
1. Read `.agent/memory/config.yml`.
2. Confirm `auto_write.enabled == true`.
3. Confirm `auto_write.allow_external_skills == true`.
4. Confirm `auto_write.skills.testing != false`.
5. Confirm the target `auto_write.categories.<file> == true`.
6. If any check fails, skip auto-write and suggest running `/memory-update`.

---

## Commands

### `/test`

**Purpose**: Run the full test suite and report results.

**Execution Flow**:
1. **Detect test setup**: Look for test configs (`jest.config.*`, `vitest.config.*`, `*.test.*`, `*.spec.*`, `mocha`, etc.) and `package.json` test scripts.
2. **Run tests**: Execute the appropriate test command (e.g., `npm test`, `npx jest`, `npx vitest`).
3. **Parse results**: Collect pass/fail counts, coverage (if available), and failure details.
4. **Report**: Output a concise summary of results. For failures, include the test name, error message, and relevant code location.

---

### `/test-unit`

**Purpose**: Create or run unit tests for specified code.

**Execution Flow**:
1. **Gather context**: Read `conventions.md` for test patterns and naming conventions.
2. **If creating tests**:
   - Identify the target function(s) or module(s).
   - Generate test cases covering: happy path, edge cases, error cases, and boundary values.
   - Place test files according to project conventions (co-located or in `__tests__/` or `tests/`).
3. **If running tests**:
   - Execute only the relevant unit test file(s).
   - Parse and report results.
4. **Update memory** (conditional, if auto-write allowed):
   - Update `conventions.md` if new test patterns were established.

---

### `/test-integration`

**Purpose**: Create or run integration tests.

**Execution Flow**:
1. **Gather context**: Read `architecture.md` to understand component boundaries and integration points.
2. **If creating tests**:
   - Identify the integration boundary (e.g., API + database, module A + module B).
   - Generate tests that verify the interaction between components.
   - Include setup/teardown for shared state.
3. **If running tests**:
   - Execute integration test files.
   - Parse and report results.
4. **Update memory** (conditional, if auto-write allowed):
   - Update `conventions.md` if new integration test patterns were established.

---

### `/test-e2e`

**Purpose**: Create or run end-to-end tests.

**Execution Flow**:
1. **Gather context**: Read `features.md` and `architecture.md` for user flows and entry points.
2. **If creating tests**:
   - Identify key user flows to test.
   - Generate e2e tests using the project's e2e framework (Playwright, Cypress, Puppeteer, etc.).
   - Cover critical paths: navigation, form submission, error states.
3. **If running tests**:
   - Execute e2e tests.
   - Capture and report results, including screenshots/traces if available.
4. **Update memory** (conditional, if auto-write allowed):
   - Update `conventions.md` if new e2e patterns were established.

---

### `/test-fix`

**Purpose**: Diagnose and fix failing tests.

**Execution Flow**:
1. **Identify failing tests**: Run the test suite or use the user-specified test.
2. **Diagnose**: Analyze the failure:
   - Is the test wrong (outdated assertion, incorrect setup)?
   - Or is the implementation wrong (regression, behavior change)?
3. **Fix**: Apply the appropriate fix:
   - Update the test if the implementation change was intentional.
   - Fix the implementation if the test is correct and the code regressed.
4. **Verify**: Re-run the fixed test(s) to confirm they pass.
5. **Update memory** (if auto-write allowed):
   - Update `issues.md` if a bug was discovered and resolved.

---

## Skill Execution Rules

1. **Detect, don't assume**: Always detect the existing test framework before writing tests. Don't assume Jest, Vitest, or any specific tool.
2. **Follow project conventions**: Use `conventions.md` for file naming, test structure, and assertion style.
3. **Never invent facts**: Test only behaviors that verifiably exist in the code.
4. **Minimal test footprint**: Write focused tests. Avoid over-mocking or testing implementation details.
5. **Report clearly**: Test output should include pass/fail counts, failure details, and suggested fixes.
6. **No unrelated changes**: Only modify test files and the specific source files being fixed.
