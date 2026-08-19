---
name: development
description: Core coding workflows for building features, fixing bugs, debugging, refactoring, modifying, and removing code.
---

# Development Skill

Provides structured workflows for all core coding operations. Each command follows a consistent pattern: read context from memory → plan → implement → verify → update memory.

## Memory Integration

This skill is a **read-write** consumer of `.agent/memory/`.

Before any auto-write to memory:
1. Read `.agent/memory/config.yml`.
2. Confirm `auto_write.enabled == true`.
3. Confirm `auto_write.allow_external_skills == true`.
4. Confirm `auto_write.skills.development != false`.
5. Confirm the target `auto_write.categories.<file> == true`.
6. If any check fails, skip auto-write and suggest running `/memory-update`.

---

## Commands

### `/feature`

**Purpose**: Plan and implement a new feature.

**Execution Flow**:
1. **Gather context**: Read `.agent/memory/architecture.md`, `conventions.md`, and `features.md` to understand the current system and coding standards.
2. **Plan**: Outline the implementation approach — files to create/modify, components, data flow.
3. **Implement**: Write code following project conventions. Create new files or modify existing ones.
4. **Verify**: Run basic checks (syntax, imports) to ensure nothing is obviously broken.
5. **Update memory** (if auto-write allowed):
   - Add the feature to `features.md` under the appropriate section.
   - Update `architecture.md` if structural changes were made.
   - Log the change in `history.md`.

---

### `/fix`

**Purpose**: Diagnose and fix a bug.

**Execution Flow**:
1. **Gather context**: Read `.agent/memory/issues.md` and related source files.
2. **Diagnose**: Reproduce or reason about the issue. Trace the root cause through code.
3. **Fix**: Apply the minimal correct fix, following project conventions.
4. **Verify**: Confirm the fix resolves the issue without regressions.
5. **Update memory** (if auto-write allowed):
   - Mark the issue as resolved in `issues.md`.
   - Log the fix in `history.md`.

---

### `/debug`

**Purpose**: Investigate an issue with structured debugging steps, without necessarily applying a fix.

**Execution Flow**:
1. **Gather context**: Read relevant memory files and source code. Check `issues.md` for known problems.
2. **Reproduce**: Identify the conditions that trigger the issue.
3. **Isolate**: Narrow down to the specific file(s), function(s), or line(s) causing the problem.
4. **Identify root cause**: Determine the underlying reason. Document findings.
5. **Report findings**: Present the diagnosis with evidence. Suggest a fix approach.
6. **Update memory** (conditional, if auto-write allowed):
   - Only if a confirmed bug is found, add it to `issues.md`.

---

### `/refactor`

**Purpose**: Restructure code without changing external behavior.

**Execution Flow**:
1. **Gather context**: Read `architecture.md` and `conventions.md` to understand current patterns.
2. **Plan**: Identify the refactoring scope. Document what will change and what will stay the same.
3. **Implement**: Apply the refactoring. Keep behavior identical.
4. **Verify**: Confirm the refactored code produces the same results.
5. **Update memory** (if auto-write allowed):
   - Update `architecture.md` if the structure changed.
   - Update `conventions.md` if patterns were standardized.
   - Log the refactoring in `history.md`.

---

### `/modify`

**Purpose**: Make a targeted code modification as specified by the user.

**Execution Flow**:
1. **Gather context**: Read relevant memory files to understand conventions and architecture.
2. **Plan**: Confirm the scope of the modification with the user if ambiguous.
3. **Implement**: Apply the modification precisely. Avoid side effects beyond the stated scope.
4. **Verify**: Check that the change works as intended.
5. **Update memory** (conditional, if auto-write allowed):
   - Update the relevant memory category based on the nature of the change.

---

### `/remove`

**Purpose**: Safely remove code, files, or features from the project.

**Execution Flow**:
1. **Gather context**: Read `features.md` and `architecture.md` to understand dependencies.
2. **Impact analysis**: Identify all references to the code being removed. List affected files.
3. **Remove**: Delete or clean up the targeted code, files, or features.
4. **Clean up**: Remove orphaned imports, dead references, and unused variables.
5. **Verify**: Confirm the project still works without the removed components.
6. **Update memory** (if auto-write allowed):
   - Archive the removed feature in `features.md`.
   - Update `architecture.md` if structural components were removed.
   - Log the removal in `history.md`.

---

## Skill Execution Rules

1. **Never invent facts**: Only reference features, files, and structures that verifiably exist.
2. **Read memory first**: Always consult project memory for context before making changes.
3. **Follow conventions**: Adhere to `conventions.md` for code style, naming, and patterns.
4. **Minimize blast radius**: Make the smallest change that correctly solves the problem.
5. **Preserve history**: When removing or replacing, archive rather than silently delete.
6. **No unrelated changes**: Only modify files directly related to the current task.
