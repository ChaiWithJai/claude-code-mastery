# LangSmith Setup Reference

Quick reference for LangSmith tracing with Claude Code.

---

## Why LangSmith?

Without traces, you're debugging blind:
- What skill was triggered?
- What principles were applied?
- Why did it choose that path?
- Where did it fail?

---

## Setup Steps

### 1. Create Account

1. Go to [smith.langchain.com](https://smith.langchain.com)
2. Sign up (free tier available)
3. Create a project

### 2. Get API Key

1. Settings → API Keys
2. Create new key
3. Copy it (shown once)

### 3. Configure Environment

**Option A: Shell config (~/.zshrc or ~/.bashrc)**

```bash
export LANGSMITH_TRACING=true
export LANGSMITH_API_KEY="lsv2_pt_your_key_here"
export LANGSMITH_PROJECT="claude-code-mastery"
```

**Option B: Claude Code settings**

```json
// ~/.claude/settings.json
{
  "env": {
    "LANGSMITH_TRACING": "true",
    "LANGSMITH_API_KEY": "lsv2_pt_your_key_here",
    "LANGSMITH_PROJECT": "claude-code-mastery"
  }
}
```

### 4. Verify

```bash
source ~/.zshrc  # or restart terminal
claude
> Hello
```

Check LangSmith for the trace.

---

## Environment Variables

| Variable | Purpose | Example |
|----------|---------|---------|
| `LANGSMITH_TRACING` | Enable tracing | `true` |
| `LANGSMITH_API_KEY` | Authentication | `lsv2_pt_...` |
| `LANGSMITH_PROJECT` | Project name | `my-project` |
| `LANGSMITH_DEBUG` | Debug logging | `true` (optional) |

---

## Reading Traces

### Trace Structure

```
Run: "Review this code"
├── [1] Intent Classification
│   ├── Input: "Review this code"
│   ├── Output: code-review-preferences
│   └── Duration: 0.2s
├── [2] Load Skill
│   ├── Skill: code-review-preferences
│   ├── Tokens: 342
│   └── Duration: 0.05s
├── [3] Generate Response
│   ├── Output: [review content]
│   ├── Tokens: 1847 in / 892 out
│   └── Duration: 2.1s
└── Total: 4.35s
```

### What to Look For

| Signal | Meaning |
|--------|---------|
| Low confidence match | Skill description needs work |
| High token count | Skill too verbose |
| Long single step | Bottleneck found |
| Missing principles | Skill not loaded correctly |

---

## Trace Types

### Skill Activation

```
Match: skill-name (0.92 confidence)
Load: SKILL.md (342 tokens)
Intake: Questions generated
Route: workflow/path.md
```

### MCP Call

```
MCP: google-calendar.list-events
Request: {timeMin: ..., timeMax: ...}
Response: [{event1}, {event2}]
Duration: 0.4s
```

### Error

```
MCP: github.get-pull-request
Request: {pull_number: 999}
Response: ERROR - Not Found (404)
```

---

## Debugging with Traces

### Skill Not Triggering

Check the trace for:
- What skill was matched (if any)
- Confidence score
- User input that was classified

**Fix**: Update skill description to match input patterns.

### Wrong Behavior

Check the trace for:
- Which principles were loaded
- What routing decision was made
- What context was in scope

**Fix**: Adjust skill content or move critical rules up.

### Performance Issues

Check the trace for:
- Duration of each step
- Token counts (input/output)
- Bottleneck steps

**Fix**: Reduce token count, split into subagents, optimize prompts.

---

## Projects & Organization

### One Project Per Use Case

```
claude-code-mastery    # Learning/testing
work-productivity      # Daily work
team-reviews           # Team review workflow
```

### Naming Convention

```
{context}-{purpose}
```

Examples:
- `personal-productivity`
- `team-code-review`
- `project-deployment`

---

## Troubleshooting

| Issue | Cause | Fix |
|-------|-------|-----|
| No traces appearing | Tracing not enabled | Check `LANGSMITH_TRACING=true` |
| Empty traces | Key not set | Check `LANGSMITH_API_KEY` |
| Wrong project | Project not set | Check `LANGSMITH_PROJECT` |
| Auth error | Invalid key | Generate new key |

### Verify Setup

```bash
# Check variables
echo $LANGSMITH_TRACING
echo $LANGSMITH_API_KEY
echo $LANGSMITH_PROJECT

# Test trace
claude
> test
```
