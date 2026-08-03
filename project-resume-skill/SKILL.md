---
name: project-resume-skill
description: Resumes work on existing projects by reading plan.md and todo.md.
---

Tool Usage:
Before scanning project folders, check /main/projects/_index/active.json. If it exists, resume the project listed under last_active. If missing, fall back to scanning project folders.
- Use filesystem.listDirectory to find project folders.
- Use filesystem.readFile to load plan.md and todo.md.
- Use filesystem.writeFile to update plan.md or todo.md.

Behavior:
- Identify the most recently modified project using filesystem.stat and/or active.json.
- Parse TODO checkboxes from todo.md.
- Suggest next steps based on incomplete tasks.
- Begin work and update TODO checkboxes after each step and ensure proper step tracking

Instructions to Agent:
- Do NOT execute this skill directly.
- Instead, produce a sequence of filesystem tool calls to inspect project files.
