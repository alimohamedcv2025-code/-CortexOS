# Memory System Configuration Schema

The `.agent/memory/config.yml` governs the behavior of the project memory skill.

## Schema Specification

- `version`: String. The version of the project-memory specification.
- `project_name`: String. The name of the project.
- `auto_write`: Object. Defines automatic memory update permissions.
  - `enabled`: Boolean. If false, only explicit commands change memory.
  - `allow_external_skills`: Boolean. Enables/disables automatic edits triggered by other tools/skills.
  - `categories`: Map of `filename` to Boolean. Sets auto-write on/off per memory category.
  - `skills`: Map of `skill_name` to Boolean. Restricts or allows specific skills to auto-update memory.
- `rules`: Object. Strict runtime constraints for the agent.
  - `never_invent_facts`: Boolean (Default: true)
  - `prefer_codebase_evidence`: Boolean (Default: true)
  - `preserve_history`: Boolean (Default: true)
  - `archive_before_delete`: Boolean (Default: true)
