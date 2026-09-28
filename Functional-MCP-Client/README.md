# MCP Client Lab

This project teaches you how to build Model Context Protocol (MCP) clients.

## What You'll Learn
- STDIO transport connections
- Tool invocation patterns
- Resource reading via URIs
- Prompt template usage

✅ Created a lightweight MCP client with STDIO transport
✅ Connected to a FastMCP server
✅ Discovered and invoked tools (echo, write_file)
✅ Listed and read resources via URI templates
✅ Retrieved and used prompt templates
✅ Built a simple command-line interface
✅ Understood resource template patterns
✅ Worked with real resource files

Key concepts
STDIO Transport - Local communication via stdin/stdout, perfect for development

ClientSession - Manages all MCP protocol details (JSON-RPC, message IDs, and so on)

FastMCP - Simplifies server creation with decorators and automatic schema generation

Tools - Server actions the client can invoke with arguments

Resource Templates - URI patterns such as file://resources/{filename} that dynamically expose multiple resources

Prompts - Server templates the client can render with arguments

You now have a solid foundation for building MCP-enabled applications!
