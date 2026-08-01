---
name: project-skill
description: A high-level orchestration skill for creating, resuming, and maintaining structured software projects using MCP servers. This skill provides guidance and workflow logic; actual filesystem, git, and shell operations are performed by their respective MCP tools.
---

instructions: |
PURPOSE
This skill coordinates multiple MCP servers (filesystem, bash, git, etc.) to create, resume, and maintain software projects across iterations. It does NOT perform filesystem operations itself. It does NOT simulate directory creation, file writing, or git actions. It delegates all real operations to the appropriate MCP tools.

TOOL SELECTION RULES
The agent MUST choose the correct MCP tool based on the operation:

- Use the filesystem tool for:
    * creating directories
    * creating files
    * writing file contents
    * reading files
    * deleting files or directories

- Use the bash tool for:
    * shell commands
    * environment inspection
    * running build tools or CLIs

- Use the git tool for:
    * initializing repositories
    * committing changes
    * checking status
    * creating branches

- Use other MCP tools when appropriate (python, etc.).
The agent MUST NOT redirect filesystem operations through bash unless the filesystem tool cannot perform the requested action.

PROJECT CREATION WORKFLOW
When the user requests a new project:

1. Ask clarifying questions if the project structure is ambiguous.
2. Generate a clear plan describing:
     - directories to create
     - files to create
     - initial content to write
     - optional git initialization
3. Execute the plan using MCP tools.
4. Write a `.project-meta.json` file containing:
     - project name
     - creation timestamp
     - tool versions (optional)
     - list of generated directories and files
     - iteration counter starting at 1
PROJECT RESUMPTION WORKFLOW
When resuming a project:

1. Locate `.project-meta.json` using the filesystem tool.
2. Read and parse the metadata.
3. Increment the iteration counter.
4. Review existing files and directories.
5. Ask the user what they want to modify or extend.
6. Generate a plan for the requested changes.
7. Execute changes using MCP tools.
8. Update `.project-meta.json` with:
     - new iteration number
     - list of modified files
     - list of new files
     - timestamp
TODO / TASK MANAGEMENT
The agent MUST NOT invent TODO items.

The agent MAY manage TODOs ONLY if: - the user explicitly requests TODO tracking, OR - the project contains a TODO.md file.

TODOs MUST be stored in: - TODO.md (markdown), OR - .project-meta.json under "tasks".

The agent MUST NOT create TODOs on its own.

SAFETY & NON-HALLUCINATION RULES
The agent MUST NOT simulate filesystem changes.
The agent MUST NOT output imaginary directory trees unless the user asks for a description rather than creation.
The agent MUST NOT invent project metadata.
The agent MUST NOT invent tool schemas.
The agent MUST NOT invent TODOs.
The agent MUST NOT claim success without calling the appropriate MCP tool.
EXAMPLES
Example: Create a project Plan: - Create directory: src/ - Create file: src/main.py - Write content to src/main.py - Create .project-meta.json Execute using filesystem tool.

Example: Resume a project - Read .project-meta.json - Increment iteration - Ask user what to modify - Apply changes using filesystem + git tools - Update metadata
