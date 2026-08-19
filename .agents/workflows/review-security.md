---
description: Security-focused code review (XSS, injection, auth, secrets).
---
# /review-security Workflow

This workflow uses the `code-review` skill.

## Steps
1. Read the instructions in the [code-review skill](../skills/code-review/SKILL.md).
2. Execute the `/review-security` command flow:
   - Determine the review scope from user input.
   - Read `architecture.md` for data flow and integration points.
   - Analyze for: input validation, injection (SQL/XSS/command), authentication/authorization gaps, hardcoded secrets, data exposure, CORS/CSP misconfigurations.
   - Report findings by OWASP category with severity and remediation steps.
   - This is a read-only operation — no source code is modified.
