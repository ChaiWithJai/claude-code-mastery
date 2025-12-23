# Exercise 5: Build a Domain Expertise Skill

**Duration**: 10-15 minutes
**Segment**: 7 (Domain Expertise Encoding)

---

## Objective

Encode YOUR expertise as a Claude Code skill using the framework pattern.

## Instructions

### Step 1: Choose Your Domain

What do you do repeatedly that involves expertise?

**Examples:**
- Sprint planning ritual
- Customer interview synthesis
- Technical decision documentation
- Incident post-mortem
- Architecture review
- Hiring interview evaluation
- Feature specification

### Step 2: List Your Components

**Principles** (3-5): What are the core beliefs?
1. ___
2. ___
3. ___

**Process** (3-5 steps): What's the methodology?
1. ___
2. ___
3. ___

**Output**: What's the deliverable format?
- ___

**Anti-patterns** (2-3): What mistakes should we avoid?
1. ___
2. ___

### Step 3: Create the Skill

```bash
mkdir -p ~/.claude/skills/my-expertise
touch ~/.claude/skills/my-expertise/SKILL.md
```

### Step 4: Fill in the Template

```markdown
---
name: my-expertise
description: Use when [trigger]. Applies [your methodology] for [outcome].
---

<framework_overview>
## What This Is
[One paragraph description]

## When to Use
- [Trigger 1]
- [Trigger 2]
- [Trigger 3]
</framework_overview>

<principles>
## Core Philosophy

### 1. [PRINCIPLE NAME]
[Why this matters and what it means in practice]

### 2. [PRINCIPLE NAME]
[Why this matters and what it means in practice]

### 3. [PRINCIPLE NAME]
[Why this matters and what it means in practice]
</principles>

<process>
## The Process

### Step 1: [Name]
[What to do and why]

### Step 2: [Name]
[What to do and why]

### Step 3: [Name]
[What to do and why]
</process>

<templates>
## Output Format

[Template for the deliverable]
</templates>

<anti-patterns>
## Common Mistakes

### 1. [ANTI-PATTERN NAME]
Why it's wrong: [explanation]
Instead: [correct approach]

### 2. [ANTI-PATTERN NAME]
Why it's wrong: [explanation]
Instead: [correct approach]
</anti-patterns>
```

### Step 5: Test It

```bash
claude
> Help me with [your domain task]
```

## Domain Ideas

| Domain | Trigger | Key Output |
|--------|---------|------------|
| Sprint Planning | "Plan the sprint" | Sprint backlog |
| Customer Interview | "Synthesize interview" | Insights document |
| Tech Decision | "Document decision" | ADR (Architecture Decision Record) |
| Post-Mortem | "Write post-mortem" | Incident report |
| Arch Review | "Review architecture" | Review findings |

## Verification

- [ ] Skill triggers on your domain phrase
- [ ] Has at least 3 principles
- [ ] Has at least 3 process steps
- [ ] Has output format defined
- [ ] Has at least 1 anti-pattern

## Example

See `solution/SKILL.md` for a complete technical decision skill.

---

**[Back to Segment 7 →](../../segments/07-domain-expertise.md)**
