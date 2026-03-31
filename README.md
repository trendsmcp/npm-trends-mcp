# npm-trends-mcp

[![npm Trends](https://img.shields.io/badge/npm%20Trends-CB3837?style=flat-square)](https://trendsmcp.ai/npm-trends)
[![MCP](https://img.shields.io/badge/MCP-compatible-blue?style=flat-square)](https://modelcontextprotocol.io)
[![Works with Claude](https://img.shields.io/badge/Claude-supported-orange?style=flat-square)](https://trendsmcp.ai/mcp-server-for-claude)
[![Works with Cursor](https://img.shields.io/badge/Cursor-supported-purple?style=flat-square)](https://trendsmcp.ai/mcp-server-for-cursor)

> **npm package trend data for AI assistants**
> Track weekly download counts for any npm package. Package download trends reveal which JavaScript libraries and frameworks developers are adopting, which are losing ground, and where the ecosystem is heading.

**Full docs and live demo:** [https://trendsmcp.ai/npm-trends](https://trendsmcp.ai/npm-trends)

Part of **[Trends MCP](https://trendsmcp.ai)** - the MCP server for live trend data across 12+ sources.
See the main repo: [https://github.com/trendsmcp/trends-mcp](https://github.com/trendsmcp/trends-mcp)

---

## Get started in 2 steps

**Step 1:** Get your free API key at **[trendsmcp.ai](https://trendsmcp.ai)**
100 requests/day, no credit card required.

**Step 2:** Add to your AI client (replace `YOUR_API_KEY`):

[**+ Add to Cursor (one click)**](cursor://anysphere.cursor-deeplink/mcp/install?name=trends-mcp&config=eyJ1cmwiOiAiaHR0cHM6Ly9hcGkudHJlbmRzbWNwLmFpL21jcCIsICJ0cmFuc3BvcnQiOiAiaHR0cCJ9)

**Cursor / Windsurf / Cline** &nbsp; (`~/.cursor/mcp.json` or equivalent)
```json
{
  "mcpServers": {
    "trends-mcp": {
      "url": "https://api.trendsmcp.ai/mcp",
      "transport": "http",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**VS Code / GitHub Copilot** &nbsp; (`.vscode/mcp.json`)
```json
{
  "servers": {
    "trends-mcp": {
      "type": "http",
      "url": "https://api.trendsmcp.ai/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude Desktop** &nbsp; (`claude_desktop_config.json`)
```json
{
  "mcpServers": {
    "trends-mcp": {
      "url": "https://api.trendsmcp.ai/mcp",
      "transport": "http",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude.ai** (browser) &nbsp; Settings -> Connectors -> Add custom connector:
```
https://api.trendsmcp.ai/mcp
```

---

## Example query

After connecting, ask your AI:
```
get_trends(keyword='react', source='npm', data_mode='weekly')
```

---

## Available tools

| Tool | What it does |
|------|-------------|
| `get_trends` | Time-series for a keyword on this source |
| `get_growth` | Growth % over 1W, 1M, 3M, 6M, 1Y periods |
| `get_top_trends` | What is trending right now on this source |
| `get_ranked_trends` | Top topics ranked by volume |

---

## FAQ

### What npm data does Trends MCP return?

Weekly download counts for any npm package, normalized to a 0-100 scale, plus raw download volume, growth rates over standard periods (7D, 1M, 3M, 1Y), and a historical time series going back up to 5 years.

### How do I query a specific package?

Use the exact npm package name - for example 'react', 'lodash', 'express', or '@anthropic-ai/sdk'. Scoped packages use the @org/package format.

### Can I compare multiple packages?

Yes. Use get_growth with comma-separated package names or call get_trends for each package and compare the normalized series. Useful for framework comparisons like React vs Vue vs Svelte.

### Why is npm data useful for investment research?

npm download trends are a leading indicator of developer ecosystem adoption. A library growing fast in downloads often precedes broader commercial adoption of the underlying platform or framework.

### How is npm download data normalized?

Raw weekly download counts are normalized to a 0-100 scale relative to the package's own historical peak. This makes it possible to compare adoption velocity across packages with very different absolute download volumes.

---

## All data sources

Trends MCP covers 12+ sources in one connection:
Google Search, YouTube, TikTok, Reddit, Amazon, Wikipedia,
News Sentiment, Web Traffic, App Downloads, Steam, npm, and more.

Browse all: [https://trendsmcp.ai/data-sources](https://trendsmcp.ai/data-sources)


---

## Also works as a Python client

Same API key works directly in Python - no MCP host needed.

```bash
pip install npm-trends-mcp
```

```python
import os
from npm_trends_mcp import TrendsMcpClient, SOURCE

client = TrendsMcpClient(api_key=os.environ["TRENDSMCP_API_KEY"])

series  = client.get_trends(source=SOURCE, keyword="your keyword")
growth  = client.get_growth(source=SOURCE, keyword="your keyword", percent_growth=["1M", "3M", "12M"])
top     = client.get_top_trends(type="Npm", limit=10)
```

Full Python docs: [trendsmcp.ai/docs](https://trendsmcp.ai/docs)
---

## License

MIT &copy; [Trends MCP](https://trendsmcp.ai)