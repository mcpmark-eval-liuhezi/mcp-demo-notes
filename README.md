# MCP Demo Notes

Prep notes for the team intro session on the **Model Context Protocol (MCP)**,
delivered **Friday, September 18, 2026**.

## What MCP is for

The **Model Context Protocol (MCP)** is an **open-source standard for connecting
AI applications to external systems**. Using MCP, AI applications like Claude or
ChatGPT can connect to:

- **Data sources** (e.g. local files, databases)
- **Tools** (e.g. search engines, calculators)
- **Workflows** (e.g. specialized prompts)

…enabling them to access key information and perform tasks.

The official documentation describes it as **"a USB-C port for AI
applications"**: just as USB-C provides a standardized way to connect electronic
devices, MCP provides a standardized way to connect AI applications to external
systems.

**Why MCP matters:**

- **Developers** — reduces development time and complexity when building or
  integrating AI applications or agents.
- **AI applications or agents** — gives them access to an ecosystem of data
  sources, tools and apps, enhancing capabilities and improving the end-user
  experience.
- **End-users** — results in more capable AI applications that can access user
  data and take actions on the user's behalf when necessary.

## Server primitives (core building blocks)

An MCP server exposes functionality through **three core primitives**, confirmed
from the live official documentation ("Architecture overview" page):

| Primitive | What it is | Example |
| --- | --- | --- |
| **Tools** | Executable functions that AI applications can invoke to perform actions (e.g. file operations, API calls, database queries) | Querying a database, calling an external API, writing to a file |
| **Resources** | Data sources that provide contextual information to AI applications (e.g. file contents, database records, API responses) | File contents, database records, API responses |
| **Prompts** | Reusable templates that help structure interactions with language models (e.g. system prompts, few-shot examples) | System prompts, few-shot examples for interacting with tools |

Each primitive type has associated methods for **discovery** (`*/list`), **retrieval**
(`*/get`), and in some cases **execution** (`tools/call`). MCP clients use the
`*/list` methods to discover available primitives — for example, a client can
first list all available tools (`tools/list`) and then execute them. This design
allows listings to be dynamic.

**Client-side primitives** (for contrast): MCP also defines primitives that
**clients** can expose — mainly **elicitation** (letting servers ask the user for
input) and **sampling** (servers requesting LLM completions from the host).

Remember: **tools are *model-initiated actions*, resources are *application-
supplied context*, and prompts are *user-requested workflows*.**

## Sources

- [What is the Model Context Protocol (MCP)?](https://modelcontextprotocol.io/introduction) — official MCP documentation (introduction page), pulled live during prep.
- [Architecture overview](https://modelcontextprotocol.io/docs/concepts/architecture) — official MCP documentation (architecture page); the three core server primitives (tools, resources, prompts) were confirmed from this page on the live docs today.
