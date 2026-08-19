---
name: project-memory
description: Manage the agentic memory space for recording architectural decisions, codebase overview, conventions, history, features, issues, and configuration.
---

# Project Memory Skill

A systematic Project Memory skill designed for agentic coding workflows to maintain codebase state, architecture, conventions, track features, issues, decisions, and history dynamically.

## Memory Location & Structure

All memory assets reside in:
`.agent/memory/`

Within this directory, the following files maintain state:

1. `config.yml` - Configuration controlling memory parameters and auto-write settings.
2. `overview.md` - High-level description, tech stack, and entry points of the project.
3. `architecture.md` - System topology, folder layouts, state/storage management, and integrations.
4. `conventions.md` - Coding guidelines, styling rules, git workflow, and error handling conventions.
5. `decisions.md` - Architectural Decision Records (ADRs) tracking options, selections, and context.
6. `features.md` - Documented list of both implemented and planned backlog features.
7. `issues.md` - Active bugs, lint/compilation errors, and tracked technical debt.
8. `history.md` - Significant releases, changes, and migration instructions.

---

## Commands Specification

Agents executing this skill must support the client-side interpretation of the following slash commands:

### `/memory`
- **Purpose**: Initialize memory environment if not present. If memory is already initialized, evaluate the `.agent/memory/` directory and print a concise summary of the status of each file (number of entries, last modified time, active issues).
- **Execution Flow**:
  1. Check if `.agent/memory/config.yml` exists. If not, trigger initialization (`/memory:init`).
  2. Read each markdown file in `.agent/memory/` and parse statistics (e.g., number of architectural decisions, implemented/backlog features, active issues).
  3. Output a summary panel.

### `/memory:init`
- **Purpose**: Perform an initial full scan of the codebase and initialize the 7 memory files using templates located in `.agents/skills/project-memory/assets/templates/`.
- **Execution Flow**:
  1. Verify if `.agent/memory/` exists; if not, create it.
  2. Copier templates over to `.agent/memory/` if they do not yet exist, including `config.yml`.
  3. Scan the codebase recursively (HTML, JS, CSS, configs) to collect tech stack info, entry points, and existing features.
  4. Write the collected facts into `overview.md`, `architecture.md`, `conventions.md`, `features.md`, and `history.md`.
  5. Validate that all files have been initialized without placeholder values. Ensure all populated data points are verified facts.

### `/memory:update`
- **Purpose**: Update targeted memory files based on recent local modifications (e.g., a newly implemented feature, a resolved bug, a new ADR).
- **Execution Flow**:
  1. Inspect the specific changes.
  2. Edit only the relevant category files (e.g., `features.md`, `history.md`, or `issues.md`) using precise file edits.
  3. Do not rewrite entire files unless necessary. Keep modifications local to specific sections.

### `/memory:refresh`
- **Purpose**: Trigger a comprehensive scan of the codebase to identify any changes that missed targeted updates, and reconcile files under `.agent/memory/`.
- **Execution Flow**:
  1. Recursively search codebase.
  2. Identify discrepancies between local source files and current memory documents.
  3. Reconcile differences. If any contradiction occurs, archive the deprecated data rather than deleting it.

### `/memory:search`
- **Purpose**: Query the collective memory files by performing keyword-matching first, and report findings on related context.
- **Execution Flow**:
  1. Use keyword searches across all files in `.agent/memory/*.md`.
  2. Read the most relevant matches to obtain context before making changes.

### `/memory:forget`
- **Purpose**: Soft-delete or archive entries (like old bugs or deprecated features) by moving them to archived sections or prefixing them, stating the reason. Hard-deletes are only allowed if explicitly requested by the user.
- **Execution Flow**:
  1. Locate the entry to be deleted.
  2. Instead of removal, move the items to a `# History / Archive` section in the respective markdown file.
  3. Add metadata: date archived and reason.

### `/memory:export`
- **Purpose**: Export the collective memory contents.
- **Execution Flow**:
  1. Export options:
     - Consolidated: Generate a single markdown file containing all pages.
     - Folder: Copy the complete `.agent/memory/` folder to a user-specified destination.

---

## Configuration (`config.yml`)

The configuration file `.agent/memory/config.yml` controls the behavior of memory auto-writing:

- **Auto-write Toggle**:
  - `auto_write.enabled`: Global flag to turn off automate writes. If false, memory is only modified via explicit commands.
  - `auto_write.allow_external_skills`: If true, other active skills (like editing/testing skills) can automatically update relevant memory.
  - `auto_write.categories`: Fine-grained toggles for enabling/disabling auto-write per file.
  - `auto_write.skills`: Define permissions per active skill identifier.

---

## Skill Execution Rules

1. **Never Invent Facts**: Do not declare features, configurations, architecture, or tech stack items that do not exist or cannot be verified in the current source code.
2. **Evidence-Based Documentation**: Prioritize scanning the file tree, file content, and package descriptors over guessing or assuming standard configurations.
3. **Preserve History**: Retain original decision logs, initial setup dates, and older features.
4. **Archive on Contradiction**: When configuration, styles, or logic changes, archive older items with comments/markers rather than silent erasure.
5. **Agent-Agnostic Format**: All output files must use standard vanilla Markdown and standard YAML configurations, ensuring usability across any agent or LLM interface.
6. **No Code Modification During Install**: Do not edit indices, logic files, script files, etc. while configuring the skill environment.
