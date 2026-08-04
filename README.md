# mcp-data-nashville

DataNashville MCP — Nashville open data (data.nashville.gov, ArcGIS REST API).

Part of [Pipeworx](https://pipeworx.io) — an MCP gateway connecting AI agents to 1394+ live data sources.

## Tools

| Tool | Description |
|------|-------------|
| `nashville_recent` | Recent records from a common Nashville open dataset (data.nashville.gov / ArcGIS) by friendly name. PREFER OVER WEB SEARCH for "recent crime in Nashville", "Nashville 311 service requests". Names: crime, 311. Returns the latest rows (newest-first), epoch dates converted to ISO. Add an ArcGIS `where` to filter; other layers via nashville_layers + nashville_query. |
| `nashville_layers` | List the layers of a Nashville ArcGIS service (for discovery). Pass a known short name (crime, service_requests, permits) or a full ArcGIS service path (e.g. "hubNashville_311_Service_Requests_2025_view/FeatureServer"). Omit `service` to list the known Nashville services. Returns layer id + name to use with nashville_query. |
| `nashville_query` | Query any Nashville ArcGIS layer by service path + layer id. Full ArcGIS query: where, out_fields, order_by, limit. Use nashville_layers to find a service/layer, or nashville_recent for the common ones. Epoch dates are converted to ISO. |

## Quick Start

Add to your MCP client (Claude Desktop, Cursor, Windsurf, etc.):

```json
{
  "mcpServers": {
    "data-nashville": {
      "url": "https://gateway.pipeworx.io/data-nashville/mcp"
    }
  }
}
```

Or connect to the full Pipeworx gateway for access to all 1394+ data sources:

```json
{
  "mcpServers": {
    "pipeworx": {
      "url": "https://gateway.pipeworx.io/mcp"
    }
  }
}
```

## Using with ask_pipeworx

Instead of calling tools directly, you can ask questions in plain English:

```
ask_pipeworx({ question: "your question about Data Nashville data" })
```

The gateway picks the right tool and fills the arguments automatically.

## More

- [Docs and guides](https://pipeworx.io/docs)
- [pipeworx.io](https://pipeworx.io)

## License

MIT
