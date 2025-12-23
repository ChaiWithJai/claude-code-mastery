# Pre-Livestream Setup

Complete these steps before the livestream starts. Takes ~15 minutes.

---

## Required

### 1. Install Claude Code

```bash
# macOS/Linux
curl -fsSL https://claude.ai/install.sh | sh

# Or via npm
npm install -g @anthropic-ai/claude-code
```

**Verify installation:**
```bash
claude --version
```

### 2. Authenticate

```bash
claude auth
```

This opens a browser window. Sign in with your Anthropic account.

### 3. Clone This Repository

```bash
git clone https://github.com/ChaiWithJai/claude-code-mastery.git
cd claude-code-mastery
```

### 4. Create a Test Project

You'll build skills during the livestream. Have a project ready:

```bash
# Option A: Use an existing project you work on
cd /path/to/your/project

# Option B: Create a fresh test project
mkdir ~/claude-code-test && cd ~/claude-code-test
git init
```

---

## Recommended

### 5. LangSmith Account (Free)

We'll set up tracing during the stream, but you can get ahead:

1. Go to [smith.langchain.com](https://smith.langchain.com)
2. Create a free account
3. Create a project called `claude-code-mastery`
4. Copy your API key (Settings → API Keys)

### 6. Prepare Your Domain

Think about what expertise you want to encode as a skill:

- A code review checklist you use repeatedly?
- A deployment process you follow?
- A framework you apply to decisions?
- A documentation template you use?

**Write down 3-5 bullet points about this process.** You'll encode it as a skill during Segment 7.

### 7. IDE Setup

Have your code editor open alongside the terminal:
- VS Code, Cursor, or your preferred editor
- Terminal visible for Claude Code commands
- Browser tab for LangSmith (after setup)

---

## Troubleshooting

### "command not found: claude"

```bash
# Check if installed
which claude

# If using npm install, ensure global bin is in PATH
export PATH="$PATH:$(npm config get prefix)/bin"
```

### Authentication fails

```bash
# Clear existing auth and retry
claude auth logout
claude auth
```

### Permission denied

```bash
# macOS may require security approval
# Go to System Preferences → Security & Privacy → Allow
```

---

## During the Livestream

### Pause Points

There are 5 pause points where you build alongside me:

| # | Time | Task | Duration |
|---|------|------|----------|
| 1 | ~15 min | Create CLAUDE.md skeleton | 3 min |
| 2 | ~55 min | Create skill skeleton | 5 min |
| 3 | ~90 min | Add command to skill | 5 min |
| 4 | ~130 min | Identify guardrails | 3 min |
| 5 | ~155 min | Build domain expertise skill | 5 min |

### If You Fall Behind

- Each segment is independent—you can catch up at the break
- Reference implementations are in `examples/`
- Exercise solutions are in each exercise folder

### Questions

- Post in chat during the stream
- Common questions will be addressed
- Complex questions → office hours after

---

## Checklist

Before the stream starts, verify:

- [ ] `claude --version` works
- [ ] `claude auth` completed
- [ ] This repo cloned locally
- [ ] Test project ready (new or existing)
- [ ] LangSmith account created (optional but recommended)
- [ ] Domain expertise identified (3-5 bullet points)
- [ ] Editor + terminal visible

---

**Ready?** See you at the livestream.

**[Back to Course →](README.md)**
