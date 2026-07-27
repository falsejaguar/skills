---
name: bash
description: A shell script execution server that allows AI models to execute shell scripts and commands.  Use for bash execution.
allowed-tools: bash
---

How to use the bash mcp tool.

Features:

Execute shell scripts with full shell capabilities
Configurable shell command (default: sh -c)
Separate stdout and stderr capture
Exit code reporting
Configurable timeout (default: 30 seconds)
JSON schema validation for inputs/outputs
Tool:

execute_command - Execute a shell script and return the output, exit code, and any errors
Configuration:

SHELL_CMD - Environment variable to set the shell command to use (default: sh -c). Can include arguments, e.g., bash -x or zsh
SHELL_TIMEOUT_DISABLED - Set to true to disable the timeout completely (default: timeout is 30 seconds)
SHELL_TIMEOUT - Environment variable to set the timeout in seconds (default: 30 seconds)
SHELL_WORKING_DIR - Environment variable to set the working directory for script execution (default: current directory)
Input Format:

{
  "script": "ls -la /tmp",
  "timeout": 30
}
Output Format:

{
  "script": "ls -la /tmp",
  "stdout": "total 1234\ndrwxrwxrwt...",
  "stderr": "",
  "exit_code": 0,
  "success": true,
  "error": ""
**Docker Image:**
```bash
docker run -e SHELL_CMD=bash ghcr.io/mudler/mcps/shell:latest
With timeout disabled:

docker run -e SHELL_CMD=bash -e SHELL_TIMEOUT_DISABLED=true ghcr.io/mudler/mcps/shell:latest
With custom working directory:

docker run -e SHELL_CMD=bash -e SHELL_WORKING_DIR=/workspace ghcr.io/mudler/mcps/shell:latest
