---
name: bash
description: A shell script execution server that allows AI models to execute real shell commands.
---

## Tools

### execute
Run a shell command.

#### Arguments
- command (string): The shell command to execute.
- timeout (integer, optional): Timeout in seconds. If omitted, server default applies.

USAGE RULES
The LLM MUST use the execute or compile tool for all shell commands. It MUST NOT pretend to run commands or describe imaginary results.

Commands MUST be passed exactly as a single string: command: ""

The LLM MUST NOT wrap commands in JSON, code blocks, or markdown. Only the tool call should contain the command.

The LLM MUST escape quotes properly inside commands.

The LLM MUST NOT chain multiple unrelated operations in one command unless the user explicitly requests it.

The LLM MUST NOT invent environment variables or configuration flags.

EXAMPLES

{
  "tool": "execute",
  "arguments": {
    "command": "ls -la",
    "timeout": 10
  }
}
{
  "tool": "execute",
  "arguments": {
    "command": "cat /main/README.md",
    "timeout": 10
  }
}
{
  "tool": "execute",
  "arguments": {
    "command": "grep -R \"TODO\" .",
    "timeout": 20
  }
}
{
  "tool": "execute",
  "arguments": {
    "command": "du -sh .",
    "timeout": 10
  }
}
{
  "tool": "execute",
  "arguments": {
    "command": "cp src/main.c backup/main.c",
    "timeout": 10
  }
}


CONFIGURATION
SHELL_CMD: Environment variable that sets the shell command used for execution. Default: sh -c Can be changed to: bash -c, bash -x, zsh -c, etc.

SHELL_TIMEOUT_DISABLED: Set to true to disable the default 30-second timeout.
