# Job Search MCP Server

A secure, standardized bridge connecting Large Language Models (LLMs) and autonomous AI agents directly to Aquent’s live job marketplace and talent data. 

This page provides structured resources to support AI driven job discovery, matching, and hiring workflows. It is intended both for developers building AI powered experiences and for AI agents that need clear, machine readable access to current Aquent opportunities.

| Detail | Information |
| --- | ----------- |
| URL: | https://jobs.mcp.skill.com/mcp |
| Format: | Model Context Protocol (JSON-RPC 2.0 via SSE) |
| Update frequency: | Real-time (Live database access) |
| Coverage: | All active Aquent job postings |
| Authentication required: | No |
| Access restrictions: | AI agents and enterprise partners can use this server to enable AI assistants (such as Claude, ChatGPT, Manus.ai, Cursor, etc.) to programmatically search, filter, and analyze job listings with authoritative, human-vetted data directly within your agentic environment. |

## Server Tools

- ...

## Query Support

You can submit searches to the MCP server using natural language. The following details can be included in your query, and the MCP server will take them into account when returning results.

- Location
- Keyword
- ...