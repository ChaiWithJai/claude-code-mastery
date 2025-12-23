# MCP Servers Reference

Quick reference for MCP (Model Context Protocol) integration.

---

## What is MCP?

MCP connects Claude Code to external systems:
- Calendars, tasks, databases
- APIs, services, tools
- Custom integrations

---

## .mcp.json Structure

```json
{
  "mcpServers": {
    "server-name": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@package/mcp-server"],
      "env": {
        "API_KEY": "${API_KEY}",
        "CONFIG_PATH": "${HOME}/.config/app/config.json"
      }
    }
  }
}
```

---

## Available Servers

### Productivity

| Server | Package | Purpose |
|--------|---------|---------|
| Google Calendar | `@cocal/google-calendar-mcp` | Calendar read/write |
| Google Tasks | `@overlay-one/google-tasks-mcp-server` | Task management |
| Notion | `@notionhq/notion-mcp` | Notion databases |

### Development

| Server | Package | Purpose |
|--------|---------|---------|
| GitHub | `@anthropic-ai/mcp-github` | Repos, PRs, issues |
| Playwright | `@anthropic-ai/mcp-playwright` | Browser automation |
| Postgres | `@anthropic-ai/mcp-postgres` | Database queries |

### Other

| Server | Package | Purpose |
|--------|---------|---------|
| Stripe | `@stripe/stripe-mcp` | Payment data |
| Supabase | `@supabase/mcp-server` | Supabase integration |

---

## Configuration Examples

### GitHub

```json
{
  "mcpServers": {
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@anthropic-ai/mcp-github"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

Setup:
```bash
export GITHUB_TOKEN="ghp_your_token"
```

### Google Calendar

```json
{
  "mcpServers": {
    "google-calendar": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@cocal/google-calendar-mcp"],
      "env": {
        "GOOGLE_OAUTH_CREDENTIALS": "${HOME}/.config/app/oauth.json"
      }
    }
  }
}
```

Setup:
```bash
GOOGLE_OAUTH_CREDENTIALS="~/.config/app/oauth.json" \
npx -y @cocal/google-calendar-mcp auth
```

### Postgres

```json
{
  "mcpServers": {
    "postgres": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@anthropic-ai/mcp-postgres"],
      "env": {
        "DATABASE_URL": "${DATABASE_URL}"
      }
    }
  }
}
```

---

## Environment Variables

Use `${VAR_NAME}` syntax:

```json
{
  "env": {
    "API_KEY": "${API_KEY}",
    "HOME_PATH": "${HOME}/.config/app",
    "CUSTOM_VAR": "${MY_CUSTOM_VAR}"
  }
}
```

Set in your shell:
```bash
export API_KEY="your_key"
export MY_CUSTOM_VAR="value"
```

---

## OAuth Setup Pattern

### setup.sh Template

```bash
#!/bin/bash

CONFIG_DIR="${HOME}/.config/my-app"
mkdir -p "$CONFIG_DIR"

echo "Setting up OAuth..."

# Run the OAuth flow
GOOGLE_OAUTH_CREDENTIALS="$CONFIG_DIR/oauth.json" \
npx -y @cocal/google-calendar-mcp auth

echo "OAuth complete!"
echo "Credentials: $CONFIG_DIR/oauth.json"
```

---

## Testing MCP

### Verify Connection

```bash
claude
> What MCP servers are available?
```

### Test Server

```bash
> What's on my calendar today?     # Google Calendar
> What are my open PRs?            # GitHub
> Run this SQL: SELECT 1          # Postgres
```

---

## Troubleshooting

| Issue | Cause | Fix |
|-------|-------|-----|
| Server not found | Package not installed | Check npx can run it |
| Auth failed | Tokens expired | Re-run auth flow |
| No data returned | Wrong permissions | Check API scopes |
| Env var not found | Not exported | Check shell config |

### Debug Steps

1. Check .mcp.json syntax (valid JSON?)
2. Check env vars are set (`echo $VAR`)
3. Run server manually (`npx -y @package/server`)
4. Check server-specific auth
