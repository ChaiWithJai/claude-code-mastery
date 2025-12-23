# Exercise 2: Build Your First Skill

**Duration**: 10-15 minutes
**Segment**: 2 (Build Your First Skill)

---

## Objective

Create a complete Claude Code skill with frontmatter, essential principles, and intake questions.

## Instructions

### Step 1: Create Skill Directory

```bash
mkdir -p ~/.claude/skills/my-first-skill
cd ~/.claude/skills/my-first-skill
```

### Step 2: Create SKILL.md

```bash
touch SKILL.md
```

### Step 3: Add Frontmatter

```yaml
---
name: my-first-skill
description: Use when [your trigger condition]. Applies [your methodology/framework].
---
```

### Step 4: Add Essential Principles

```markdown
<essential_principles>
## [Your Domain] Philosophy

### Principle 1: [NAME]
[Why this matters and what it means in practice]

### Principle 2: [NAME]
[Why this matters and what it means in practice]

### Principle 3: [NAME]
[Why this matters and what it means in practice]

## The Checklist

### Must Do
- [ ] [Required item 1]
- [ ] [Required item 2]

### Should Do
- [ ] [Recommended item 1]
- [ ] [Recommended item 2]
</essential_principles>
```

### Step 5: Add Intake Questions

```markdown
<intake>
Before proceeding, I need to understand:

1. **[Question 1]**
   - Option A
   - Option B
   - Option C

2. **[Question 2]**
   [Open-ended question]

3. **Any specific constraints or concerns?**

**Wait for answers before proceeding.**
</intake>
```

### Step 6: Test Your Skill

```bash
claude
> [Trigger phrase that should activate your skill]
```

## Skill Ideas

Choose one of these or create your own:

| Skill | Trigger | Purpose |
|-------|---------|---------|
| code-review | "Review this code" | Apply your team's review standards |
| standup-formatter | "Format standup" | Structure daily standup reports |
| tech-spec | "Write a spec" | Template for technical specifications |
| incident-response | "Debug this issue" | Systematic debugging approach |

## Verification

- [ ] SKILL.md exists in `~/.claude/skills/your-skill/`
- [ ] Frontmatter has name and description
- [ ] Has `<essential_principles>` section
- [ ] Has at least 3 principles
- [ ] Has `<intake>` section with questions
- [ ] Skill triggers when you use the trigger phrase

## Example

See `solution/SKILL.md` for a complete code-review skill.

---

**[Back to Segment 2 →](../../segments/02-first-skill.md)**
