# MCP Demo Notes

Prep notes for a team intro session on the **Model Context Protocol (MCP)**, delivered **Friday, September 18, 2026**.

## What MCP is for

The Model Context Protocol (MCP) is an **open standard for connecting AI applications to external systems**. Per the official documentation (Architecture overview), MCP is a client-server protocol in which an **MCP host** — an AI application like Claude Desktop, Claude Code, or Visual Studio Code — establishes connections to one or more **MCP servers**. The host creates one MCP client per server, and each client maintains a dedicated connection to its server. MCP focuses solely on the protocol for context exchange; it does not dictate how AI applications use LLMs or manage the provided context.

The official docs describe MCP with a **"USB-C port for AI applications"** analogy: just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems (data sources, tools, and workflows).

**Why MCP matters:**

- **Developers** — MCP reduces development time and complexity when building or integrating with AI applications or agents.
- **AI applications or agents** — MCP gives them access to an ecosystem of data sources, tools, and apps, which enhances capabilities and improves the end-user experience.
- **End-users** — MCP results in more capable AI applications that can access user data and take actions on the user's behalf when necessary.

MCP is an open protocol supported across a wide range of clients and servers — AI assistants like Claude and ChatGPT, and tools like Visual Studio Code, Cursor, and MCPJam all support MCP, so you can build once and integrate everywhere.

## Server primitives

MCP defines **three core primitives that servers can expose** (confirmed from the official "Architecture overview" documentation):

1. **Tools** — Executable functions that AI applications can invoke to perform actions (e.g., file operations, API calls, database queries). These are *model-initiated actions*.
2. **Resources** — Data sources that provide contextual information to AI applications (e.g., file contents, database records, API responses). These are *application-supplied context*.
3. **Prompts** — Reusable templates that help structure interactions with language models (e.g., system prompts, few-shot examples). These are *user-requested workflows*.

Each primitive type has associated methods for discovery (`*/list`), retrieval (`*/get`), and in some cases, execution (`tools/call`). MCP clients use the `*/list` methods to discover available primitives — for example, a client can first list all available tools (`tools/list`) and then execute them. MCP also defines primitives that clients can expose (e.g., elicitation for input from the user; sampling is deprecated as of protocol version 2026-07-28).

**Quick memory aid:** *tools are model-initiated actions, resources are application-supplied context, and prompts are user-requested workflows.*

## How it works (brief)

MCP uses **JSON-RPC 2.0** as its underlying RPC protocol. It consists of two layers:

- **Data layer** — Defines the JSON-RPC based protocol for client-server communication, including capability and version discovery, and core primitives such as tools, resources, prompts, and notifications.
- **Transport layer** — Defines the communication mechanisms: **Stdio transport** (standard input/output streams for local servers) and **Streamable HTTP transport** (HTTP POST with optional Server-Sent Events for remote servers, supporting OAuth).

## Sources

- [Architecture overview](https://modelcontextprotocol.io/docs/concepts/architecture) — official MCP documentation (primary source for what MCP is for and the three server primitives: tools, resources, prompts).
- [What is the Model Context Protocol (MCP)?](https://modelcontextprotocol.io/docs/getting-started/intro) — official MCP documentation (intro/USB-C analogy).
