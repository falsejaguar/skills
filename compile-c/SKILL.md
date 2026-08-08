---
name: compile-c
description: compile c
---
## Tools
Example:
{
  "tool": "compile",
  "arguments": {
    "command": "gcc *.c -o main",
    "timeout": 30
  }
}
{
  "tool": "compile",
  "arguments": {
    "command": "make",
    "timeout": 60
  }
}
{
  "tool": "compile",
  "arguments": {
    "command": "gcc src/main.c src/util.c -o bin/app",
    "timeout": 45
  }
}
{
  "tool": "compile",
  "arguments": {
    "command": "gcc -Wall -Wextra -O2 *.c -o main",
    "timeout": 45
  }
}


{
  "tool": "compile",
  "arguments": {
    "command": "cmake -S . -B build && cmake --build build",
    "timeout": 120
  }
}

### compile
Run a shell command and return stdout, stderr, and exit code.

#### Arguments
- command (string): The shell command to execute.
- timeout (integer, optional): Timeout in seconds.
When the user mentions compiling, building, gcc, make, or errors,
the agent MUST call the correct tool: execute or compile.

The agent MUST NOT answer narratively until after executing the execute or compile command.


If the user does not specify a command, the agent MUST run:
gcc *.c -o main
