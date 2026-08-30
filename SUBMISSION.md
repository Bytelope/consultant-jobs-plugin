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

### Reviewer verification path

Reviewers can create a fresh Consultant.dev account during OAuth. No invite,
subscription, payment card, or allowlist entry is required:

1. Install the wrapper and start a Consultant Assignments search.
2. Create or sign in to the Consultant.dev account in the browser window.
3. Run `search_assignments`.
4. Pass one returned assignment ID to `get_assignment`.
5. Disconnect the server, reconnect, and verify OAuth is requested again.

Never publish a shared reviewer password. If Anthropic explicitly requests a
dedicated credential, deliver it only through Anthropic's private reviewer
channel. Reviewer policy and support links are [Privacy](PRIVACY.md),
[Support](SUPPORT.md), [Security](SECURITY.md),
[Consultant.dev privacy](https://consultant.dev/privacy), and
[Consultant.dev terms](https://consultant.dev/terms).

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

## Gemini CLI Extension Gallery

1. Keep `gemini-extension.json` in the repository root.
2. Keep the repository public and add the `gemini-cli-extension` GitHub topic.
3. Ensure the manifest version matches the release tag.
4. Create a non-prerelease GitHub release. Gemini's crawler scans tagged
   repositories daily and lists valid extensions automatically; there is no
   submission form.
5. Verify the listing in the
   [Gemini CLI Extension Gallery](https://geminicli.com/extensions/browse/).

## Release and attribution

- Keep the plugin manifest and `server.json` versions aligned.
- Bump both versions before every immutable registry publication.
- The Claude manifest homepage and Registry website URL use separate UTM
  sources. Preserve them so directory visits and account conversions can be
  compared by channel.
- Never put tracking parameters on the MCP endpoint itself. Its canonical OAuth
  resource identifier must remain exactly
  `https://mcp.consultant.dev/mcp`.
