# MCP Demo Notes

Prep notes for a team intro session on the **Model Context Protocol (MCP)**, delivered **Friday, September 18, 2026**.

## What MCP is for

The Model Context Protocol (MCP) is an **open-source standard for connecting AI applications to external systems**. Using MCP, AI applications like Claude or ChatGPT can connect to:

- **Data sources** (e.g. local files, databases)
- **Tools** (e.g. search engines, calculators)
- **Workflows** (e.g. specialized prompts)

…enabling them to access key information and perform tasks. The official docs describe it as "a **USB-C port for AI applications**": just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems.

**Why MCP matters：**

- **Developers** — MCP reduces development time and complexity when building, or integrating with, an AI application or agent.
- **AI applications or agents** — MCP gives them access to an ecosystem of data sources, tools and apps, which enhances their capabilities and improves the end-user experience.
- **End-users** — MCP results in more capable AI applications or agents that can access user data and take actions on the user's behalf when necessary.

MCP is an open protocol supported across a wide range of clients and servers — AI assistants like Claude and ChatGPT, and tools like Visual Studio Code, Cursor, and MCPJam all support MCP, so you can build once and integrate everywhere.

## Server primitives

An MCP server exposes functionality through **three core building blocks (primitives)**, confirmed from the official documentation ("Architecture overview"):

| Primitive | What it is | Who controls it | Examples |
| --- | --- | --- | --- |
| **Tools** | Executable functions that AI applications can invoke to perform actions (e.g. file operations, API calls, database queries) | **Model** | Querying a database, running a search, executing file operations |
| **Resources** | Data sources that provide contextual information to AI applications (e.g. file contents, database records, API responses) | **Application** | File contents, database records, API responses |
| **Prompts** | Reusable templates that help structure interactions with language models (e.g. system prompts, few-shot examples) | **User** | System prompts, few-shot examples for interacting with tools |

A useful way to remember it: **tools are *model-initiated actions*, resources are *application-supplied context*, and prompts are *user-requested workflows*.** Each primitive type has associated methods for discovery (`*/list`), retrieval (`*/get`), and in some cases, execution (`tools/call`).

## Sources

- [What is the Model Context Protocol (MCP)?](https://modelcontextprotocol.io/docs/getting-started/intro) — official MCP documentation (primary source for what MCP is for and the USB-C analogy)
- [Architecture overview](https://modelcontextprotocol.io/docs/concepts/architecture) — official MCP documentation (source for the three server primitives: tools, resources, prompts)
