# Distribution checklist

This repository is the public distribution wrapper for the proprietary hosted
Consultant.dev MCP server. Do not add server implementation, secrets, user
data, private logs, or private deployment configuration here.

## Claude community marketplace

1. Ensure the remote OAuth flow is live and requires a Consultant.dev account.
2. Run:

   ```bash
   claude plugin validate . --strict
   ```

3. Test with `claude --plugin-dir .`, including sign-in, search, logout, and
   reconnect.
4. Submit the public repository through one of Anthropic's forms:

   - [claude.ai submission](https://claude.ai/admin-settings/directory/submissions/plugins/new)
   - [Claude Platform submission](https://platform.claude.com/plugins/submit)

5. Confirm the approved commit appears in the
   [community catalog](https://github.com/anthropics/claude-plugins-community/blob/main/.claude-plugin/marketplace.json).
6. Install from the catalog in a clean Claude profile and repeat the account
   flow.

The forms submit to `claude-community`, not Anthropic's separately curated
official marketplace. Anthropic does not publish an application process for
the official marketplace.

## Official MCP Registry

1. Validate `server.json` against the current
   [registry schema](https://github.com/modelcontextprotocol/registry/blob/main/docs/reference/server-json/draft/server.schema.json).
2. Confirm `https://mcp.consultant.dev/mcp` is publicly reachable and returns
   OAuth protected-resource discovery for unauthenticated requests.
3. Authenticate the `dev.consultant` namespace using Consultant.dev domain
   ownership. Follow the registry's
   [authentication guide](https://modelcontextprotocol.io/registry/authentication).
4. Ensure the repository Actions secret `MCP_PRIVATE_KEY` contains the raw
   Ed25519 private key matching the proof served from
   `https://consultant.dev/.well-known/mcp-registry-auth`.
5. Run the manual `Publish to MCP Registry` GitHub Actions workflow. The
   workflow downloads a pinned `mcp-publisher` release, verifies its checksum,
   authenticates the `consultant.dev` namespace, publishes `server.json`, and
   verifies the resulting registry entry.
6. Verify:

   ```text
   https://registry.modelcontextprotocol.io/v0.1/servers?search=dev.consultant/assignments
   ```

## Release and attribution

- Keep the plugin manifest and `server.json` versions aligned.
- Bump both versions before every immutable registry publication.
- The Claude manifest homepage and Registry website URL use separate UTM
  sources. Preserve them so directory visits and account conversions can be
  compared by channel.
- Never put tracking parameters on the MCP endpoint itself. Its canonical OAuth
  resource identifier must remain exactly
  `https://mcp.consultant.dev/mcp`.
