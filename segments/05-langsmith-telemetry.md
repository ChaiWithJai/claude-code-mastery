# Segment 5: LangSmith Telemetry

**Duration**: 20 minutes
**Builds**: Tracing setup for your Claude Code

---

## Learning Objectives

By the end of this segment, you will:
1. Understand why tracing matters
2. Configure LangSmith for Claude Code
3. Read and interpret traces

---

## 5.1 Why Trace Everything?

### Without Traces

```
User: "Review this code"
Claude: [does something]
User: "That wasn't what I wanted"
Claude: [does something else]
User: "Why isn't this working?"
```

**Debugging**: Guesswork

### With Traces

```
Trace: "Review this code"
├── Intent Classification (0.92 → code-review-preferences)
├── Load SKILL.md
│   └── Parsed 342 tokens
├── Generate Response
│   ├── Applied principle: "Max 5 comments"
│   └── Used checklist: 4/6 items checked
└── Token Usage: 1,247 in / 523 out
```

**Debugging**: Exact visibility into what happened

---

## 5.2 What Traces Show You

### Skill Activation
- Which skill was triggered
- Confidence score
- What was loaded

### Decision Making
- Which principles were applied
- What routing decisions were made
- Why certain paths were taken

### External Calls
- MCP server invocations
- API responses
- Error handling

### Performance
- Token usage (cost tracking)
- Latency per step
- Bottlenecks

---

## 5.3 Setting Up LangSmith

### Step 1: Create Account

1. Go to [smith.langchain.com](https://smith.langchain.com)
2. Sign up (free tier available)
3. Create a project: "claude-code-mastery"

### Step 2: Get API Key

1. Settings → API Keys
2. Create new key
3. Copy it (you won't see it again)

### Step 3: Configure Claude Code

Add to your shell config (~/.zshrc or ~/.bashrc):

```bash
export LANGSMITH_TRACING=true
export LANGSMITH_API_KEY="lsv2_pt_your_key_here"
export LANGSMITH_PROJECT="claude-code-mastery"
```

Or add to Claude Code settings:

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

### Step 4: Verify

```bash
source ~/.zshrc  # or restart terminal
claude
> Hello
```

Check LangSmith—you should see a trace appear.

---

## 5.4 Reading Traces

### Trace Anatomy

```
Run: "Review this code for security issues"
│
├── [1] Intent Classification
│   ├── Input: "Review this code for security issues"
│   ├── Output: code-review-preferences (confidence: 0.94)
│   └── Duration: 0.2s
│
├── [2] Load Skill
│   ├── Skill: code-review-preferences
│   ├── Tokens loaded: 342
│   └── Duration: 0.05s
│
├── [3] Generate Intake Questions
│   ├── Questions: ["What type of review?", "Context?"]
│   └── Duration: 0.8s
│
├── [4] User Response
│   └── Input: "Security audit, it's a payment handler"
│
├── [5] Apply Principles
│   ├── Active principles:
│   │   - "Check for injection vulnerabilities"
│   │   - "Verify input validation"
│   │   - "Review auth boundaries"
│   └── Duration: 1.2s
│
└── [6] Generate Review
    ├── Output: [structured review with 3 security findings]
    ├── Tokens: 1,847 in / 892 out
    └── Duration: 2.1s

Total Duration: 4.35s
Total Tokens: 2,739
```

### What to Look For

| Signal | Meaning |
|--------|---------|
| Low confidence match | Skill description needs work |
| High token count | Skill is too verbose |
| Long duration on one step | Bottleneck identified |
| Missing principles | Skill not loaded correctly |
| Wrong routing | Routing table needs adjustment |

---

## 5.5 Trace Walkthrough: Real Examples

### Example 1: Skill Activation

```
Trace: "Help me write positioning for my product"
├── Match: pmm-best-practices (0.96)
├── Load SKILL.md (892 tokens)
├── Intake questions generated
└── User routed to: workflows/create-positioning.md
```

**What we learn**: Skill matched correctly, routed to right workflow.

### Example 2: MCP Call

```
Trace: "/briefing"
├── Load command: briefing.md
├── MCP Call: google-calendar.list-events
│   ├── Request: {timeMin: "2024-01-15T00:00:00", timeMax: "..."}
│   ├── Response: [{summary: "Team standup", start: {...}}]
│   └── Duration: 0.4s
├── MCP Call: google-tasks.list-tasks
│   └── Response: [{title: "Review PR #234", ...}]
└── Synthesize briefing
```

**What we learn**: Both MCP calls succeeded, data was available.

### Example 3: Debug Failure

```
Trace: "Review PR #500"
├── Match: code-reviewer (0.88)
├── Load agent: code-reviewer.md
├── MCP Call: github.get-pull-request
│   ├── Request: {owner: "...", repo: "...", pull_number: 500}
│   ├── Response: ERROR - Not Found (404)
│   └── Duration: 0.2s
└── Error: "Could not find PR #500"
```

**What we learn**: PR doesn't exist. Not a Claude problem—data problem.

---

## 5.6 Advanced: Evaluations

### Beyond Tracing

LangSmith also supports:
- **Evaluations**: Score outputs against criteria
- **Datasets**: Track inputs/outputs over time
- **Experiments**: A/B test different prompts

### Simple Evaluation Example

```python
from langsmith import Client

client = Client()

# Create evaluation criteria
def check_security_coverage(run):
    output = run.outputs["response"]
    security_keywords = ["injection", "auth", "validation"]
    coverage = sum(1 for kw in security_keywords if kw in output.lower())
    return {"score": coverage / len(security_keywords)}

# Run evaluation
client.evaluate(
    dataset_name="code-review-samples",
    evaluators=[check_security_coverage]
)
```

We won't build this today, but it's where you go next.

---

## Key Takeaways

1. **Traces show exactly what happened**—no guesswork
2. **Configure once, trace forever**—always on
3. **Look for patterns**: low confidence, high tokens, slow steps
4. **Debug with evidence**, not intuition
5. **Evaluations are next level**—once you have traces, you can score them

---

**[Next: Segment 6 - Git Workflow Guardrails →](06-git-guardrails.md)**

---

## Notes for Instructor

### Key Points to Land
1. Traces are like logs for AI—essential for debugging
2. Show a REAL trace, not a mock
3. Point out specific things to look for

### Live Demo Notes
- Have LangSmith open in browser
- Trigger a skill, show the trace appearing
- Walk through each step in the trace

### Common Issues
- Traces not appearing → Check API key is set
- Empty traces → Check LANGSMITH_TRACING=true
- Wrong project → Check LANGSMITH_PROJECT value
