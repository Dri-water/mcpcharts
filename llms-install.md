# Installing MCP Charts (for AI agents)

MCP Charts is a **hosted remote MCP server**. There is nothing to download,
build or run locally, and no API key or account is needed.

1. Add a remote MCP server entry to the client's MCP settings:

   ```json
   {
     "mcpServers": {
       "mcpcharts": {
         "url": "https://mcpcharts.com/mcp",
         "type": "streamableHttp"
       }
     }
   }
   ```

   If the client doesn't accept `"type": "streamableHttp"`, try `"streamable-http"`,
   or omit `type`. The transport is MCP Streamable HTTP.

2. Leave `env`, `command`, `args` and headers unset. No authentication is used.

3. Verify by listing tools. You should see `recommend_resources`,
   `search_resources` and `get_resource`.

4. Try it: call `recommend_resources` with `{"task": "query a Postgres database"}`.
