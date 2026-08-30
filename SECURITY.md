# Security

The plugin connects Claude to the hosted Consultant.dev MCP service at
`https://mcp.consultant.dev/mcp`.

- A Consultant.dev account is mandatory. Tool access is not available
  anonymously.
- Authentication uses OAuth and Consultant.dev's Clerk sign-in. The plugin
  contains no API keys, client secrets, or user credentials.
- OAuth clients use authorization code flow with S256 PKCE. Redirects must be
  explicit HTTPS URLs or local loopback URLs.
- The hosted MCP server and Consultant.dev application are proprietary. This
  public repository contains only integration metadata, instructions, and
  brand assets.

Do not report vulnerabilities in a public GitHub issue. Send a private report
through [Consultant.dev contact](https://consultant.dev/contact) and mark it as
a security report. Include the affected URL, impact, and reproduction steps.
