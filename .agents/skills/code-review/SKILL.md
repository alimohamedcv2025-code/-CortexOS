---
name: code-review
description: Structured code review workflows for quality, security, performance, and architecture analysis.
---

# Code Review Skill

Provides structured, read-only code review workflows. Reviews are performed against project conventions and architecture documented in memory. This skill **never modifies source code** — it only produces findings and recommendations.

## Memory Integration

This skill is a **read-only** consumer of `.agent/memory/`.

- Reads `architecture.md`, `conventions.md`, and `features.md` for review context.
- Does **not** auto-write to memory by default.
- If a review uncovers important findings, suggest running `/memory-update` to record them.

---

## Commands

### `/review`

**Purpose**: General code review for quality, readability, correctness, and convention compliance.

**Execution Flow**:
1. **Determine scope**: Review file(s) or changes specified by the user. If unspecified, review recently changed files.
2. **Read context**: Load `conventions.md` and `architecture.md` from memory.
3. **Analyze**: Check for:
   - Code correctness and logic errors.
   - Readability and naming conventions.
   - Convention compliance (from `conventions.md`).
   - Code duplication.
   - Error handling completeness.
   - Edge cases.
4. **Report findings**: Output a structured review with severity ratings:
   - 🔴 **Critical**: Bugs, security issues, data loss risks.
   - 🟡 **Warning**: Bad practices, potential issues, maintainability concerns.
   - 🔵 **Info**: Style suggestions, minor improvements.
5. **Suggest fixes**: Provide actionable code suggestions for each finding.

---

### `/review-security`

**Purpose**: Security-focused code review.

**Execution Flow**:
1. **Determine scope**: Same as `/review`.
2. **Read context**: Load `architecture.md` for data flow and integration points.
3. **Analyze for security issues**:
   - **Input validation**: Unsanitized user input, missing validation.
   - **Injection**: SQL, XSS, command injection, template injection.
   - **Authentication/Authorization**: Missing auth checks, privilege escalation.
   - **Secrets**: Hardcoded API keys, passwords, tokens.
   - **Data exposure**: Sensitive data in logs, error messages, or client-side code.
   - **Dependencies**: Known vulnerable patterns.
   - **CORS/CSP**: Misconfigured security headers.
4. **Report findings**: Structured by OWASP category with severity and remediation.

---

### `/review-performance`

**Purpose**: Performance-focused code review.

**Execution Flow**:
1. **Determine scope**: Same as `/review`.
2. **Read context**: Load `architecture.md` for system topology.
3. **Analyze for performance issues**:
   - **Algorithmic complexity**: O(n²) or worse operations on large datasets.
   - **Memory**: Unbounded growth, memory leaks, large allocations.
   - **I/O**: Blocking operations, unnecessary network calls, missing caching.
   - **Rendering**: Excessive DOM manipulation, layout thrashing, unoptimized assets.
   - **Bundle size**: Unused imports, large dependencies.
   - **Concurrency**: Race conditions, deadlocks, inefficient async patterns.
4. **Report findings**: Include estimated impact (high/medium/low) and suggested optimizations.

---

### `/review-architecture`

**Purpose**: Architecture-level code review.

**Execution Flow**:
1. **Determine scope**: Review the overall project or specific modules.
2. **Read context**: Load `architecture.md`, `conventions.md`, and `decisions.md`.
3. **Analyze for architectural issues**:
   - **Coupling**: Tight coupling between modules, circular dependencies.
   - **Cohesion**: Low cohesion within modules, misplaced responsibilities.
   - **SOLID principles**: Violations of single responsibility, open/closed, etc.
   - **Scalability**: Patterns that won't scale with growth.
   - **Consistency**: Deviations from established architectural patterns.
   - **Separation of concerns**: Mixed layers (UI logic in data layer, etc.).
4. **Report findings**: Include architectural diagrams or dependency maps when helpful.
5. **Reference ADRs**: Cross-reference findings with existing decisions in `decisions.md`.

---

## Skill Execution Rules

1. **Never modify source code**: Reviews are read-only. Provide suggestions, not edits.
2. **Read memory first**: Always consult project memory to understand conventions and architecture.
3. **Be actionable**: Every finding must include a specific recommendation.
4. **Use severity ratings**: Categorize findings so the user can prioritize.
5. **No invented issues**: Only flag problems that are concretely evidenced in the code.
6. **Respect scope**: Review only what the user asked for. Don't review the entire codebase unless requested.
