# Exercise 3: Add a Command

**Duration**: 5-10 minutes
**Segment**: 3 (Plugin Architecture)

---

## Objective

Create a Claude Code command that executes with `/your-command`.

## Instructions

### Step 1: Create Commands Directory

```bash
mkdir -p ~/.claude/commands
cd ~/.claude/commands
```

### Step 2: Create Command File

```bash
touch standup.md
```

### Step 3: Add Frontmatter

```yaml
---
name: standup
description: Generate a daily standup report based on recent activity
argument-hint: "[optional: date YYYY-MM-DD]"
---
```

### Step 4: Add Command Body

```markdown
# Standup Report Generator

Generate a standup report for today (or the specified date).

## Process

1. Check git log for recent commits (last 24 hours)
2. Check for open PRs
3. Identify any blockers mentioned in recent work
4. Format as standup

## Output Format

```markdown
## Daily Standup - {date}

### Yesterday
- [Completed items from git log]
- [PRs merged]

### Today
- [Planned work based on open PRs/branches]
- [Calendar items if available]

### Blockers
- [Any identified blockers, or "None"]
```

## Notes

- Keep items concise (one line each)
- Focus on outcomes, not activities
- If no git activity, note that and ask what was worked on
```

### Step 5: Test Your Command

```bash
claude
> /standup
```

## Command Ideas

| Command | Trigger | Purpose |
|---------|---------|---------|
| `/standup` | Daily standup | Format standup report |
| `/doc` | Documentation | Generate docs for code |
| `/commit` | Git commit | Format commit message |
| `/review` | Quick review | Fast code review |

## Namespacing

To avoid collisions with built-in commands, use a prefix:

```yaml
---
name: mytools:standup
description: ...
---
```

Usage: `/mytools:standup`

## Verification

- [ ] Command file exists in `~/.claude/commands/`
- [ ] Frontmatter has name and description
- [ ] Has argument-hint (if arguments accepted)
- [ ] Has process/output format documented
- [ ] Command works when invoked

## Example

See `solution/standup.md` for a complete standup command.

---

**[Back to Segment 3 →](../../segments/03-plugin-architecture.md)**
