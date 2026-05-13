# Job Search MCP Server

A secure, standardized bridge connecting Large Language Models (LLMs) and autonomous AI agents directly to Aquent’s live job marketplace and talent data. 

This page provides structured resources to support AI driven job discovery, matching, and hiring workflows. It is intended both for developers building AI powered experiences and for AI agents that need clear, machine readable access to current Aquent opportunities.

`mcp-jobs` exposes Aquent's live job-postings catalog to MCP-compatible AI clients (Claude.ai, ChatGPT, Cursor, VS Code, Zed, Goose, Postman, MCPJam, and any client that speaks Streamable HTTP).

## Details

This MCP server is first-party hosted; not user-installable; production endpoint only.

**Hosted-only, read-only.** This server is operated by Aquent at `https://jobs.mcp.skill.com/mcp`. It is **not** designed for self-hosting: it connects to Aquent's internal PostgreSQL database over the corporate network. Use the production endpoint above; do not run this locally expecting it to work outside Aquent's VPN.

| Detail | Information |
| --- | ----------- |
| URL: | https://jobs.mcp.skill.com/mcp |
| Format: | Model Context Protocol (JSON-RPC 2.0 via SSE) |
| Update frequency: | Real-time (Live database access) |
| Coverage: | All active Aquent job postings |
| Authentication required: | No |
| Rate limit: | 60/minute |
| Access restrictions: | AI agents and enterprise partners can use this server to enable AI assistants (such as Claude, ChatGPT, Manus.ai, Cursor, etc.) to programmatically search, filter, and analyze job listings with authoritative, human-vetted data directly within your agentic environment. |

## Connect

Add a remote MCP connector pointing at `https://jobs.mcp.skill.com/mcp` in your MCP client. The transport is Streamable HTTP. OAuth 2.1 metadata is discoverable at `https://jobs.mcp.skill.com/.well-known/oauth-authorization-server`.

### Claude.ai (web)

Settings → Connectors → Add custom connector → URL `https://jobs.mcp.skill.com/mcp`.

### ChatGPT (web)

Settings → Apps & Connectors → Create → URL `https://jobs.mcp.skill.com/mcp`. The app exposes `search` and `fetch` and is therefore eligible for Company Knowledge in ChatGPT Business / Enterprise / Edu.


## Server Capabilities

### Tools

| Tool | Purpose | Annotations |
|---|---|---|
| `jobs_search_postings` | Search active postings by keyword, market, location, industry, practice | `readOnlyHint:true, destructiveHint:false, idempotentHint:true, openWorldHint:true` |
| `jobs_get_details` | Fetch a single posting by ID | same |
| `jobs_list_markets` | List Aquent markets | same |
| `jobs_list_locations` | List supported locations | same |
| `jobs_list_industries` | List industries served | same |
| `jobs_list_practices` | List practice areas | same |
| `search` | ChatGPT deep-research / company-knowledge compatible search | same |
| `fetch` | ChatGPT deep-research compatible document fetch | same |

### Resources

- jobs://locations
- jobs://markets
- jobs://postings/{id}
- jobs://search-filters

### Prompts

- compare-postings
- job-posting-summary
- job-search-assistant

## Query Support

You can submit searches to the MCP server using natural language. The following details can be included in your query, and the MCP server will take them into account when returning results.

- Location
- Keyword
- ...

## Support
**Issues:** https://github.com/aquent/mcp-jobs/issues
**Email:** mcp-support@aquent.com
**Status:** https://status.aquent.com