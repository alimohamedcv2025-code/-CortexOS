---
description: Architecture review (patterns, coupling, scalability, SOLID).
---
# /review-architecture Workflow

This workflow uses the `code-review` skill.

## Steps
1. Read the instructions in the [code-review skill](../skills/code-review/SKILL.md).
2. Execute the `/review-architecture` command flow:
   - Determine the review scope: overall project or specific modules.
   - Read `architecture.md`, `conventions.md`, and `decisions.md` from `.agent/memory/`.
   - Analyze for: coupling, cohesion, SOLID violations, scalability concerns, pattern consistency, separation of concerns.
   - Report findings with architectural diagrams when helpful.
   - Cross-reference findings against existing ADRs in `decisions.md`.
   - This is a read-only operation — no source code is modified.
