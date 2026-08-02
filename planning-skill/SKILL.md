---
name: planning-skill
description: Maintains todo.md and plan.md inside each project and generates actionable plans.
---

Tool Usage:
- Use filesystem.readFile to load todo.md and plan.md.
- Use filesystem.writeFile to update them.
- Use bash only for text manipulation when necessary.

Behavior:
- Add tasks by rewriting todo.md.
- Mark tasks complete by updating checkbox states.
- Synchronize plan.md with todo.md.

Instructions to Agent:
- Do NOT execute this skill directly.
- Instead, generate a plan that uses filesystem tool calls to modify the files.

TODO Format:
- [ ] Task description
- [x] Completed task

Plan Update Rules:
- When a TODO is added, append it to “Next Steps”.
- When a TODO is completed, move it to “Completed Work”.
- When major progress is made, update “Current Status”.

Example plan.md structure:
# Project Plan
## Overview
(description)

## Current Status
(summary)

## Next Steps
- (tasks from todo.md)

## Completed Work
- (completed tasks)
