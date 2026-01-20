# MCP Setup

Model Context Protocol (MCP) lets MCP-enabled clients connect to external tools and data sources. Pigeon MCP exposes Pigeon tools and automation management over a remote MCP server.

Remote MCP server URL:
`https://backend.pigeon.trade/mcp`

!> **Note**: You must use a client or editor that supports MCP servers (VS Code, Cursor, Claude Code, etc.).

## What you can do

- List Pigeon tools by category and fetch tool schemas.
- Create, edit, and run automations.
- Fetch automation code and execution history.

## Authentication

Pigeon MCP uses OAuth. The first time you connect, your client will open a browser to sign in and grant access.
If your client asks for OAuth scopes, use `mcp:tools`.

### How OAuth works (high level)

1. Your client contacts the MCP server and receives a 401 challenge.
2. The client discovers OAuth endpoints via `/.well-known/oauth-authorization-server`.
3. The client registers (dynamic client registration) or uses its own client ID.
4. Your browser opens to approve access.
5. The client stores the access token and uses it on MCP requests.

### Auth steps by client

#### Cursor

- Add the server in MCP settings.
- Click Connect next to `pigeon`.
- Browser opens: sign in and click Allow Access.
- Cursor shows "Connected" once tokens are stored.

#### VS Code

- After adding the server, click Start above `pigeon`.
- Browser opens: sign in and click Allow Access.
- VS Code confirms the server is connected.

#### Claude Code

- Add the server with `claude mcp add ...`.
- In Claude Code, run `/mcp`, select `pigeon`, then Authenticate.
- Approve access in the browser, then return to Claude Code.

#### OpenCode

- After configuring, run `opencode mcp auth pigeon`.
- Complete the browser login and return to the terminal.

#### GitHub Coding Agent

- Save the MCP config in repo settings.
- The agent will prompt for OAuth on first use.

### Scopes

If your client requests scopes, use `mcp:tools`. This is required for tool access.

### Troubleshooting auth

- If you see repeated 401 errors, re-run authentication and retry the tool call.
- If the browser window does not open, copy the URL shown in your client and open it manually.
- If your client supports OAuth logout, remove stored credentials and authenticate again.

## Install in common clients

### Claude Code

```bash
claude mcp add -t http -s user pigeon https://backend.pigeon.trade/mcp
```

Use `user`, `project`, or `local` for the `-s` scope.

### Claude Desktop

- Open Settings > Connectors
- Click Add Custom Connector
- Name: `pigeon`
- Remote MCP server URL: `https://backend.pigeon.trade/mcp`
- Click Add, then authenticate when prompted

### Codex CLI

Add to `~/.codex/config.toml`:

```toml
experimental_use_rmcp_client = true
[mcp_servers.pigeon]
url = "https://backend.pigeon.trade/mcp"
```

### Gemini CLI

```bash
gemini mcp add -t http -s user pigeon https://backend.pigeon.trade/mcp
```

The `-s` scope must be `user` or `project`.

### OpenCode

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "pigeon": {
      "type": "remote",
      "url": "https://backend.pigeon.trade/mcp",
      "enabled": true
    }
  }
}
```

OpenCode will prompt you to authenticate on first use.

### VS Code

- Open the command palette
- Select "MCP: Add Server..."
- Select "HTTP (HTTP or Server-Sent-Events)"
- URL: `https://backend.pigeon.trade/mcp`
- Name: `pigeon`
- Choose Global or Workspace

### Cursor

Add to `.cursor/mcp.json` (project) or `~/.cursor/mcp.json` (global):

```json
{
  "mcpServers": {
    "pigeon": {
      "url": "https://backend.pigeon.trade/mcp",
      "type": "http"
    }
  }
}
```

Authenticate when prompted.

### GitHub Coding Agent

In repo Settings > Copilot > Coding agent, add:

```json
{
  "mcpServers": {
    "pigeon": {
      "type": "http",
      "url": "https://backend.pigeon.trade/mcp",
      "tools": ["*"]
    }
  }
}
```

### Other clients

Use the remote MCP URL and authenticate via OAuth when prompted:
`https://backend.pigeon.trade/mcp`

## Cursor install link (one-click)

Config JSON:

```json
{
  "type": "http",
  "url": "https://backend.pigeon.trade/mcp"
}
```

Install link:

```text
cursor://anysphere.cursor-deeplink/mcp/install?name=pigeon&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vYmFja2VuZC5waWdlb24udHJhZGUvbWNwIn0=
```

## After connecting

- Call `pigeon_whoami` to verify authentication.
- Use `pigeon_automation_tools_list` to see categories.
- Use `pigeon_automation_tools_category` and `pigeon_automation_tool_schema` to keep context small.
