# Target MCP Server

## Details

### Target: turn a messy job description into structured, recruiter-ready data

Point an AI agent at a job description. Get back a clean summary, sourcing keywords, and a normalized title in one call.

Hiring inputs are messy: a description copied from a requisition system, a few notes from an intake call with the hiring manager, a title that doesn’t quite fit the role. The Target MCP server cleans that up instantly, so recruiters and hiring workflows can act on a clear, consistent definition of the role.

It's powered by the same talent-intelligence engine behind Skill & Aquent's staffing operations  and is not a generic summarizer.

### What you get back

- **A job target** - a concise, semantic summary of the role's key responsibilities, qualifications, and must-have skills.
- **Sourcing keywords** - the terms a recruiter or sourcing system would search on to find matching candidates.
- **A normalized job title** - inferred from the description when one can be confidently determined.

You can also pass intake-call notes (a summary and/or transcript) alongside the written description, capturing the must-haves and context that rarely make it into a formal posting.

The operation is read-only and non-destructive. Your input is processed for the request and not stored or shared.

### Why it matters

- **Faster intake.** Go from a raw requisition to a structured, searchable role definition in seconds.
- **Better sourcing.** Consistent keywords and qualifications mean cleaner candidate searches and fewer missed matches.
- **Built for agents.** As an MCP server, it drops into any AI workflow without custom API glue.


## Connect

The Target server is served over streamable HTTP at target.mcp.skill.com. Add it to any MCP-compatible client.

### Claude Code

`claude mcp add --transport http skill-target https://target.mcp.skill.com/mcp`

### Claude Desktop / other clients (mcp.json)

```
{
  "mcpServers": {
    "skill-target": {
      "type": "http",
      "url": "https://target.mcp.skill.com/mcp"
    }
  }
}
```

Once connected, ask your assistant to "distill this job description" or "pull the sourcing keywords for this role," and it will call distill_job automatically.


### Claude.ai (web)

Settings → Connectors → Add custom connector → URL `https://target.mcp.skill.com/mcp`.

### ChatGPT (web)

Settings → Apps & Connectors → Create → URL `https://target.mcp.skill.com/mcp`. The app exposes `search` and `fetch` and is therefore eligible for Company Knowledge in ChatGPT Business / Enterprise / Edu.

## Try it

### Natural-language variants

Once connected, ask your assistant to "distill this job description" or "pull the sourcing keywords for this role," and it will call `distill_job` automatically.

## Server Capabilities

### Tools

| Tool | Purpose | Annotations |
|---|---|---|
| `distill_job` | Distills a job description into a clean summary, sourcing keywords, and a normalized title. | Read-only; non-destructive; does not store or transmit your input. |

#### distill_job arguments

Extracts the most important details from a job description.

##### Input

| Field | Required | Description |
|---|---|---|
| `job.description` | Yes | The full job description text. |
| `job.id` | No | An identifier for your own tracking/logging (auto-generated if omitted). |
| `job.intake_call.summary` | No | A summary of an intake call with the hiring manager. |
| `job.intake_call.transcript` | No | The full intake-call transcript. |

##### Output

| Field | Description |
|---|---|
| `target` | A concise synopsis of the role’s responsibilities, qualifications, and key details. |
| `keywords` | A list of sourcing/search keywords for finding candidates. |
| `title` | The inferred job title (best-effort; may be empty). |

##### When to use it

- You have a raw or messy job description and want it cleaned up or summarized.
- You need sourcing keywords to kick off a candidate search.
- You want to normalize or infer a job title from a long description.
- You’re building an automated hiring workflow and need structured job data as an input.

**Tip:** The more context you provide, (full description plus intake notes) the sharper the target and keywords.

### Resources

- 

### Prompts

- 

## Query Support

You can submit distill requests to the MCP server using natural language. The following details can be included in your query, and the MCP server will take them into account when returning a summary.

- Job description
- Job ID
- Intake call notes (summary or transcript)

## Support

**Issues:** https://github.com/aquent/mcp-aquent-skill/issues
**Email:** mcp-support@aquent.com
**Status:** https://status.aquent.com

### FAQs

- **What is an MCP server?** The Model Context Protocol is an open standard that lets AI assistants connect to external tools and data. An MCP server like Target exposes capabilities that any compatible AI client can discover and use.
- **Which AI clients can use it?** Any MCP-compatible client, including Claude (Code, Desktop, and the API), Github Copilot and a growing list of agent frameworks and IDEs.
- **Is my data stored?** No. `distill_job` is a read-only operation that processes your input for the request and does not persist or transmit it elsewhere.
- **Will there be more Skill.com MCP servers?** Yes. Target and Jobs are live today, and we’re expanding the family across the talent lifecycle. Check the hub page for the current lineup.
- **Who builds this?** Skill.com, the staffing and talent platform from Aquent.