---
name: project-management
description: Initialize, audit, and manage the overall project structure, tech stack detection, and health overview.
---

# Project Management Skill

Provides project-level operations including initialization, scaffolding, tech stack detection, and project health audits.

## Memory Integration

This skill is a **read-write** consumer of `.agent/memory/`.

Before any auto-write to memory:
1. Read `.agent/memory/config.yml`.
2. Confirm `auto_write.enabled == true`.
3. Confirm `auto_write.allow_external_skills == true`.
4. Confirm `auto_write.skills.project-management != false`.
5. Confirm the target `auto_write.categories.<file> == true`.
6. If any check fails, skip auto-write and suggest running `/memory-update`.

---

## Commands

### `/init`

**Purpose**: Initialize or audit the project structure, detect the tech stack, and ensure memory is populated.

**Execution Flow**:

1. **Detect project type and tech stack**:
   - Scan root files: `package.json`, `index.html`, `*.config.*`, `*.yml`, `*.toml`, `Makefile`, etc.
   - Identify language(s), framework(s), build tools, and entry points.
   - Detect testing frameworks if present.

2. **Audit project structure**:
   - Verify essential files exist (e.g., `.gitignore`, `README.md`).
   - Report missing recommended files without creating them automatically.

3. **Bootstrap memory if absent**:
   - Check if `.agent/memory/config.yml` exists.
   - If not, trigger the `/memory-init` workflow to initialize project memory.

4. **Populate or refresh memory**:
   - If memory already exists, check if `overview.md` and `architecture.md` are outdated.
   - Update only stale categories with verified facts from the scan.
   - Record the initialization in `history.md`.

5. **Output a project health report**:
   - Tech stack summary.
   - File structure overview.
   - Memory status (initialized / needs refresh).
   - Any missing recommended configuration files.

---

## Skill Execution Rules

1. **Never invent facts**: Only report what is verified in the file system and source code.
2. **Do not create project files automatically**: Report missing files; let the user decide.
3. **Non-destructive**: Never overwrite or delete existing project files.
4. **Respect memory config**: Follow the guard logic described in Memory Integration.
5. **Keep output concise**: Summarize findings in structured tables or bullet lists.
