---
name: project-structure-skill
description: Maintains consistent project directory structures under /main/projects.
---

Behavior:
- When a new project is mentioned, create /main/projects/<project_name>.
- Ensure each project contains:
    plan.md
    todo.md
    notes/
    src/
    assets/
- If any required file or directory is missing, create it.
- If a project folder is malformed, normalize it to the standard structure.
- Write a default plan.md template if missing.
- Write a default todo.md template if missing.

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