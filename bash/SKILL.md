---
name: bash
description: A shell script execution server that allows AI models to execute real shell commands.
allowed-tools: bash
---

## Tools

### execute
Run a shell command.

#### Arguments
- command (string): The shell command to execute.
- timeout (integer, optional): Timeout in seconds. If omitted, server default applies.

USAGE RULES
The LLM MUST use the bash tool for all shell commands. It MUST NOT pretend to run commands or describe imaginary results.

Commands MUST be passed exactly as a single string: command: ""

The LLM MUST NOT wrap commands in JSON, code blocks, or markdown. Only the tool call should contain the command.

The LLM MUST escape quotes properly inside commands.

The LLM MUST NOT chain multiple unrelated operations in one command unless the user explicitly requests it.

The LLM MUST NOT invent environment variables or configuration flags.

EXAMPLES
Example: Create a directory Use bash tool: command: "mkdir -p src"

Example: Create a file command: "touch README.md"

Example: Write content to a file command: "printf "%s" "Hello" > README.md"

Example: List files command: "ls -la"

CONFIGURATION
SHELL_CMD: Environment variable that sets the shell command used for execution. Default: sh -c Can be changed to: bash -c, bash -x, zsh -c, etc.

SHELL_TIMEOUT_DISABLED: Set to true to disable the default 30-second timeout.
