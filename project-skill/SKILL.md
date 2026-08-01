name: project-skill
description: A skill for scaffolding project structures using real filesystem operations.

requires:
  - bash-skill

instructions: |
  This skill provides structured project scaffolding capabilities. The LLM must
  NEVER simulate filesystem changes. It must NEVER claim to create directories,
  files, or project layouts on its own. All filesystem operations MUST be
  performed using the bash tool provided by bash-skill.

  ---------------------------------------------------------------------------
  TOOL USAGE RULES
  ---------------------------------------------------------------------------

  1. The LLM MUST use the bash tool for all filesystem operations.
     It MUST NOT describe imaginary directory creation or pretend to write files.

  2. Directory creation:
       Use the bash tool with:
         command: "mkdir -p <directory_path>"

  3. File creation:
       Use the bash tool with:
         command: "touch <file_path>"

  4. Writing content to a file:
       Use the bash tool with:
         command: "printf \"%s\" '<content>' > <file_path>"

     - The LLM MUST escape quotes properly.
     - The LLM MUST NOT simulate file content creation.

  5. Creating nested project structures:
       The LLM MUST issue multiple bash tool calls, one per operation.
       It MUST NOT output a fake directory tree unless explicitly asked to
       *describe* a structure rather than *create* it.

  6. When the user requests a project scaffold:
       - The LLM MUST ask clarifying questions if the structure is ambiguous.
       - The LLM MUST generate a step-by-step plan.
       - The LLM MUST execute the plan using bash tool calls only.

  7. The LLM MUST NOT invent tools, schemas, or capabilities not defined in
     bash-skill. It MUST NOT call tools from other skills unless explicitly
     required.

  ---------------------------------------------------------------------------
  EXAMPLES
  ---------------------------------------------------------------------------

  Example: Create a directory
    Use bash tool:
      command: "mkdir -p src/components"

  Example: Create a file
    Use bash tool:
      command: "touch README.md"

  Example: Write content to a file
    Use bash tool:
      command: "printf \"%s\" \"# My Project\" > README.md"

  ---------------------------------------------------------------------------
  SUMMARY
  ---------------------------------------------------------------------------

  - All filesystem actions MUST use bash-skill.
  - No hallucinated directory creation.
  - No imaginary file writing.
  - No simulated scaffolding.
  - Only real bash tool calls.
