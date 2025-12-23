# Segment 4: MCP Server Integration

**Duration**: 25 minutes
**Builds**: External API connection

---

## Learning Objectives

By the end of this segment, you will:
1. Understand what MCP servers do and why they matter
2. Know how to configure MCP servers
3. See MCP in action with a real integration

---

## 4.1 What is MCP?

### Model Context Protocol

MCP (Model Context Protocol) connects Claude Code to external systems:

```
Claude Code ←→ MCP Server ←→ External API
                  │
                  └── Handles auth, formatting, rate limits
```

**Without MCP:**
- Claude can only work with local files
- No access to calendars, databases, APIs
- Limited to what's in your codebase

**With MCP:**
- Claude can read your calendar
- Claude can query your database
- Claude can call external APIs
- Full integration with your tools

---

## 4.2 Available MCP Servers

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

### Custom
| Server | Package | Purpose |
|--------|---------|---------|
| Stripe | `@stripe/stripe-mcp` | Payment data |
| Supabase | `@supabase/mcp-server` | Supabase integration |
| Custom | Build your own | Your internal APIs |

---

## 4.3 Configuring MCP Servers

### .mcp.json Structure

```json
{
  "mcpServers": {
    "google-calendar": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@cocal/google-calendar-mcp"],
      "env": {
        "GOOGLE_OAUTH_CREDENTIALS": "${HOME}/.config/my-app/oauth.json"
      }
    },
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

### Key Fields

| Field | Purpose |
|-------|---------|
| `type` | Connection type (usually "stdio") |
| `command` | How to run the server |
| `args` | Command arguments |
| `env` | Environment variables |

### Environment Variables

Use `${VAR_NAME}` for:
- API keys
- OAuth credentials
- Config paths

**Never hardcode secrets in .mcp.json**

---

## 4.4 OAuth Setup Pattern

### The Problem

Many APIs require OAuth (Google, Microsoft, etc.):
1. User needs to authorize
2. App gets tokens
3. Tokens need to be stored/refreshed

### The Solution: setup.sh

```bash
#!/bin/bash
# setup.sh

CONFIG_DIR="${HOME}/.config/my-plugin"
mkdir -p "$CONFIG_DIR"

echo "Setting up OAuth for Google Calendar..."

# Run the OAuth flow
GOOGLE_OAUTH_CREDENTIALS="$CONFIG_DIR/oauth.json" \
npx -y @cocal/google-calendar-mcp auth

echo "OAuth setup complete!"
echo "Credentials stored in: $CONFIG_DIR/oauth.json"
```

### Usage

```bash
# First time setup
./setup.sh

# This opens browser, user authorizes, tokens saved
```

---

## 4.5 Live Demo: Calendar MCP

### Show the /briefing command working

```bash
cd ~/projects/fulcrum
claude
> /briefing
```

### Show the trace

```
Trace: /briefing
├── Load briefing command
├── Call MCP: google-calendar
│   ├── list-events
│   │   └── Returns: [{summary: "Team standup", ...}]
│   └── get-freebusy
│       └── Returns: busy/free blocks
├── Call MCP: google-tasks
│   └── list-tasks
│       └── Returns: [{title: "Review PR", ...}]
└── Synthesize briefing
```

### Key Insight

Claude isn't just reading text. It's calling real APIs, getting real data, making real decisions.

---

## 4.6 Adding MCP to Your Plugin

### Step 1: Create .mcp.json

```bash
touch .mcp.json
```

### Step 2: Add server configuration

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

### Step 3: Set environment variable

```bash
export GITHUB_TOKEN="ghp_your_token_here"
```

### Step 4: Test the connection

```bash
claude
> What are my open PRs?
# Claude uses GitHub MCP to fetch and display PRs
```

---

## 4.7 When NOT to Use MCP

### Use MCP When:
- You need real-time data (calendars, PRs, databases)
- You want Claude to take actions (create events, post comments)
- The integration already exists

### Don't Use MCP When:
- Static data (embed in CLAUDE.md instead)
- One-time lookups (just paste the data)
- Custom logic needed (write a script, let Claude call it)

---

## Key Takeaways

1. **MCP connects Claude to external systems**
2. **Configure in .mcp.json** with env vars for secrets
3. **OAuth flows go in setup.sh**
4. **Many servers already exist**—check before building
5. **Use traces to debug** MCP calls

---

**[Next: Break (10 min) →](05-langsmith-telemetry.md)**

---

## Notes for Instructor

### Key Points to Land
1. MCP is what makes Claude Code an agent, not just a chatbot
2. Real APIs, real data, real actions
3. Never hardcode secrets

### Live Demo Notes
- Have Google Calendar OAuth already set up
- Show a real calendar with real events
- Show the trace in LangSmith if possible

### Common Issues
- OAuth fails → Check credentials path
- Server not found → Check npx can run the package
- No data returned → Check API permissions
