# Exercise 4: Identify Team Guardrails

**Duration**: 5 minutes
**Segment**: 6 (Git Workflow Guardrails)

---

## Objective

Identify dangerous operations for your team and create guardrail rules.

## Instructions

### Step 1: Answer These Questions

**What's the most dangerous command someone could run?**
- Git: `git push --force`, `git reset --hard`, `git branch -D main`
- Database: `DELETE`, `DROP TABLE`, `TRUNCATE`
- Deployment: `deploy production`, `kubectl delete`
- Other: ___

**What secrets should NEVER be committed?**
- `.env` files
- `credentials.json`
- API keys
- Private keys
- Other: ___

**What's your team's "never do this" rule?**
- Deploy on Friday after 2pm
- Skip code review
- Merge without tests passing
- Other: ___

**What needs explicit confirmation?**
- Destructive operations
- Production deployments
- Data migrations
- Other: ___

### Step 2: Write Your NEVER Rules

Fill in these templates:

```markdown
## NEVER Do These

1. NEVER [dangerous operation 1]
   Why: [consequence]

2. NEVER [dangerous operation 2]
   Why: [consequence]

3. NEVER [dangerous operation 3]
   Why: [consequence]
```

### Step 3: Write Your ALWAYS Rules

```markdown
## ALWAYS Do These

1. ALWAYS [safe practice 1]
   How: [specific command or process]

2. ALWAYS [safe practice 2]
   How: [specific command or process]

3. ALWAYS [safe practice 3]
   How: [specific command or process]
```

### Step 4: (Optional) Create the Skill

If time permits, create the guardrails skill:

```bash
mkdir -p ~/.claude/skills/team-guardrails
touch ~/.claude/skills/team-guardrails/SKILL.md
```

## Guardrail Categories

### Git Operations
- Force push to protected branches
- Delete main/master branch
- Reset without backup

### Database Operations
- DELETE/DROP without WHERE
- Run migrations in production without backup
- Expose connection strings

### Deployment Operations
- Deploy outside of deploy windows
- Skip staging environment
- Deploy without running tests

### Security Operations
- Commit secrets
- Disable security features
- Expose internal endpoints

## Verification

- [ ] Identified at least 3 NEVER rules
- [ ] Identified at least 3 ALWAYS rules
- [ ] Rules are specific (not vague)
- [ ] Rules include "why" or consequences

## Example

See `solution/guardrails.md` for a complete guardrails skill.

---

**[Back to Segment 6 →](../../segments/06-git-guardrails.md)**
