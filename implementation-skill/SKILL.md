---
name: implementation-skill
description: A universal implementation skill that takes a completed project plan and scaffolding and turns it into a fully implemented, functional project. This skill generates complete source code for every file, writes the code using filesystem.writeFile, installs dependencies when needed, compiles languages that require compilation, runs the project when appropriate, and iterates until the project builds and executes successfully.
---

# Implementation Skill

## Purpose
This skill performs full project implementation after planning and scaffolding are complete. It generates complete source code for every file, writes the code using filesystem.writeFile or other more powerful available skills, installs dependencies when required, compiles languages that need compilation, runs the project when appropriate, and iterates until the project is fully functional.

## Behavior

### 1. Detect readiness for implementation
Begin implementation only after:
- The project plan is complete.
- The directory structure and file scaffolding exist.

### 2. Generate complete code for each file
For every file listed in the project plan:
- Generate full, functional code appropriate to the project's language, framework, and requirements.
- Ensure the code is complete, not placeholder or partial.
- Write the code into the files using bash skill or filesystem skill.

### 3. Handle dependencies
If the project requires dependencies:
- Identify the correct dependency manager for the language (e.g., pip, cargo, npm, go mod, etc.).
- Use skills to install dependencies.
- If installation fails, diagnose the issue, adjust the dependency list or code, and retry.

### 4. Handle compilation (if required)
If the language requires compilation (e.g., C, C++, Rust, Go, Java):
- Use bash.run to invoke the correct compiler or build system.
- If compilation fails:
  - Read the error output.
  - Diagnose the problem.
  - Regenerate or patch the relevant code.
  - Rewrite the corrected code using filesystem.writeFile.
  - Recompile until successful.

### 5. Handle execution (if appropriate)
If the project is meant to run:
- Use tools to execute the program.
- If runtime errors occur:
  - Capture the error output.
  - Diagnose the issue.
  - Regenerate or patch the relevant code.
  - Rewrite the corrected code using available skills and tools.
  - Re-run until successful.

### 6. Iterate until completion
Continue implementing, compiling, fixing, and running until:
- All files contain complete, correct code.
- All dependencies are installed.
- The project compiles successfully (if applicable).
- The project runs without errors (if applicable).
- The implementation is fully complete.

## Requirements
- Never leave files empty.
- Never stop after scaffolding.
- Always proceed to full implementation unless the user explicitly requests only planning.
- Always fix compilation or runtime errors automatically.
- Always write code using the best available tool, never inline in the agent output.
- Always use skills and tools to handle dependency installation, compilation, and execution.


