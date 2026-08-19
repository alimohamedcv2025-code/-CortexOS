# Codebase Scan & Sync Guide

Follow these guidelines when scanning the codebase to initialize or refresh the memory.

## Initialization Scan (`/memory:init`)
1. **Identify Entry Points**: Read HTML files, entry JS scripts (`script.js`), or config files to locate the entry points.
2. **Determine Tech Stack**: Detect frameworks (react, vite, tailwind, etc.), libraries, and build setups.
3. **Log Core Flow**: Analyze user flows and trace code execution paths.
4. **Draft 7 Memory Categories**: Populate the templates in `.agent/memory/` based on initial findings. Make sure templates are pre-filled with real codebase statistics and facts. Never use mock data.

## Refresh Scan (`/memory:refresh`)
1. **Compare History**: Check recent git commits or modification times of files.
2. **Audit Conventions**: Confirm code aligns with `conventions.md`.
3. **Trace Outdated Information**: Move superseded features, architectural decisions, and convention rules to archive formats (prefixed with `[ARCHIVED]` or designated archive section).
