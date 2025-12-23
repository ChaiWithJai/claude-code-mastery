# Skill Anatomy Reference

Quick reference for Claude Code skill structure.

---

## Directory Structure

```
~/.claude/skills/
└── my-skill/
    ├── SKILL.md          # Main skill file (required)
    ├── workflows/        # Optional workflow files
    │   ├── workflow-1.md
    │   └── workflow-2.md
    └── references/       # Optional reference files
        ├── patterns.md
        └── examples.md
```

---

## SKILL.md Structure

```markdown
---
name: skill-name
description: When to trigger this skill. Be specific.
---

<essential_principles>
Core knowledge loaded when skill triggers.
</essential_principles>

<intake>
Questions to clarify before proceeding.
</intake>

<routing>
Map user intent to workflows.
</routing>

<references>
Pointers to additional files.
</references>
```

---

## Frontmatter

```yaml
---
name: skill-name              # Identifier (lowercase, dashes)
description: |                # When to trigger
  Use when reviewing code,
  discussing code quality,
  or writing review comments.
---
```

**Tips:**
- Be specific about triggers
- Include key phrases users might say
- Description is matched against user input

---

## Essential Principles

```markdown
<essential_principles>
## Core Philosophy

### 1. [PRINCIPLE NAME]
[Why and how]

### 2. [PRINCIPLE NAME]
[Why and how]

## The Method

### Step 1: [Name]
[What to do]

## Checklist

- [ ] Required item
- [ ] Required item
</essential_principles>
```

**Tips:**
- 200-500 words typical
- Philosophy + methodology + checklists
- This is the "soul" of the skill

---

## Intake

```markdown
<intake>
Before proceeding, I need to understand:

1. **[Question]**
   - Option A
   - Option B

2. **[Open question]**

**Wait for answers before proceeding.**
</intake>
```

**Tips:**
- Prevents Claude from guessing
- Clarifies context before action
- "Wait for answers" is important

---

## Routing

```markdown
<routing>
Based on answers, route to:

| Intent | Workflow |
|--------|----------|
| "review" | `workflows/review.md` |
| "create" | `workflows/create.md` |
</routing>
```

**Tips:**
- Maps intent to workflow files
- Keeps main SKILL.md focused
- Workflows are Level 3 (loaded as needed)

---

## Progressive Disclosure

| Level | What | When Loaded |
|-------|------|-------------|
| 1 | Frontmatter (name, description) | Always |
| 2 | SKILL.md body | When triggered |
| 3 | Referenced files | As needed |

---

## Common Patterns

### Checklist Pattern
```markdown
## Must Do
- [ ] Item 1
- [ ] Item 2

## Should Do
- [ ] Item 1

## Nice to Have
- [ ] Item 1
```

### Do/Don't Pattern
```markdown
**DO:**
- Good practice 1
- Good practice 2

**DON'T:**
- Bad practice 1
- Bad practice 2
```

### Framework Pattern
```markdown
### 1. [PRINCIPLE IN CAPS]
[Explanation with examples]

### 2. [PRINCIPLE IN CAPS]
[Explanation with examples]
```

---

## Troubleshooting

| Issue | Cause | Fix |
|-------|-------|-----|
| Skill doesn't trigger | Description doesn't match | Add more trigger phrases |
| Principles ignored | Too far down in file | Move critical rules up |
| Too verbose | Too much content | Move details to references |
| Wrong routing | Routing table incorrect | Check intent matching |
