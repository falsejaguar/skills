---
name: compile-c
description: compile c
---

When the user mentions compiling, building, gcc, make, or errors,
the agent MUST call the bash tool.

The agent MUST NOT answer narratively until after executing the bash command.

The agent MUST run the exact compile command requested by the user.

If the user does not specify a command, the agent MUST run:
gcc *.c -o main
