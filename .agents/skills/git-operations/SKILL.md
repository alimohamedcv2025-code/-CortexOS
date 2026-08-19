---
name: git-operations
description: Git workflow wrappers for status, diff, commit, branch, log, undo, and sync operations with safety checks.
---

# Git Operations Skill

Provides safe, structured wrappers around common Git operations. Includes safety checks, conventional commit message generation, and formatted output.

## Memory Integration

This skill is a **read-write** consumer of `.agent/memory/`.

Before any auto-write to memory:
1. Read `.agent/memory/config.yml`.
2. Confirm `auto_write.enabled == true`.
3. Confirm `auto_write.allow_external_skills == true`.
4. Confirm `auto_write.skills.git-operations != false`.
5. Confirm the target `auto_write.categories.<file> == true`.
6. If any check fails, skip auto-write and suggest running `/memory-update`.

---

## Commands

### `/git-status`

**Purpose**: Show the current working tree status and staged changes.

**Execution Flow**:
1. Run `git status --porcelain` and `git status`.
2. Parse and present results in a structured format:
   - Staged changes (ready to commit).
   - Unstaged modifications.
   - Untracked files.
3. Summarize: total files changed, additions, deletions.

---

### `/git-diff`

**Purpose**: Show diffs for working changes, staged changes, or between branches/commits.

**Execution Flow**:
1. Determine diff scope from user input:
   - Working directory: `git diff`
   - Staged: `git diff --staged`
   - Between refs: `git diff <ref1>..<ref2>`
   - Specific file: `git diff -- <file>`
2. Present the diff with syntax context.
3. Summarize: files changed, insertions, deletions.

---

### `/git-commit`

**Purpose**: Stage and commit changes with a well-crafted conventional commit message.

**Execution Flow**:
1. **Check status**: Run `git status` to see what's changed.
2. **Stage files**: Stage the relevant files. If the user specifies files, stage those. Otherwise, present the changes and confirm what to stage.
3. **Generate commit message**: Create a conventional commit message:
   - Format: `<type>(<scope>): <description>`
   - Types: `feat`, `fix`, `refactor`, `docs`, `style`, `test`, `chore`, `perf`, `ci`, `build`
   - Description should be concise and imperative.
4. **Confirm**: Present the staged files and proposed message to the user before committing.
5. **Commit**: Execute `git commit -m "<message>"`.
6. **Update memory** (if auto-write allowed):
   - Add a brief entry to `history.md`.

---

### `/git-branch`

**Purpose**: Create, switch, list, or delete branches.

**Execution Flow**:
1. Determine the operation from user input:
   - **List**: `git branch -a` — show local and remote branches.
   - **Create**: `git checkout -b <name>` — create and switch to a new branch.
   - **Switch**: `git checkout <name>` — switch to an existing branch.
   - **Delete**: `git branch -d <name>` — delete a merged branch (use `-D` only if user confirms force).
2. Present the result: current branch, list of branches, or confirmation.

---

### `/git-log`

**Purpose**: Show recent commit history.

**Execution Flow**:
1. Run `git log --oneline --graph -n 20` (or user-specified count).
2. Present the log in a readable format.
3. If the user asks for details on a specific commit, show the full commit info with `git show <hash>`.

---

### `/git-undo`

**Purpose**: Undo the last commit, unstage files, or discard changes.

**Execution Flow**:
1. Determine the undo operation from user input:
   - **Undo last commit** (keep changes): `git reset --soft HEAD~1`
   - **Undo last commit** (discard changes): `git reset --hard HEAD~1` — **requires explicit user confirmation**.
   - **Unstage file(s)**: `git restore --staged <file>`
   - **Discard working changes**: `git restore <file>` — **requires explicit user confirmation**.
2. **Safety check**: For destructive operations (`--hard`, discard), always show what will be lost and require confirmation.
3. Execute the operation.
4. **Update memory** (conditional, if auto-write allowed):
   - Log significant undos in `history.md`.

---

### `/git-sync`

**Purpose**: Pull from or push to remote, with conflict detection.

**Execution Flow**:
1. Determine the operation:
   - **Pull**: `git pull --rebase` (preferred) or `git pull --merge`.
   - **Push**: `git push origin <branch>`.
   - **Sync**: Pull then push.
2. **Pre-flight checks**:
   - Check for uncommitted changes before pull.
   - Check if the branch has an upstream remote.
3. Execute the operation.
4. **Handle conflicts**: If conflicts occur during pull, list conflicted files and advise the user on resolution.

---

## Skill Execution Rules

1. **Safety first**: Never run destructive git commands without explicit user confirmation.
2. **Show before executing**: Present what will happen before running write operations (commit, reset --hard, push --force).
3. **Conventional commits**: Always use conventional commit format unless the user specifies otherwise.
4. **No force push by default**: Never use `--force` unless the user explicitly requests it and confirms.
5. **Respect .gitignore**: Never suggest staging ignored files.
6. **No unrelated changes**: Only operate on the files and branches relevant to the user's request.
