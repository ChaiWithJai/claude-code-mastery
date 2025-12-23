# Segment 6: Git Workflow Guardrails

**Duration**: 15 minutes
**Builds**: Safety constraints for your team

---

## Learning Objectives

By the end of this segment, you will:
1. Understand why guardrails are essential
2. Know the pattern for creating constraint skills
3. Identify guardrails for your own workflow

---

## 6.1 The Horror Stories

### Without Guardrails

```bash
User: "Push this to production"
Claude: git push origin main --force
# Production is now broken
```

```bash
User: "Clean up old branches"
Claude: git branch -D main
# Main branch deleted locally
```

```bash
User: "Commit everything"
Claude: git add . && git commit -m "changes"
# .env file with secrets committed
```

**These actually happen.** Claude is helpful, not cautious.

---

## 6.2 The Guardrails Pattern

### A Guardrail is a Constraint Skill

```markdown
# ~/.claude/skills/git-workflow-guardrails/SKILL.md

---
name: git-workflow-guardrails
description: MANDATORY guardrails for git operations. Claude MUST follow these before ANY git push, merge, or commit to protected branches.
---

<essential_principles>
## NEVER Do These (Automatic Block)

1. **NEVER** run `git push origin main` directly
2. **NEVER** run `git push --force` to main/master
3. **NEVER** run `git branch -D main` or `git branch -D master`
4. **NEVER** commit files matching: .env, credentials.*, secrets.*
5. **NEVER** run `git reset --hard` without explicit user confirmation

## ALWAYS Do These

1. **ALWAYS** create a feature branch for changes
2. **ALWAYS** use `gh pr create` instead of direct pushes to main
3. **ALWAYS** check `git status` before committing
4. **ALWAYS** review staged files for secrets before commit
5. **ALWAYS** confirm with user before any destructive operation

## When User Requests Dangerous Operation

If user explicitly requests a blocked operation:
1. Explain why it's dangerous
2. Offer the safe alternative
3. If they insist, require them to type: "I understand the risk, proceed"

## Safe Patterns

### Pushing Changes
```bash
# Wrong
git push origin main

# Right
git checkout -b feature/my-change
git push -u origin feature/my-change
gh pr create --title "My change" --body "Description"
```

### Updating Main
```bash
# Wrong
git checkout main && git merge feature --no-ff

# Right
# Merge via PR on GitHub, then:
git checkout main
git pull origin main
```
</essential_principles>
```

---

## 6.3 How Guardrails Load

### Always-On Pattern

The skill description includes "MANDATORY" and "MUST":

```yaml
description: MANDATORY guardrails for git operations. Claude MUST follow these before ANY git push, merge, or commit to protected branches.
```

This ensures Claude considers this skill whenever git operations are involved.

### Trigger Words

Claude matches on:
- "push"
- "merge"
- "commit"
- "main"
- "master"
- "force"

When these appear in context with git, the guardrails activate.

---

## 6.4 Custom Guardrails

### Beyond Git

The same pattern works for any dangerous operation:

**Database Guardrails**
```markdown
## NEVER Do These
1. NEVER run DELETE without WHERE clause
2. NEVER run DROP TABLE in production
3. NEVER expose connection strings

## ALWAYS Do These
1. ALWAYS use parameterized queries
2. ALWAYS backup before schema changes
```

**API Guardrails**
```markdown
## NEVER Do These
1. NEVER commit API keys to git
2. NEVER call production APIs in tests
3. NEVER expose internal endpoints

## ALWAYS Do These
1. ALWAYS use environment variables for keys
2. ALWAYS use sandbox/test environments
```

**Deployment Guardrails**
```markdown
## NEVER Do These
1. NEVER deploy on Friday after 2pm
2. NEVER skip the staging environment
3. NEVER deploy without running tests

## ALWAYS Do These
1. ALWAYS check CI status before deploy
2. ALWAYS have rollback plan ready
```

---

## Pause Point #4

**Task**: Identify guardrails for YOUR team

**Duration**: 3 minutes

**Questions to Answer**:
1. What's the most dangerous command someone could run?
2. What secrets should never be committed?
3. What's your "never do this on Friday" rule?
4. What needs explicit confirmation before proceeding?

**Write down 3-5 NEVER rules and 3-5 ALWAYS rules.**

---

## 6.5 Team Guardrails

### Sharing Guardrails

Put guardrails in your team plugin:

```
team-plugin/
├── skills/
│   └── guardrails/
│       └── SKILL.md      # Team guardrails
└── CLAUDE.md             # Reference guardrails
```

### In CLAUDE.md

```markdown
## Safety

Before any operation that modifies:
- Git history
- Database records
- Production systems
- Deployed infrastructure

Claude MUST load and follow the guardrails skill.
```

---

## 6.6 Testing Guardrails

### Verify They Work

```bash
claude
> Push this directly to main
```

Expected response:
```
I can't push directly to main. This is blocked by team guardrails.

Instead, let's:
1. Create a feature branch
2. Push to the feature branch
3. Open a PR for review

Would you like me to do that instead?
```

### If It Doesn't Work

1. Check skill is in the right directory
2. Check description includes trigger words
3. Check NEVER rules are at top of essential_principles

---

## Key Takeaways

1. **Guardrails prevent disasters**—Claude is helpful, not cautious
2. **Use NEVER/ALWAYS pattern**—clear, unambiguous rules
3. **Trigger on dangerous words**—push, force, delete, drop
4. **Require confirmation for overrides**—user must acknowledge risk
5. **Share with team**—put in team plugin

---

**[Next: Segment 7 - Domain Expertise Encoding →](07-domain-expertise.md)**

---

## Notes for Instructor

### Key Points to Land
1. These are REAL risks—show the horror stories
2. The pattern is simple: NEVER do X, ALWAYS do Y
3. Test your guardrails before trusting them

### Live Demo
- Try to get Claude to push to main
- Show how guardrails block it
- Show the alternative path offered

### Common Questions
- "Can I override guardrails?" → Yes, with explicit acknowledgment
- "What if I need to push to main?" → PR is always safer
- "How do I know they're working?" → Test them explicitly
