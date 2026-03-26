# Whimsical MCP Server Guide

The Whimsical MCP server connects AI agents to your Whimsical workspace, enabling them to create and edit boards, flowcharts, mind maps, wireframes, sequence diagrams, and docs.

For full documentation, see the [Whimsical MCP docs](https://help.whimsical.com/integrations/remote-mcp).

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

## Support

- **Documentation:** https://help.whimsical.com/integrations/remote-mcp
- **Report Issues:** Contact Whimsical support at support@whimsical.com
