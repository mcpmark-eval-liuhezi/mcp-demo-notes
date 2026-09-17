# MCP Demo Notes

Prep notes for a team intro session on the Model Context Protocol (MCP), delivered Friday, September 18, 2026.

## What MCP is for

The Model Context Protocol (MCP) is an open-source standard for connecting AI applications to external systems. Using MCP, AI applications like Claude or ChatGPT can connect to data sources (e.g. local files, databases), tools (e.g. search engines, calculators), and workflows (e.g. specialized prompts) — enabling them to access key information and perform tasks.

A helpful way to explain it to a non-technical audience: MCP is like a **USB-C port for AI applications**. Just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems.

Architecturally, MCP is client-server based. An MCP host (an AI application such as Claude Desktop or Visual Studio Code) creates one MCP client per MCP server it connects to, and each MCP server provides context to its client. Servers can run locally (STDIO transport) or remotely (Streamable HTTP transport). The protocol itself runs over JSON-RPC 2.0 and is split into a data layer (discovery, capabilities, and the core primitives) and a transport layer (connection establishment, message framing, and authorization).

## Core server primitives

An MCP server exposes three core primitives:

| Primitive | What it is | Examples | Who controls it |
| --- | --- | --- | --- |
| **Tools** | Functions that your LLM can actively call, and decides when to use them based on user requests. Tools can write to databases, call external APIs, modify files, or trigger other logic. | Search flights, send messages, create calendar events | Model |
| **Resources** | Passive data sources that provide read-only access to information for context, such as file contents, database schemas, or API documentation. | Retrieve documents, access knowledge bases, read calendars | Application |
| **Prompts** | Pre-built instruction templates that tell the model to work with specific tools and resources. | Plan a vacation, summarize my meetings, draft an email | User |

Each primitive type has associated methods for discovery (`*/list`), retrieval (`*/get`), and in some cases execution (`tools/call`). For example, a client can first list available tools with `tools/list` and then execute one with `tools/call`. This design allows listings to be dynamic.

As a concrete example, an MCP server that provides context about a database can expose tools for querying the database, a resource that contains the schema of the database, and a prompt that includes few-shot examples for interacting with those tools.

## Sources

- [Understanding MCP servers](https://modelcontextprotocol.io/docs/2026-07-28/learn/server-concepts) — official Model Context Protocol documentation (primary source for the server primitives)
- [Architecture overview](https://modelcontextprotocol.io/docs/2026-07-28/learn/architecture) — official Model Context Protocol documentation
- [What is the Model Context Protocol (MCP)?](https://modelcontextprotocol.io/introduction) — official Model Context Protocol documentation
