<p align="center">
  <img src="assets/consultant-logo.svg" alt="Consultant.dev" width="200">
</p>

# Consultant Assignments

Search live consulting, contractor, and freelance assignments worldwide from
Claude, ChatGPT, and other MCP clients.

The integration connects to the hosted Consultant.dev MCP server:

```text
https://mcp.consultant.dev/mcp
```

A Consultant.dev account is required. There is no anonymous tool access.

## What it does

- Searches live contract, consulting, and freelance assignments across fields
  and countries.
- Fetches the complete details for a specific assignment.
- Creates double-opt-in daily email alerts when you explicitly request one.

Example prompts:

- “Find senior product design contracts in London, including remote roles.”
- “Show me the newest freelance data engineering assignments in Sweden.”
- “Get the full details for this Consultant.dev assignment ID.”
- “Email me a daily alert for interim CFO assignments in Germany.”

## Install for Claude

### Claude community marketplace

After the plugin is accepted into Anthropic's community marketplace:

```text
/plugin marketplace add anthropics/claude-plugins-community
/plugin install consultant-jobs@claude-community
```

The community catalog is reviewed by Anthropic and pins this repository to a
specific commit. Until the listing is live, clone this repository and test the
plugin directly:

```bash
git clone https://github.com/Bytelope/consultant-jobs-plugin.git
claude --plugin-dir ./consultant-jobs-plugin
```

Run `/mcp` and select Consultant Assignments, or make a search request. Claude
opens the Consultant.dev sign-in flow in your browser.

## Install for Codex and ChatGPT

For Codex CLI or the ChatGPT desktop app:

```text
$skill-installer https://github.com/Bytelope/consultant-jobs-plugin
```

You can also copy `skills/consultant-jobs/` into `~/.agents/skills/` or a
project's `.agents/skills/` directory. The MCP dependency is declared in
`skills/consultant-jobs/agents/openai.yaml`.

## Other MCP clients

Clients supporting authenticated Streamable HTTP MCP can connect directly to:

```json
{
  "mcpServers": {
    "consultant-jobs": {
      "type": "streamable-http",
      "url": "https://mcp.consultant.dev/mcp"
    }
  }
}
```

The server publishes OAuth discovery metadata and supports pre-registered
clients, Client ID Metadata Documents, and constrained Dynamic Client
Registration. Every authorization completes through a Consultant.dev account.

## Repository scope

This repository intentionally contains only:

- Claude and MCP manifests
- Agent instructions and example prompts
- Installation, privacy, security, and support documentation
- Safe brand assets

The production MCP server and Consultant.dev application are proprietary and
are not distributed by this repository. The MIT license applies to the public
files here, not to the hosted service implementation.

## Registry

`server.json` contains publishable metadata for the
[Official MCP Registry](https://modelcontextprotocol.io/registry/about). The
registry supports closed-source remote servers when the endpoint is publicly
reachable; users may still be required to authenticate.

## Help and policies

- [Support](SUPPORT.md)
- [Security](SECURITY.md)
- [Privacy](PRIVACY.md)
- [Changelog](CHANGELOG.md)
- [Distribution checklist](SUBMISSION.md)
- [Hosted service documentation](https://consultant.dev/mcp/docs)

## License

MIT
