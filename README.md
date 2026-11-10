# MCP Demo Notes

## What is MCP?

Based on the official MCP documentation ("What is the Model Context Protocol (MCP)?"):

The Model Context Protocol (MCP) is an **open-source standard for connecting AI applications to external systems**. Using MCP, AI applications like Claude or ChatGPT can connect to:

- **Data sources** — e.g. local files, databases
- **Tools** — e.g. search engines, calculators
- **Workflows** — e.g. specialized prompts

enabling them to access key information and perform tasks. The docs describe it simply as "a USB-C port for AI applications": just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems.

**Why it matters:** MCP reduces development time and complexity when building or integrating with AI applications or agents; it gives AI applications access to an ecosystem of data sources, tools, and apps; and it results in more capable AI applications for end users.

**Two layers power MCP:**

1. **Data layer** — a JSON-RPC 2.0-based protocol handling capability and version discovery, and the *core primitives* servers expose to clients.
2. **Transport layer** — defines the communication channels between clients and servers (STDIO for local servers; Streamable HTTP for remote servers).

## Server primitives

From the official documentation ("Understanding MCP servers"), MCP servers are programs that expose functionality to AI applications through standardized protocol interfaces. Servers provide their functionality through **three building blocks (primitives)**:

| Primitive | What it is | Who controls it |
| --- | --- | --- |
| **Tools** | Functions that the LLM can actively call — write to databases, call external APIs, modify files, or trigger other logic. | **Model** |
| **Resources** | Passive, read-only data sources providing context for the application — e.g. file contents, database schemas, API documentation. Each resource has a unique URI and declares a MIME type. | **Application** |
| **Prompts** | Pre-built instruction templates that tell the model how to work with specific tools and resources. | **User** |

A useful way to remember it: tools are *model-initiated actions*, resources are *application-supplied context*, and prompts are *user-requested workflows*.

## Sources

- [What is the Model Context Protocol (MCP)? — MCP Documentation](https://modelcontextprotocol.io/docs/getting-started/intro)
- [Understanding MCP servers — MCP Documentation](https://modelcontextprotocol.io/docs/2026-07-28/learn/server-concepts)
