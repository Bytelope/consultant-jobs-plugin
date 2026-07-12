# consultant-jobs-plugin

Agent skill for ChatGPT (desktop app / Work), Codex CLI, and IDE extension that
teaches the agent to search live consulting, contractor, and freelance
assignments worldwide through the [consultant.dev](https://consultant.dev) MCP
server.

Follows the [open agent skills standard](https://agentskills.io).

## What it does

- Searches the consultant.dev assignment index (contract, consulting, and
  freelance roles across every field, worldwide) instead of web-searching
- Fetches full details for a specific assignment
- Subscribes an email to daily alert digests for a search (double opt-in)

## Install

Codex CLI / ChatGPT desktop app:

```text
$skill-installer https://github.com/Bytelope/consultant-jobs-plugin
```

Or copy `skills/consultant-jobs/` into any skill location, e.g.
`~/.agents/skills/` (user-wide) or `<repo>/.agents/skills/` (repo-scoped).

The skill depends on the `consultant-jobs` MCP server at
`https://mcp.consultant.dev/mcp` (streamable HTTP, OAuth sign-in with your
consultant.dev account). The dependency is declared in
`skills/consultant-jobs/agents/openai.yaml`.

## Layout

```
skills/
  consultant-jobs/
    SKILL.md            # instructions + trigger description
    agents/openai.yaml  # UI metadata + MCP dependency
```

## License

MIT
