# Gemini CLI

Gemini CLI supports authenticated remote MCP servers over Streamable HTTP and
can discover Consultant.dev OAuth automatically.

## Install

Install Consultant Assignments as a Gemini CLI extension:

```bash
gemini extensions install https://github.com/Bytelope/consultant-jobs-plugin
```

Restart Gemini CLI after installation. It will connect to the hosted MCP server
and open Consultant.dev sign-in when authentication is required.

Alternatively, add Consultant Assignments directly to your user-level Gemini
CLI configuration:

```bash
gemini mcp add --transport http --scope user \
  consultant-assignments https://mcp.consultant.dev/mcp
```

Start Gemini CLI, then inspect or authenticate the connection:

```text
/mcp
/mcp auth consultant-assignments
```

Gemini opens the Consultant.dev sign-in flow in your browser. A Consultant.dev
account is required; the server does not allow anonymous tool calls.

You can also configure the server directly in `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "consultant-assignments": {
      "httpUrl": "https://mcp.consultant.dev/mcp"
    }
  }
}
```

Do not add an authorization header or copy OAuth tokens into the configuration.
Gemini CLI handles discovery, browser authorization, token storage, and refresh.

## Verify

After signing in, try:

```text
Search Consultant for product design assignments in Sweden. Then open the full
details for the first result.
```

This should call `search_assignments`, followed by `get_assignment` with the
returned assignment ID.

## Disconnect

If you installed the extension, remove it with:

```bash
gemini extensions uninstall consultant-assignments
```

Use `/mcp auth consultant-assignments` to re-authenticate when needed, or remove
the server completely:

```bash
gemini mcp remove --scope user consultant-assignments
```

Removing the local configuration does not delete the Consultant.dev account.
Account deletion remains available through Consultant.dev account settings.

Official client reference:
[Gemini CLI MCP servers](https://github.com/google-gemini/gemini-cli/blob/main/docs/tools/mcp-server.md).
