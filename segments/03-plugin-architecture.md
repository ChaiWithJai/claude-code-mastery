# Segment 3: Plugin Architecture

**Duration**: 35 minutes
**Builds**: Agent + command added to your skill

---

## Learning Objectives

By the end of this segment, you will:
1. Understand plugin structure (skills, agents, commands, MCP)
2. Create an agent for a specific workflow
3. Create a command for quick actions

---

## 3.1 Plugin Structure Overview

### What is a Plugin?

A plugin bundles related capabilities:
- **Skills**: Domain expertise (the "how to think")
- **Agents**: Workflow execution (the "how to do")
- **Commands**: Quick actions (the "shortcuts")
- **MCP Servers**: External integrations (the "connections")

### Directory Structure

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── .mcp.json                 # MCP server configuration
├── CLAUDE.md                 # Project documentation
├── agents/
│   ├── morning-briefing.md
│   └── code-reviewer.md
├── commands/
│   ├── standup.md           # /standup
│   └── plugin:prep.md       # /plugin:prep (namespaced)
├── skills/
│   └── code-review/
│       └── SKILL.md
└── setup.sh                  # Configuration script
```

---

## 3.2 Plugin Manifest

### .claude-plugin/plugin.json

```json
{
  "name": "my-productivity-plugin",
  "version": "1.0.0",
  "description": "Personal productivity workflows for code review and standup",
  "author": "Your Name",
  "setup": "./setup.sh",
  "keywords": ["productivity", "code-review", "standup"],
  "repository": "https://github.com/you/my-productivity-plugin"
}
```

**Key Fields:**
- `name`: Plugin identifier
- `version`: Semantic versioning
- `setup`: Script for first-time configuration
- `keywords`: For discoverability

---

## 3.3 Creating Agents

### What is an Agent?

An agent is a **specialized workflow** that executes multi-step processes.

```
Skill: "Here's how to think about code review"
Agent: "Here's how to execute a full code review workflow"
```

### Agent Anatomy

```markdown
# agents/code-reviewer.md

---
name: code-reviewer
description: Use when the user wants a complete code review workflow, including fetching PR details, reviewing changes, and posting feedback.
---

# Code Reviewer Agent

## Role
Execute end-to-end code review workflow with PR integration.

## Trigger Phrases
- "Review PR #123"
- "Full code review"
- "Review and comment on this PR"

## Process

### Step 1: Fetch PR Details
- Get PR metadata (title, description, author)
- Get list of changed files
- Get diff content

### Step 2: Initial Assessment
- Categorize the change (bug fix, feature, refactor)
- Identify high-risk areas
- Note files requiring careful review

### Step 3: Detailed Review
- Apply code-review-preferences skill
- Check each file against review checklist
- Generate specific, actionable feedback

### Step 4: Synthesize Feedback
- Prioritize comments (blocking vs. suggestions)
- Write summary comment
- Provide approval recommendation

## Output Format
```markdown
## PR Review: #{number}

### Summary
[One paragraph assessment]

### Blocking Issues
- [ ] Issue 1 (file:line)
- [ ] Issue 2 (file:line)

### Suggestions
- Suggestion 1
- Suggestion 2

### Recommendation
[Approve / Request Changes / Needs Discussion]
```

## Dependencies
- GitHub MCP server (for PR fetching)
- code-review-preferences skill (for review standards)
```

### Live Build: Add an Agent

```bash
mkdir -p agents
touch agents/code-reviewer.md
```

Add the content above, customized for your workflow.

---

## 3.4 Creating Commands

### What is a Command?

A command is a **quick action** triggered by `/command-name`.

```
Agent: Multi-step workflow
Command: One-shot action
```

### Command Anatomy

```markdown
# commands/standup.md

---
name: standup
description: Generate a daily standup report based on recent work
argument-hint: "[optional: date]"
---

# Standup Report

Generate a standup report for today (or specified date).

## Process

1. Check git log for recent commits (last 24 hours)
2. Check open PRs
3. Check calendar for meetings
4. Format as standup

## Output Format

```markdown
## Daily Standup - {date}

### Yesterday
- {commit summaries}
- {PRs merged}

### Today
- {calendar events}
- {planned work based on open PRs}

### Blockers
- {any identified blockers}
```

## Usage

```bash
/standup           # Today's standup
/standup 2024-01-15  # Specific date
```
```

### Namespaced Commands

To avoid collisions with built-in commands:

```markdown
# commands/myplug:prep.md

---
name: myplug:prep
description: Prepare for a meeting by gathering context
argument-hint: "<meeting-name>"
---
```

Usage: `/myplug:prep design-review`

---

## Pause Point #3

**Task**: Add a command to your skill/plugin

**Duration**: 5 minutes

**Options**:
- `/standup` - Daily standup generator
- `/review` - Quick code review
- `/doc` - Documentation generator
- Your own: `/yourcommand`

**Verify**:
- [ ] Command file created in `commands/`
- [ ] Has frontmatter with name and description
- [ ] Has output format defined
- [ ] Test with `/yourcommand`

---

## 3.5 Plugin vs. User-Level Organization

### User-Level (~/.claude/)

```
~/.claude/
├── skills/           # Skills available in ALL projects
├── agents/           # Agents available in ALL projects
└── commands/         # Commands available in ALL projects
```

**Use for**: Personal workflows that apply everywhere

### Plugin-Level (project directory)

```
my-project/
├── .claude-plugin/   # Plugin manifest
├── skills/           # Project-specific skills
├── agents/           # Project-specific agents
└── commands/         # Project-specific commands
```

**Use for**: Team-shared or project-specific workflows

### Precedence

```
1. Project plugin (highest priority)
2. User-level ~/.claude/
3. Built-in Claude Code (lowest priority)
```

---

## 3.6 Testing Your Plugin

### Verify Plugin Loads

```bash
claude
> /plugins
# Should list your plugin
```

### Verify Agent Triggers

```bash
> Review PR #123
# Should trigger code-reviewer agent
```

### Verify Command Works

```bash
> /standup
# Should generate standup report
```

---

## Key Takeaways

1. **Plugins bundle capabilities**: skills, agents, commands, MCP
2. **Agents are workflows**: Multi-step processes
3. **Commands are shortcuts**: Quick one-shot actions
4. **Namespace to avoid collisions**: `/myplugin:command`
5. **User-level vs project-level**: Personal vs shared

---

**[Next: Segment 4 - MCP Server Integration →](04-mcp-integration.md)**

---

## Notes for Instructor

### Key Points to Land
1. Skills = knowledge, Agents = workflows, Commands = shortcuts
2. Show the plugin.json and how it ties everything together
3. Namespace commands to avoid collisions

### Live Coding Notes
- Create the agent file live
- Show how triggers work (say the phrase, watch it activate)
- Test the command immediately

### Common Questions
- "What's the difference between skill and agent?" → Skill is expertise, agent is workflow
- "Can commands call agents?" → Yes, commands can trigger agent workflows
- "Where should I put things?" → Personal = ~/.claude/, team = plugin
