---
name: project-structure-skill
description: Creates and maintains project directory structures under /main/projects.
---

Tool Usage:
- Use the filesystem MCP server for all file and directory operations.
- Use bash MCP server only when shell commands are required.

Behavior:
- When creating a project, call filesystem.writeFile to create plan.md and todo.md.
- Use filesystem.makeDirectory to create notes/, src/, and assets/.
- Use filesystem.readFile to check existing structure.
- Never attempt to perform file operations without using filesystem or bash.
- Update TODO after each step is accomplished to ensure proper step tracking.
  
Instructions to Agent:
- Do NOT attempt to execute this skill directly.
- Instead, generate a plan that uses filesystem and bash tools to perform the actions.

Triggers:
- “start a project”
- “create a project”
- “new project”
- “set up project”
- “initialize project”

Directory Structure:
- /main/projects/<project_name>/
    plan.md
    todo.md
    notes/
    src/
    assets/

plan.md template:
# Project Plan
## Overview
(brief description)

## Current Status
Not started.

## Next Steps
- Define tasks in todo.md

todo.md template:
# TODO
- [ ] Initial setup
