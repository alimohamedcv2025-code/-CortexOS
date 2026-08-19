---
description: Performance-focused code review (bottlenecks, memory, complexity).
---
# /review-performance Workflow

This workflow uses the `code-review` skill.

## Steps
1. Read the instructions in the [code-review skill](../skills/code-review/SKILL.md).
2. Execute the `/review-performance` command flow:
   - Determine the review scope from user input.
   - Read `architecture.md` for system topology.
   - Analyze for: algorithmic complexity, memory leaks, blocking I/O, excessive DOM manipulation, bundle size, concurrency issues.
   - Report findings with estimated impact (high/medium/low) and suggested optimizations.
   - This is a read-only operation — no source code is modified.
