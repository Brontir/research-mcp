# BRONTIR Research

[![BRONTIR MCP connector](https://glama.ai/mcp/connectors/com.brontir.research/brontir/badges/score.svg)](https://glama.ai/mcp/connectors/com.brontir.research/brontir)

Remote MCP server for web research. It gives Claude, Codex, Cursor, VS Code and other MCP clients access to search, Reddit, YouTube, local businesses, reviews, ad libraries and more, with citations precise to the line.

The server is hosted: there is nothing to install or run locally. This repository holds setup documentation only.

## Endpoint

```
https://research.brontir.com/api/mcp
```

Streamable HTTP. Most clients sign in with OAuth using a Google account. Clients without OAuth support use an API key created in your account, sent as `Authorization: Bearer <key>`.

Accounts are free to create, no card required, with free credits to start: [brontir.com/signup](https://brontir.com/signup).

**Restart your client after connecting.** Clients read the tool list at startup, so a freshly added server often stays invisible until a restart.

## Connect your client

### Claude (Web and Desktop)

1. Open **Customize → Connectors** and press **Add**.
2. Name: `research`. MCP server URL: the endpoint above. Press **Continue**.
3. Leave the detected settings as they are (**Sign in now**, **Register automatically**) and press **Add**.
4. Press **Connect** on the new row, then **Approve** on the BRONTIR authorization page.
5. Restart the desktop app, or reload the page in Claude Web.

### Claude Code

```
claude mcp add --transport http --scope user research https://research.brontir.com/api/mcp
```

Then run `/mcp`, select `research` and finish the sign-in in your browser. A connector already added to your Claude account appears in Claude Code automatically.

### Codex (CLI, desktop app, IDE extension)

```
codex mcp add research --url https://research.brontir.com/api/mcp
```

The sign-in opens in your browser. If it does not, run `codex mcp login research`. The CLI, the desktop app in Codex mode and the IDE extension share one configuration.

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "research": { "url": "https://research.brontir.com/api/mcp" } } }
```

Then open **Customize → MCPs** and press **Authenticate** on the server row.

### VS Code

Add to `.vscode/mcp.json`, or run **MCP: Open User Configuration**:

```json
{ "servers": { "research": { "type": "http", "url": "https://research.brontir.com/api/mcp" } } }
```

Confirm **Allow** and **Open**, then **Approve** on the BRONTIR authorization page.

### Other clients

Step-by-step setup for Cline, Grok, Antigravity, Kiro and any other streamable HTTP client, plus troubleshooting: [brontir.com/docs](https://brontir.com/docs).

## Tools

| Tool | What it does |
| --- | --- |
| `advanced_web_search` | Finds sources across web search, news, Scholar, patents, jobs, maps, YouTube, Reddit, TikTok, Threads, stores, hotels, flights, review sites, app stores and ad libraries. One query can run across several sources at once. |
| `advanced_web_fetch` | Pulls clean content from any public URL, many at a time, with platform-aware extraction for video, social, places, reviews, app stores, products, homes, hotels, market data, patents, researcher profiles, ads, PDFs and images. |
| `seo_metrics` | Keyword demand, rankings and competitors, backlinks, domain profiles and search interest over time. |
| `ask_collected_records` | Answers a question over collected records, with line-level citations. |
| `read_collected_records` | Reads a collected record, or only the line range you need. |
| `grep_collected_records` | Keyword and regex search across everything collected. |
| `get_task_results` | Streams results from longer research tasks as they arrive. |

## Why use it

- **Citations to the line.** Every answer can point to the exact place in the source it came from.
- **A corpus, not snippets.** Everything collected is stored as records you can reopen, search and cite later.
- **Context stays small.** The agent reads only the lines it needs instead of loading whole pages.
- **Depth.** Up to a thousand business listings in one answer, full comment trees, full video transcripts.
- **Few tools, many sources.** Seven tools cover dozens of sources, so the agent is not weighed down by a long tool list.

## Links

- Documentation: [brontir.com/docs](https://brontir.com/docs)
- Website: [brontir.com](https://brontir.com)
- Official MCP Registry: `com.brontir/research`
- Support: support@brontir.com

## License

The documentation in this repository is released under the MIT License. Use of the BRONTIR service is subject to its own terms, published at [brontir.com](https://brontir.com).
