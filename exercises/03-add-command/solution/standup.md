---
name: standup
description: Generate a daily standup report based on git activity and open work
argument-hint: "[date: YYYY-MM-DD]"
---

# Standup Report Generator

Generate a concise standup report for async standups or daily sync meetings.

## Process

### 1. Gather Yesterday's Activity
```bash
# Get commits from last 24 hours
git log --oneline --since="24 hours ago" --author="$(git config user.name)"

# Get merged PRs (if using GitHub)
gh pr list --state merged --author @me --limit 5
```

### 2. Identify Today's Work
```bash
# Check current branch
git branch --show-current

# Check open PRs
gh pr list --author @me --state open
```

### 3. Identify Blockers
- Look for TODOs in recent commits
- Check for draft PRs waiting on dependencies
- Note any failing CI

## Output Format

```markdown
## Standup - [DATE]

### Done
- [Item 1: commit summary or PR merged]
- [Item 2]
- [Item 3]

### Today
- [Item 1: what you're working on]
- [Item 2]

### Blockers
- [Blocker 1: what's blocking and what you need]
- None
```

## Guidelines

- **Keep items to one line** - Details go in PRs/tickets
- **Use past tense for Done** - "Added X", "Fixed Y"
- **Use present/future for Today** - "Working on X", "Will review Y"
- **Be specific about blockers** - "Waiting on API spec from @person"

## Example Output

```markdown
## Standup - 2024-01-15

### Done
- Merged PR #234: Add DTI calculation endpoint
- Fixed flaky test in mortgage_test.py
- Reviewed Sarah's PR for loan validation

### Today
- Working on PR #236: Amortization schedule feature
- Meeting with platform team re: deployment pipeline

### Blockers
- Waiting on API spec for new risk scoring endpoint (following up with @mike)
```

## Usage

```bash
/standup           # Today's standup
/standup 2024-01-15  # Specific date
```
