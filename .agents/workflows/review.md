---
description: General code review for quality, readability, and correctness.
---
# /review Workflow

This workflow uses the `code-review` skill.

## Steps
1. Read the instructions in the [code-review skill](../skills/code-review/SKILL.md).
2. Execute the `/review` command flow:
   - Determine the review scope: file(s) or changes specified by the user.
   - Read `conventions.md` and `architecture.md` from `.agent/memory/` for context.
   - Analyze for: correctness, readability, convention compliance, duplication, error handling, edge cases.
   - Report findings with severity ratings (🔴 Critical, 🟡 Warning, 🔵 Info).
   - Provide actionable fix suggestions for each finding.
   - This is a read-only operation — no source code is modified.
