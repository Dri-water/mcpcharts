<p align="center"><img src="assets/logo.png" width="96" alt="MCP Charts logo"></p>

# MCP Charts

**The MCP for MCPs.** [MCP Charts](https://mcpcharts.com) is a hosted, read-only
MCP server. Your agent can use it to find the right MCP servers, agent skills,
plugins, agents, prompts and rules for a task.

- **Endpoint:** `https://mcpcharts.com/mcp`
- **Transport:** Streamable HTTP
- **Auth:** none. You don't need an account or API key.
- **Official MCP Registry:** [`com.mcpcharts/mcpcharts`](https://registry.modelcontextprotocol.io/v0/servers?search=com.mcpcharts/mcpcharts)

This repository holds connection docs and registry metadata only. The service
is hosted, so there is nothing to install or run locally.

## Connect

**Claude Code**

```bash
claude mcp add --transport http mcpcharts https://mcpcharts.com/mcp
```

**Cursor, VS Code, Cline, Windsurf and other `mcp.json` clients**

```json
{
  "mcpServers": {
    "mcpcharts": {
      "url": "https://mcpcharts.com/mcp"
    }
  }
}
```

Some clients use `"type": "streamable-http"` or `"transport": "http"` alongside
`url`. Check your client's remote-server docs.

**Claude.ai / ChatGPT:** add `https://mcpcharts.com/mcp` as a custom connector.

## Tools

All tools are read-only. They never install or execute anything.

| Tool | What it does | Inputs |
| --- | --- | --- |
| `recommend_resources` | Gives a ranked shortlist for a task. Keyword relevance comes before repository stars. | `task`, optional `client`, `type`, `limit` (1–8) |
| `search_resources` | Searches keywords across all resource types, up to 24 results per page. | `query`, optional `type`, `page` |
| `get_resource` | Returns compatibility evidence, freshness and the upstream setup link for one catalog entry. | `id` |

`type` is one of `skill`, `mcp`, `plugin`, `agent`, `prompt` or `rule`.

### Example prompts

- "Find me an MCP server for querying Postgres from Claude Code."
- "What skills exist for writing Playwright tests?"
- "Recommend a plugin for reviewing pull requests in Cursor."

## How the catalog works

The catalog is refreshed continuously from public sources, including the
official MCP Registry. Repository stars and activity describe repositories, not
individual resources. Client compatibility comes from manifests and registry
declarations; MCP Charts doesn't run runtime tests. Check requirements such as
"free" or "local-only" upstream before you install anything.

Requests are rate-limited and results are bounded.

## Links

- Website: https://mcpcharts.com
- MCP endpoint: https://mcpcharts.com/mcp
- Issues: [GitHub issues](../../issues)

---

Copyright © 2026 MCP Charts. All rights reserved. This repository contains
documentation only. No license to the MCP Charts service, data or software is
granted.
