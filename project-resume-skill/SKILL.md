---
name: project-resume-skill
description: Resumes work on existing projects by reading plan.md and todo.md.
---

Tool Usage:
- Use filesystem.listDirectory to find project folders.
- Use filesystem.readFile to load plan.md and todo.md.
- Use filesystem.writeFile to update plan.md or todo.md.

Behavior:
- Identify the most recently modified project using filesystem.stat.
- Parse TODO checkboxes from todo.md.
- Suggest next steps based on incomplete tasks.

Instructions to Agent:
- Do NOT execute this skill directly.
- Instead, produce a sequence of filesystem tool calls to inspect project files.
