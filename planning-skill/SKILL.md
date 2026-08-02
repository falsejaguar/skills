---
name: planning-skill
description: Maintains todo.md and plan.md inside each project and generates actionable plans.
---

Behavior:
- Add tasks to todo.md.
- Mark tasks complete.
- Remove tasks.
- Rewrite plan.md sections when progress changes.
- Generate step-by-step plans for coding tasks.
- Keep plan.md synchronized with todo.md.

Triggers:
- “add a task”
- “update the plan”
- “mark this done”
- “create a TODO”
- “what’s next”
- “plan this out”

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