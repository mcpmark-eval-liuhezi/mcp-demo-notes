# MCP Demo Notes

Prep notes for a team intro session on the **Model Context Protocol (MCP)**, delivered **Friday, September 18, 2026**.

## What MCP is for

The Model Context Protocol (MCP) is an **open-source standard for connecting AI applications to external systems**. Using MCP, AI applications like Claude or ChatGPT can connect to:

- **Data sources** (e.g. local files, databases)
- **Tools** (e.g. search engines, calculators)
- **Workflows** (e.g. specialized prompts)

…enabling them to access key information and perform tasks.

The official docs describe it as "a **USB-C port for AI applications**": just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems.

**Why MCP matters:**

- **Developers** — reduces development time and complexity when building or integrating AI applications or agents.
- **AI applications or agents** — gives them access to an ecosystem of data sources, tools and apps, enhancing their capabilities and improving the end-user experience.
- **End-users** — results in more capable AI applications that can access user data and take actions on the user's behalf when necessary.

## Server primitives

An MCP server exposes functionality through **three core building blocks (primitives)**, confirmed from the official documentation ("Understanding MCP servers"):

| Primitive | What it is | Who controls it |
| --- | --- | --- |
| **Tools** | Functions that your LLM can actively call, and decides when to use them based on user requests. Tools can write to databases, call external APIs, modify files, or trigger other logic. | **Model** |
| **Resources** | Passive data sources that provide read-only access to information for context, such as file contents, database schemas, or API documentation. Each resource has a unique URI (e.g. `file:///path/to/document.md`) and declares its MIME type. | **Application** |
| **Prompts** | Pre-built instruction templates that tell the model how to work with specific tools and resources. | **User** |

A useful way to remember it: **tools are *model-initiated actions*, resources are *application-supplied context*, and prompts are *user-requested workflows*.**

## Sources

- [What is the Model Context Protocol (MCP)?](https://modelcontextprotocol.io/docs/getting-started/intro) — official MCP documentation
- [Understanding MCP servers](https://modelcontextprotocol.io/docs/2026-07-28/learn/server-concepts) — official MCP documentation (server primitives confirmed here)
- [Architecture overview](https://modelcontextprotocol.io/docs/concepts/architecture) — official MCP documentation where the three server primitives were confirmed from the live docs during prep (September 2026)
