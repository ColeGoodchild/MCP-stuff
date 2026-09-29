Built a complete MCP system using HTTP transport with advanced features including roots security and sampling concepts. Including four interconnected components:

1. HTTP MCP Server - A FastMCP server that:

Uses HTTP transport for remote accessibility
Implements roots-based filesystem security
Provides tools, resources, and prompts
Demonstrates where sampling would integrate

2. Base HTTP Client - A reusable client library that:

Connects to HTTP MCP servers via HTTP transport
Implements all MCP protocol methods
Handles lazy initialization for async contexts
Serves as a foundation for specialized applications

3. GUI Client Application - An interactive Gradio interface that:

Provides visual access to tools, resources, and prompts
Displays roots configuration and security boundaries
Enables manual testing and exploration
Demonstrates client-side MCP interactions

4. AI Host Application - An LLM-powered assistant that:

Integrates OpenAI GPT-4o-mini with MCP tools
Uses synthetic tools to expose resources and prompts
Enables natural language interactions with the MCP server
Demonstrates the full power of combining LLMs with MCP

### Key Concepts Mastered: ###

1. HTTP Transport: how MCP servers can run as HTTP services rather than just local subprocesses. This enables:

Remote server deployment
Multiple concurrent clients
Standard web protocols for integration
Better scalability and monitoring

2. Roots Security: Implemented filesystem security boundaries that:

Prevent unauthorized file access
Enable safe multi-tenant deployments
Protect sensitive data from path traversal attacks
Allow clients to specify allowed directories

3. Sampling Architecture: Explored how servers can request LLM capabilities from clients:

Servers don't need their own API keys
Clients maintain control over model selection and costs
Human-in-the-loop approval for security
Enables agentic behavior in servers

4. MCP Protocol Components: Worked with all three MCP primitives:

Tools: Active operations with parameters and results
Resources: Template-based URIs for accessing data
Prompts: Reusable templates with argument substitution

5. Code Architecture: Applied clean software design patterns:

Base class with protocol logic
Inheritance for code reuse
Separation of concerns (protocol vs presentation)
Async/await for modern Python concurrency

### Architecture Benefits ###
Remote Accessibility:

HTTP server can be accessed from anywhere
Multiple clients can connect simultaneously
Enables cloud deployment and microservice architecture
Integrates with standard web infrastructure

Security Boundaries:

Roots prevent unauthorized file access
Path validation stops directory traversal attacks
Clean separation between server and client trust domains
Multi-tenant safe filesystem operations

Flexible LLM Integration:

Sampling allows servers to request LLM help when needed
Clients maintain control over AI costs and model selection
Human-in-the-loop ensures security and oversight
Enables agentic server behavior without embedding LLM keys

Code Reusability:

Base client provides all protocol logic
Both applications inherit seamlessly
No code duplication between GUI and AI host
Easy to add new client applications
Key Patterns

HTTP Transport for MCP:


python

# Server runs as HTTP service
mcp = FastMCP("HTTP Server")
mcp.run(transport="http", host="127.0.0.1", port=8000)

# Client connects via Streamable HTTP (FastMCP uses /mcp endpoint)
from mcp.client.streamable_http import streamablehttp_client
mcp_url = f"{server_url}/mcp"  # Append /mcp endpoint
read, write, _ = await streamablehttp_client(mcp_url)
session = ClientSession(read, write)
Roots Security:


### Key Patterns ### 

1. HTTP Transport for MCP:

python

# Server runs as HTTP service
mcp = FastMCP("HTTP Server")
mcp.run(transport="http", host="127.0.0.1", port=8000)

# Client connects via Streamable HTTP (FastMCP uses /mcp endpoint)
from mcp.client.streamable_http import streamablehttp_client
mcp_url = f"{server_url}/mcp"  # Append /mcp endpoint
read, write, _ = await streamablehttp_client(mcp_url)
session = ClientSession(read, write)
Roots Security:

2. Roots Security
   
python

def is_within_roots(filepath: str, roots_dir: str) -> bool:
    """Validate file access against roots directory."""
    abs_file = Path(filepath).resolve()
    abs_roots = Path(roots_dir).resolve()
    return abs_file.is_relative_to(abs_roots)
    
3. Sampling Concept:

python

# Server would send sampling request to client
# Client shows approval dialog to user
# If approved, client calls LLM and returns result
# Server uses LLM response to complete task

4. Synthetic Tools Pattern:

python

# Expose resources and prompts as OpenAI tools
get_available_tools():
  - Add real MCP tools
  - Add synthetic mcp_list_resources
  - Add synthetic mcp_read_resource
  - Add synthetic mcp_list_prompts
  - Add synthetic mcp_get_prompt


### Ways to Build on This

1. Implement full sampling approval workflow with user dialogs
2. Add authentication and HTTPS for production deployment
3. Create new client apps (CLI, mobile) by inheriting from base
4. Apply HTTP transport and roots patterns to your own MCP servers
   
You now have a solid foundation for building production-grade MCP applications with remote capabilities and enterprise security!
