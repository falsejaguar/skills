---
name: project-resume-skill
description: Automatically resumes work on existing projects by reading their files.
---

Behavior:
- Scan /main/projects for all project folders.
- Identify the most recently modified project.
- Read plan.md and todo.md.
- Determine current progress based on:
    - Completed tasks
    - Remaining tasks
    - Notes
- Provide a summary of the project’s current state.
- Suggest the next actionable step.
- When user says “resume”, “continue”, “pick up where we left off”, resume the active project.

Triggers:
- “resume”
- “continue”
- “pick up where we left off”
- “what was I doing”
- “open my last project”

Resume Logic:
1. Find most recently modified project folder.
2. Load plan.md and todo.md.
3. Parse TODO checkboxes.
4. Identify incomplete tasks.
5. Present next steps.
6. Re-enter the project context.

Notes:
- If no projects exist, inform the user.
- If multiple projects exist, allow user to choose.