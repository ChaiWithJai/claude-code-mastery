# Agent Patterns Reference

Quick reference for Claude Code agents.

---

## Agent vs Skill

| Aspect | Skill | Agent |
|--------|-------|-------|
| Purpose | Domain expertise | Workflow execution |
| Metaphor | "How to think" | "How to do" |
| Complexity | Single-step guidance | Multi-step process |
| Trigger | User asks about topic | User wants workflow done |

---

## Agent Structure

```markdown
# agents/my-agent.md

---
name: my-agent
description: Use when user wants [workflow]. Executes [process].
---

# [Agent Name]

## Role
[What this agent does]

## Trigger Phrases
- "Phrase 1"
- "Phrase 2"

## Process

### Step 1: [Name]
[What to do]

### Step 2: [Name]
[What to do]

### Step 3: [Name]
[What to do]

## Output Format
[Expected output structure]

## Dependencies
- [Skill or MCP it uses]
```

---

## Example: Code Review Agent

```markdown
---
name: code-reviewer
description: Use for complete code review workflow with PR integration.
---

# Code Review Agent

## Role
Execute end-to-end code review with GitHub integration.

## Trigger Phrases
- "Review PR #123"
- "Full code review"
- "Review and comment on this PR"

## Process

### Step 1: Fetch PR Details
- Get PR metadata
- Get list of changed files
- Get diff content

### Step 2: Initial Assessment
- Categorize change type
- Identify high-risk areas

### Step 3: Detailed Review
- Apply code-review-preferences skill
- Check against review checklist

### Step 4: Synthesize Feedback
- Prioritize comments
- Write summary

## Output Format
```markdown
## PR Review: #{number}

### Summary
[Assessment]

### Blocking Issues
- [ ] Issue 1

### Suggestions
- Suggestion 1

### Recommendation
[Approve / Request Changes]
```

## Dependencies
- GitHub MCP (for PR fetching)
- code-review-preferences skill
```

---

## Agent Patterns

### Sequential Pattern
Steps execute in order:
```
Step 1 → Step 2 → Step 3 → Output
```

### Branching Pattern
Different paths based on conditions:
```
Step 1 → (if X) → Step 2a → Output A
       → (if Y) → Step 2b → Output B
```

### Parallel Pattern
Multiple operations at once:
```
Step 1 → Step 2a ─┬─→ Synthesize → Output
       → Step 2b ─┘
```

### Loop Pattern
Repeat until condition met:
```
Step 1 → Step 2 → (check) → repeat or → Output
```

---

## Skill vs Agent Decision

**Use Skill when:**
- User needs guidance, not execution
- Single domain, single interaction
- Teaching principles/methodology

**Use Agent when:**
- User wants something done
- Multi-step process
- External tool integration
- Structured output needed

---

## Dependencies

Agents can depend on:
- **Skills**: For domain expertise
- **MCP servers**: For external APIs
- **Other agents**: For specialized subtasks

```markdown
## Dependencies
- code-review-preferences skill
- GitHub MCP server
- security-review agent (for security-focused PRs)
```

---

## Troubleshooting

| Issue | Cause | Fix |
|-------|-------|-----|
| Wrong agent triggers | Description overlap | Make triggers more specific |
| Steps skipped | Unclear step dependencies | Explicitly state dependencies |
| Output wrong format | Format not specified | Add output template |
| External call fails | MCP not configured | Check .mcp.json |
