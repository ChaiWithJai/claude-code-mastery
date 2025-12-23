# Segment 2: Build Your First Skill

**Duration**: 40 minutes
**Builds**: Complete skill with SKILL.md

---

## Learning Objectives

By the end of this segment, you will:
1. Understand skill anatomy (frontmatter, principles, intake, routing)
2. Create a complete skill from scratch
3. Test and iterate on your skill

---

## 2.1 Skill Anatomy

### What is a Skill?

A skill is **encoded domain expertise** that Claude Code loads when triggered.

```
User: "Review this code"
        ↓
Claude Code: Matches "code review" → loads code-review skill
        ↓
Skill: Provides checklist, patterns, principles
        ↓
Claude: Reviews code using YOUR standards
```

### The Four Components

```markdown
# SKILL.md

---
name: skill-name
description: When to trigger this skill (matched by Claude)
---

<essential_principles>
Core knowledge that's always relevant when skill is active
</essential_principles>

<intake>
Questions to clarify user intent before proceeding
</intake>

<routing>
Decision table: intent → workflow
</routing>

<references>
Pointers to additional files loaded as needed
</references>
```

---

## 2.2 Component Deep Dive

### Frontmatter (Always Loaded)

```yaml
---
name: code-review-preferences
description: Use when reviewing code, PRs, or discussing code quality standards. Applies the team's coding standards and review checklist.
---
```

**Key Points:**
- `name`: How you reference the skill
- `description`: When Claude should trigger it (be specific)
- This is Level 1—always in Claude's context (~50 words)

### Essential Principles (Loaded on Trigger)

```markdown
<essential_principles>
## Code Review Philosophy

We review for:
1. **Correctness** - Does it work?
2. **Clarity** - Can others understand it?
3. **Consistency** - Does it match our patterns?

We do NOT review for:
- Style nitpicks (linter handles this)
- Personal preferences
- Hypothetical future requirements

## The 3-Pass Method
1. First pass: Understand what changed (don't comment yet)
2. Second pass: Check for bugs and logic errors
3. Third pass: Suggest improvements (max 3)

## Review Tone
- Assume good intent
- Ask questions, don't dictate
- "What if we..." not "You should..."
</essential_principles>
```

**Key Points:**
- This is Level 2—loaded when skill triggers
- Should be 200-500 words of dense expertise
- Philosophy + methodology + constraints

### Intake (Clarification)

```markdown
<intake>
Before reviewing, I need to understand:

1. **What type of review?**
   - Quick sanity check (5 min)
   - Thorough review (30 min)
   - Architecture review (deep dive)

2. **What's the context?**
   - New feature
   - Bug fix
   - Refactor
   - Performance optimization

3. **Any specific concerns?**
   - Security implications?
   - Breaking changes?
   - Performance critical?

**Wait for answers before proceeding.**
</intake>
```

**Key Points:**
- Prevents Claude from guessing
- Gets context before acting
- The "Wait for answers" is important

### Routing (Decision Table)

```markdown
<routing>
Based on answers, route to:

| Type | Context | Workflow |
|------|---------|----------|
| Quick | Any | `workflows/quick-review.md` |
| Thorough | Bug fix | `workflows/bug-review.md` |
| Thorough | New feature | `workflows/feature-review.md` |
| Architecture | Any | `workflows/arch-review.md` |
</routing>
```

**Key Points:**
- Maps intent to specific workflows
- Workflows are separate files (Level 3)
- Keeps main SKILL.md focused

---

## 2.3 Live Build: Code Review Skill

### Step 1: Create skill directory

```bash
mkdir -p ~/.claude/skills/code-review-preferences
cd ~/.claude/skills/code-review-preferences
```

### Step 2: Create SKILL.md

```bash
touch SKILL.md
```

### Step 3: Add frontmatter

```markdown
---
name: code-review-preferences
description: Use when reviewing code, PRs, or discussing code quality. Applies team coding standards and review methodology.
---
```

### Step 4: Add essential principles

```markdown
<essential_principles>
## Code Review Philosophy

Reviews exist to:
1. Catch bugs before production
2. Share knowledge across team
3. Maintain code consistency

Reviews do NOT exist to:
- Show off knowledge
- Enforce personal style
- Block progress

## The Review Checklist

### Must Check
- [ ] Tests pass
- [ ] No obvious bugs
- [ ] Handles edge cases mentioned in PR
- [ ] No security vulnerabilities

### Should Check
- [ ] Code is readable
- [ ] Functions are reasonably sized
- [ ] Names are clear

### Nice to Check
- [ ] Performance considerations
- [ ] Documentation updated
- [ ] Future maintainability

## Feedback Style
- Use questions: "What happens if X?"
- Be specific: Line numbers, concrete suggestions
- Limit feedback: Max 5 comments per review
- Acknowledge good work: "Nice refactor here"
</essential_principles>
```

### Step 5: Add intake

```markdown
<intake>
What would you like me to review?

1. **Paste the code/diff** - I'll review inline
2. **Point to a file** - Use @filename to reference
3. **Describe the PR** - I'll ask clarifying questions

What's the context?
- Bug fix
- New feature
- Refactor
- Other: ___

Any specific concerns you want me to focus on?
</intake>
```

### Step 6: Test it

```bash
claude
> Review this function: [paste code]
```

Watch Claude load your skill and apply your standards.

---

## Pause Point #2

**Task**: Create a skill skeleton for YOUR use case

**Duration**: 5 minutes

**Options**:
- Code review preferences (follow along)
- Standup formatter
- Documentation template
- Your own workflow

**Verify**:
- [ ] Skill directory created
- [ ] SKILL.md has frontmatter
- [ ] Has at least one `<essential_principles>` section
- [ ] Has basic `<intake>` questions

---

## 2.4 Testing and Iteration

### How to Know It's Working

1. **Check skill loads**:
   ```
   > /skills
   # Should list your skill
   ```

2. **Test trigger**:
   ```
   > Review this code
   # Should activate code-review-preferences
   ```

3. **Check behavior**:
   - Does it ask intake questions?
   - Does it follow your principles?
   - Does it use your checklist?

### Common Issues

| Issue | Fix |
|-------|-----|
| Skill doesn't trigger | Description doesn't match intent—be more specific |
| Principles ignored | Move critical rules to top of essential_principles |
| Too generic | Add more specific examples and constraints |
| Too verbose | Trim to essentials, move details to reference files |

---

## LangSmith Trace: Skill Activation

```
Trace: "Review this code"
├── Intent Classification
│   └── Matches: code-review-preferences (0.92 confidence)
├── Load SKILL.md
│   ├── Parse frontmatter
│   ├── Load essential_principles
│   └── Load intake
├── Generate Intake Questions
│   └── "What's the context? Any concerns?"
└── Wait for User Response
```

This is what we'll see in Segment 5.

---

## Key Takeaways

1. **Skills are encoded expertise**, not configuration
2. **Four components**: frontmatter, principles, intake, routing
3. **Progressive disclosure**: frontmatter always, body on trigger
4. **Test and iterate**: Skills improve with use

---

**[Next: Segment 3 - Plugin Architecture →](03-plugin-architecture.md)**

---

## Notes for Instructor

### Key Points to Land
1. Skills are YOUR expertise, encoded
2. The structure matters: frontmatter → principles → intake → routing
3. Testing is easy—just trigger and observe

### Live Coding Notes
- Type slowly, explain each section
- Show the file structure in VS Code
- Test immediately after creating

### If People Are Lost
- Point them to `examples/skills/code-review-preferences/`
- Have them copy and modify rather than write from scratch
- Pair faster people with slower ones
