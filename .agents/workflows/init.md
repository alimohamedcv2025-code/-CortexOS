---
description: Initialize or audit the project structure, detect tech stack, and bootstrap memory.
---
# /init Workflow

This workflow uses the `project-management` skill.

## Steps
1. Read the instructions in the [project-management skill](../skills/project-management/SKILL.md).
2. Execute the `/init` command flow:
   - Scan root files to detect the tech stack, language(s), framework(s), build tools, and entry points.
   - Audit the project structure and report any missing recommended files (e.g., `.gitignore`, `README.md`).
   - If `.agent/memory/config.yml` does not exist, trigger the `/memory-init` workflow.
   - If memory already exists, update stale categories with verified facts from the scan.
   - Output a concise project health report: stack, structure, and memory status.
