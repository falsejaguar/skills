---
name: filesystem
description: Full filesystem control inside /main using Mudler's filesystem MCP server.   Use when user asks "create a file" "write" "read" "check files" "check folders" "create a new folder"
allowed-tools: filesystem
---

Tools:

read - Read file with line numbers, supports optional offset and limit for reading specific line ranges
write - Write content to a file, creates parent directories if needed, overwrites existing files
edit - Replace old string with new string in a file, old string must be unique unless all=true
glob - Find files by glob pattern, sorted by modification time (newest first)
grep - Search files for regex pattern, returns up to 50 matches

Ensure all tool calls contain all required fields like path.

Read File Input Format:

{
  "path": "/path/to/file.txt",
  "offset": 0,
  "limit": 50
}
Read File Output Format:

{
  "content": "   1| line one\n   2| line two",
  "total_lines": 100,
  "success": true
}
Write File Input Format:

{
  "path": "/path/to/file.txt",
  "content": "file content here"
}
Edit File Input Format:

{
  "path": "/path/to/file.txt",
  "old": "old text",
  "new": "new text",
  "all": false
}
Glob Files Input Format:

{
  "pat": "**/*.go",
  "path": "."
}
Grep Files Input Format:

{
  "pat": "func main",
  "path": "."
}