# Support

## Sign in

Install and enable the plugin, then ask Claude to search for a consulting
assignment. Claude opens the Consultant.dev OAuth flow in your browser. Sign in
or create an account, approve access, and return to Claude.

In Claude Code, you can also open `/mcp`, select the Consultant Jobs server,
and start authentication there.

## Disconnect

Open `/mcp`, select the Consultant Jobs server, and clear its stored
authentication. From the command line, use `claude mcp list` to find the
server's displayed name and `claude mcp logout <name>` to clear its credentials.

Disabling or uninstalling the plugin removes its MCP configuration from future
sessions. To delete your Consultant.dev account or data, use the account
settings on [Consultant.dev](https://consultant.dev).

## Get help

For installation or plugin issues, open a
[GitHub issue](https://github.com/Bytelope/consultant-jobs-plugin/issues).
For account or service issues, use
[Consultant.dev contact](https://consultant.dev/contact).

Security reports must follow [SECURITY.md](SECURITY.md).
