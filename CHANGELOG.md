# Changelog

All notable changes to **mcp-jobs** are documented here.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.0.1] - 2026-05-08
### Added
- Initial public release of the Aquent Jobs MCP server.
- Streamable HTTP transport at `/mcp` (port 8085) following MCP spec 2025-11-25.
- Six MCP tools: `jobs_search_postings`, `jobs_get_details`, `jobs_list_markets`,
  `jobs_list_locations`, `jobs_list_industries`, `jobs_list_practices`.
- Two ChatGPT-compatible tools: `search` and `fetch`.
- Four MCP resources: `jobs://markets`, `jobs://locations`,
  `jobs://postings/{id}`, `jobs://search-filters`.
- Three MCP prompts: `job-search-assistant`, `job-posting-summary`,
  `compare-postings`.
- Two completion providers: market and location prefix auto-complete.
- Per-IP rate limiting (60 req/min).
- Caffeine cache with admin refresh endpoint at `/admin/refresh-cache`
  (key-protected, separate port 8086).
- Structured JSON logs with MDC, Spring Retry on PostgreSQL, JaCoCo/Checkstyle/
  SpotBugs/PMD enforced in CI.

[Unreleased]: https://github.com/aquent/mcp-jobs/compare/v0.0.1...HEAD
[0.0.1]: https://github.com/aquent/mcp-jobs/releases/tag/v0.0.1
