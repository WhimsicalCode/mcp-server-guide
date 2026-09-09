# Whimsical MCP Server Guide

The Whimsical MCP server connects an AI agent to a Whimsical workspace. It can create and edit boards, docs, flowcharts, mind maps, sequence diagrams, wireframes, tables and sticky notes, and read, search and comment on content that already exists. Authentication is OAuth 2.1 with PKCE, so there is no API key to manage, and a free Whimsical account can use every tool.

For full documentation, see the [Whimsical MCP docs](https://whimsical.com/learn/integrations/mcp).
For a tool-by-tool reference, see the [MCP tool spec](https://whimsical.com/learn/ai/mcp-tools).

## Features

- **Create boards and diagrams.** Generate flowcharts, mind maps, sequence diagrams, and wireframes from your AI agent.
- **Edit existing content.** Modify boards, add or remove shapes, update text, and rearrange layouts.
- **Search your workspace.** Find files by name or content.
- **Read board content.** Extract structured data from existing boards for context.
- **Create and edit docs.** Write and update Whimsical docs.

## Installation & Setup

### Cursor

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=whimsical&config=eyJ1cmwiOiJodHRwczovL21jcC53aGltc2ljYWwuY29tL21jcCJ9)

Or add it by hand: open **Cursor → Settings → Cursor Settings → MCP**, click
**+ Add new global MCP server**, and save this configuration:

```json
{
  "mcpServers": {
    "whimsical": {
      "url": "https://mcp.whimsical.com/mcp"
    }
  }
}
```

For more information, see [Cursor's official documentation](https://cursor.com/docs/mcp).

### Claude Code

Run the following command to add the Whimsical MCP server:

```bash
claude mcp add --transport http whimsical https://mcp.whimsical.com/mcp
```

### Claude.ai

Connect directly from the [Anthropic Connectors Directory](https://claude.ai/connectors).

### ChatGPT (VS Code / Copilot)

1. Use the shortcut `⌘ Shift P` to search for `MCP: Add Server`.
2. Select `HTTP`.
3. Paste the server URL `https://mcp.whimsical.com/mcp` in the search bar. Then hit `Enter`.
4. When you're prompted for a server ID, enter `whimsical`.
5. Select whether you want to add this server globally or only for the current workspace.

### Other editors

Any code editor or tool that supports Streamable HTTP can connect to the Whimsical MCP server using this configuration:

```json
{
  "mcpServers": {
    "whimsical": {
      "url": "https://mcp.whimsical.com/mcp"
    }
  }
}
```

## Authentication

The Whimsical MCP server uses OAuth 2.0. When you first connect, you'll be redirected to sign in with your Whimsical account and authorize access to your workspace.

## Troubleshooting

- **OAuth doesn't open or fails.** Run `/mcp` in Claude Code (or the equivalent reconnect action in your client) to reauthenticate. The browser will redirect back to your client once you've signed in to Whimsical.
- **Tools don't appear after install.** Run `/reload-plugins` in Claude Code, or restart your editor in other clients.
- **`401` or "Missing Bearer token".** Your OAuth session has expired. Reauthenticate via `/mcp`.
- **No Whimsical account.** Create one at <https://whimsical.com>; the MCP server signs you in to your existing workspace via OAuth.

## Examples

### Create a flowchart from a description

**Prompt:** "Create a flowchart in Whimsical showing a user authentication flow: login page → validate credentials → if valid go to dashboard, if invalid show error and retry"

The agent creates a new board in your workspace with the complete flowchart, including decision nodes, connectors, and labels.

### Generate a mind map for brainstorming

**Prompt:** "Create a mind map in Whimsical to brainstorm features for a mobile app, with branches for onboarding, core features, monetization, and growth"

The agent creates a mind map with the central topic and its branches.

### Create a wireframe for a new feature

**Prompt:** "Create a wireframe in Whimsical for a settings page with a sidebar navigation, a profile section with avatar and form fields, and a danger zone at the bottom"

The agent creates a wireframe with the UI elements laid out to represent the page structure.

### Create a technical architecture diagram

**Prompt:** "Create a technical diagram in Whimsical showing the architecture of my ACME project: a React frontend talks to an API gateway, which routes to auth, billing, and notification microservices, each with their own database"

The agent creates a board with labeled components, service boundaries, and connectors showing the data flow between systems.

### Search and read existing boards

**Prompt:** "Search my Whimsical workspace for anything related to 'API design' and summarize what you find"

The agent searches your workspace, reads the matching boards, and summarizes them.

## Support

- **Overview:** https://whimsical.com/integrations/mcp
- **Documentation:** https://whimsical.com/learn/integrations/mcp
- **Tool reference:** https://whimsical.com/learn/ai/mcp-tools
- **Report Issues:** Contact Whimsical support at support@whimsical.com
- **Privacy Policy:** https://whimsical.com/terms/privacy
