# Whimsical MCP Server Guide

The Whimsical MCP server connects AI agents to your Whimsical workspace, enabling them to create and edit boards, flowcharts, mind maps, wireframes, sequence diagrams, and docs.

For full documentation, see the [Whimsical MCP docs](https://help.whimsical.com/integrations/remote-mcp).

## Features

- **Create boards and diagrams** — Generate flowcharts, mind maps, sequence diagrams, and wireframes directly from your AI agent
- **Edit existing content** — Modify boards, add or remove shapes, update text, and rearrange layouts
- **Search your workspace** — Find files across your Whimsical workspace by name or content
- **Read board content** — Extract structured data from existing boards for context in your coding workflow
- **Create and edit docs** — Write and update Whimsical docs

## Installation & Setup

### Cursor

Install the Whimsical plugin by typing the following command in Cursor's agent chat:

```
/add-plugin whimsical
```

<details>
<summary>Manual setup</summary>

1. Open **Cursor → Settings → Cursor Settings**.
2. Go to the **MCP** tab.
3. Click **+ Add new global MCP server**.
4. Enter the following configuration and save:

```json
{
  "mcpServers": {
    "whimsical": {
      "url": "https://mcp.whimsical.com/mcp"
    }
  }
}
```

For more information, see [Cursor's official documentation](https://docs.cursor.com/context/model-context-protocol).

</details>

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

## Examples

### Create a flowchart from a description

**Prompt:** "Create a flowchart in Whimsical showing a user authentication flow: login page → validate credentials → if valid go to dashboard, if invalid show error and retry"

The agent creates a new board in your workspace with the complete flowchart, including decision nodes, connectors, and labels.

### Generate a mind map for brainstorming

**Prompt:** "Create a mind map in Whimsical to brainstorm features for a mobile app, with branches for onboarding, core features, monetization, and growth"

The agent creates a structured mind map with the central topic and branches, ready for you to expand.

### Create a wireframe for a new feature

**Prompt:** "Create a wireframe in Whimsical for a settings page with a sidebar navigation, a profile section with avatar and form fields, and a danger zone at the bottom"

The agent creates a wireframe with UI elements laid out to represent the page structure, ready for review and iteration.

### Create a technical architecture diagram

**Prompt:** "Create a technical diagram in Whimsical showing the architecture of my ACME project: a React frontend talks to an API gateway, which routes to auth, billing, and notification microservices, each with their own database"

The agent creates a board with labeled components, service boundaries, and connectors showing the data flow between systems.

### Search and read existing boards

**Prompt:** "Search my Whimsical workspace for anything related to 'API design' and summarize what you find"

The agent searches your workspace, reads the matching boards, and provides a summary of the content and structure.

## Support

- **Documentation:** https://help.whimsical.com/integrations/remote-mcp
- **Report Issues:** Contact Whimsical support at support@whimsical.com
- **Privacy Policy:** https://whimsical.com/terms/privacy
