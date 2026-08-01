name: filesystem
description: A skill describing how to use the filesystem MCP server to perform
real file and directory operations. This skill provides usage guidance only;
all actual filesystem actions are performed by the filesystem MCP tool.

instructions: |
  ---------------------------------------------------------------------------
  PURPOSE
  ---------------------------------------------------------------------------
  This skill explains how the agent should use the filesystem MCP tool to
  perform real filesystem operations. It does NOT simulate filesystem changes.
  It does NOT redirect filesystem operations through bash. It does NOT invent
  schemas. It does NOT override the behavior of the filesystem MCP server.

  The filesystem MCP server is responsible for:
    - creating directories
    - creating files
    - writing file contents
    - reading file contents
    - deleting files or directories
    - listing directory contents

  ---------------------------------------------------------------------------
  TOOL USAGE RULES
  ---------------------------------------------------------------------------
  The agent MUST use the filesystem MCP tool for all filesystem operations.

  The agent MUST NOT:
    - simulate directory creation
    - simulate file creation
    - output imaginary directory trees
    - pretend to write or delete files
    - claim success without calling the filesystem tool
    - redirect filesystem operations through bash unless explicitly required

  The agent MAY use bash for:
    - shell commands
    - build tools
    - environment inspection
    - running CLIs

  But NOT for filesystem operations that the filesystem MCP tool already
  supports.

  ---------------------------------------------------------------------------
  OPERATION GUIDANCE
  ---------------------------------------------------------------------------

  Create a directory:
    Use the filesystem tool with:
      action: "create_directory"
      path: "<directory_path>"

  Create a file:
      action: "create_file"
      path: "<file_path>"

  Write content to a file:
      action: "write_file"
      path: "<file_path>"
      content: "<content>"

  Append content to a file:
      action: "append_file"
      path: "<file_path>"
      content: "<content>"

  Read a file:
      action: "read_file"
      path: "<file_path>"

  Delete a file:
      action: "delete_file"
      path: "<file_path>"

  Delete a directory:
      action: "delete_directory"
      path: "<directory_path>"

  List directory contents:
      action: "list_directory"
      path: "<directory_path>"

  ---------------------------------------------------------------------------
  PROJECT WORKFLOW INTEGRATION
  ---------------------------------------------------------------------------
  When used by project-skill:

    - The filesystem tool MUST be used to create project structures.
    - The filesystem tool MUST be used to read and update .project-meta.json.
    - The filesystem tool MUST be used to manage TODO.md if present.
    - The agent MUST NOT invent project metadata.
    - The agent MUST NOT invent TODOs.
    - The agent MUST NOT simulate project scaffolding.

  The filesystem skill does NOT enforce project logic; it only ensures correct
  usage of the filesystem MCP server.

  ---------------------------------------------------------------------------
  SAFETY RULES
  ---------------------------------------------------------------------------
  - The agent MUST NOT invent tool schemas.
  - The agent MUST NOT invent fields not supported by the filesystem MCP tool.
  - The agent MUST NOT hallucinate directory trees or file contents.
  - The agent MUST NOT claim success without calling the filesystem tool.
  - The agent MUST ask clarifying questions if paths or structures are unclear.

  ---------------------------------------------------------------------------
  EXAMPLES
  ---------------------------------------------------------------------------

  Example: Create a directory
    action: "create_directory"
    path: "src/components"

  Example: Write content to a file
    action: "write_file"
    path: "README.md"
    content: "# My Project"

  Example: Read metadata file
    action: "read_file"
    path: ".project-meta.json"
