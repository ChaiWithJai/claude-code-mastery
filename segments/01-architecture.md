# Segment 1: The Architecture Mind Shift

**Duration**: 20 minutes
**Builds**: CLAUDE.md skeleton for your project

---

## Learning Objectives

By the end of this segment, you will:
1. Understand why CLAUDE.md is architecture documentation, not a config file
2. Know the "soul lives in prompts" philosophy
3. Have created a CLAUDE.md skeleton for your project

---

## 1.1 CLAUDE.md is Not .cursorrules

### The Problem with .cursorrules

```
# .cursorrules
- Use TypeScript
- Prefer functional components
- Always add error handling
```

**What happens:**
- Sometimes followed, sometimes ignored
- No structure, just vibes
- Resets every session
- AI doesn't understand your architecture

### CLAUDE.md is Different

```markdown
# My Project

## What This Project Does
A mortgage calculation service that processes loan applications.

## Architecture
├── src/
│   ├── calculations/     # Pure functions for financial math
│   ├── validators/       # Input validation
│   └── api/              # Express routes
├── tests/                # Jest unit tests
└── scripts/              # CLI tools

## Key Patterns
- All calculations are pure functions (no side effects)
- Validation happens at API boundary
- Financial amounts use Decimal.js (never floats)

## Development Workflow
1. Run tests: `npm test`
2. Start dev server: `npm run dev`
3. Deploy: `./scripts/deploy.sh`
```

**What happens:**
- Claude reads this on every session
- Understands your actual architecture
- Makes decisions consistent with your patterns
- Compounds over time as you add detail

---

## 1.2 The "Soul Lives in Prompts" Philosophy

### From deep-agent-scaffold

> "Aim for 100-500 lines of pure domain expertise in prompts.
> Tools return prompts/structured data for Claude to evaluate.
> The system prompt IS the product."

### What This Means

```
Traditional Approach:
  Code defines behavior
  AI assists with implementation
  Prompts are afterthoughts

Claude Code Approach:
  Prompts define behavior
  Code enables capabilities
  Architecture IS documentation
```

### Example: PMM Agent System Prompt

```python
SYSTEM_PROMPT = """
You are a B2B product marketing expert with deep expertise in:
- April Dunford's positioning methodology
- Messaging hierarchy frameworks
- ICP development and segmentation
- Competitive differentiation

## Core Principles

1. POSITIONING IS PIGEONHOLING
   You can't be everything to everyone. Own a specific place
   in YOUR customer's mind, not the general market.

2. CUSTOMER PERCEPTION IS REALITY
   It doesn't matter what you think you are. It matters what
   customers perceive you to be.

3. CLARITY OVER CLEVERNESS
   Boring and clear beats clever and confusing every time.
   If a 12-year-old can't explain it, simplify.

... [300 more lines of domain expertise]
"""
```

**The prompt IS the expert.** Code just enables it.

---

## 1.3 Progressive Disclosure Design

### How Claude Code Loads Context

```
Level 1: Always Loaded (~100 words)
  └── Skill/Agent metadata (name, description, triggers)

Level 2: On Trigger (<5,000 words)
  └── Full SKILL.md or agent prompt

Level 3: As Needed (unlimited)
  └── Reference files, bundled resources
```

### Why This Matters

- CLAUDE.md loads at Level 1 (always in context)
- Skills load at Level 2 (when triggered)
- References load at Level 3 (when needed)

**Implication:** Your CLAUDE.md should be dense, not exhaustive. It's an index, not a manual.

---

## Live Build: CLAUDE.md Skeleton

### Step 1: Create the file

```bash
cd /path/to/your/project
touch CLAUDE.md
```

### Step 2: Add the structure

```markdown
# [Project Name]

[One sentence: What this project does]

## Architecture

```
[Directory structure with explanations]
```

## Key Patterns

- [Pattern 1: Why this matters]
- [Pattern 2: Why this matters]
- [Pattern 3: Why this matters]

## Development Workflow

1. [How to run tests]
2. [How to start dev]
3. [How to deploy]

## What NOT to Do

- [Anti-pattern 1]
- [Anti-pattern 2]
```

### Step 3: Fill in YOUR project

Take 3 minutes. Fill in the skeleton for your actual project.

---

## Pause Point #1

**Task**: Create CLAUDE.md skeleton for your project

**Duration**: 3 minutes

**Verify**:
- [ ] File exists at project root
- [ ] Has project description
- [ ] Has architecture section
- [ ] Has at least 2 key patterns

---

## Key Takeaways

1. **CLAUDE.md is architecture documentation**, not a config file
2. **Prompts define behavior**, code enables capabilities
3. **Progressive disclosure** keeps context efficient
4. **Dense, not exhaustive**—CLAUDE.md is an index

---

## LangSmith Trace Preview

In Segment 5, we'll see how Claude Code reads CLAUDE.md:

```
Trace: Session Start
├── Load CLAUDE.md (Level 1)
├── Parse architecture section
├── Index key patterns
└── Ready for interaction
```

Every session starts with this. Your architecture is always in context.

---

**[Next: Segment 2 - Build Your First Skill →](02-first-skill.md)**

---

## Notes for Instructor

### Key Points to Land
1. CLAUDE.md is read EVERY session (unlike .cursorrules which is hit-or-miss)
2. Think of it as writing documentation for a smart colleague
3. The "soul lives in prompts" = your expertise, encoded

### Common Questions
- "How long should CLAUDE.md be?" → As long as needed, but dense. 500-2000 words typical.
- "What if my project is complex?" → Focus on patterns, not exhaustive detail.
- "Do I need to update it constantly?" → Update when architecture changes, not daily.

### If Pause Point Runs Long
- Have people share one pattern they wrote
- Highlight good examples
- Move on, they can finish async
