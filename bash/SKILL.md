name: bash
description: A shell script execution server that allows AI models to execute real shell commands.

allowed-tools:
  - bash

instructions: |
  This skill exposes a bash execution tool that MUST be used for all shell
  commands. The LLM MUST NOT simulate command execution, MUST NOT invent tools,
  and MUST NOT describe imaginary filesystem changes. All shell actions MUST be
  performed using the bash tool defined below.

  ---------------------------------------------------------------------------
  TOOL INTERFACE
  ---------------------------------------------------------------------------

  Tool name: bash
  Action: execute_command

  Input schema:
    {
      "command": "string"
    }

  Output schema:
    {
      "stdout": "string",
      "stderr": "string",
      "exit_code": "number"
    }

  ---------------------------------------------------------------------------
  USAGE RULES
  ---------------------------------------------------------------------------

  1. The LLM MUST use the bash tool for all shell commands.
     It MUST NOT pretend to run commands or describe imaginary results.

  2. Commands MUST be passed exactly as a single string:
       command: "<shell command>"

  3. The LLM MUST NOT wrap commands in JSON, code blocks, or markdown.
     Only the tool call should contain the command.

  4. The LLM MUST escape quotes properly inside commands.

  5. The LLM MUST NOT chain multiple unrelated operations in one command
     unless the user explicitly requests it.

  6. The LLM MUST NOT invent environment variables or configuration flags.

  ---------------------------------------------------------------------------
  EXAMPLES
  ---------------------------------------------------------------------------

  Example: Create a directory
    Use bash tool:
      command: "mkdir -p src"

  Example: Create a file
      command: "touch README.md"

  Example: Write content to a file
      command: "printf \"%s\" \"Hello\" > README.md"

  Example: List files
      command: "ls -la"

  ---------------------------------------------------------------------------
  CONFIGURATION
  ---------------------------------------------------------------------------

  SHELL_CMD:
    Environment variable that sets the shell command used for execution.
    Default: sh -c
    Can be changed to: bash -c, bash -x, zsh -c, etc.

  SHELL_TIMEOUT_DISABLED:
    Set to true to disable the default 30-second timeout.
