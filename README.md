# Claude Code Mastery

**Go from "AI autocomplete user" to "AI agent architect" in one livestream.**

---

## The Problem

You use Cursor. Or Copilot. Or both. You've gotten faster at writing code.

But you're still just using autocomplete with extra steps.

- Your `.cursorrules` file is ignored half the time
- Context resets every session
- You're prompting, not architecting
- AI helps you code, but doesn't know YOUR stack

**You're using AI. You're not building with AI.**

This course fixes that.

---

## The Transformation

```
CURSOR/COPILOT                         CLAUDE CODE
───────────────────────────────────────────────────────────────────
Single-file autocomplete          →   Multi-file agents with memory
"Chat in sidebar"                 →   Skills that encode YOUR expertise
.cursorrules (ignored)            →   CLAUDE.md (sacred architecture)
Generic AI assistant              →   Domain expert that knows your stack
Every session starts fresh        →   Compound knowledge across sessions
───────────────────────────────────────────────────────────────────
```

**Duration**: 3.5 hour livestream (built in public)
**Outcome**: Your first Claude Code skill shipped, production setup complete

---

## What You'll Build

| Segment | You'll Ship | Time |
|---------|-------------|------|
| [0. Cold Open](segments/00-cold-open.md) | See a working agent demo | 5 min |
| [1. Architecture](segments/01-architecture.md) | CLAUDE.md for your project | 20 min |
| [2. First Skill](segments/02-first-skill.md) | Complete skill with SKILL.md | 40 min |
| [3. Plugin Architecture](segments/03-plugin-architecture.md) | Agent + command | 35 min |
| [4. MCP Integration](segments/04-mcp-integration.md) | External API connection | 25 min |
| **Break** | Catch up | 10 min |
| [5. Telemetry](segments/05-langsmith-telemetry.md) | LangSmith tracing | 20 min |
| [6. Guardrails](segments/06-git-guardrails.md) | Safety constraints | 15 min |
| [7. Domain Expertise](segments/07-domain-expertise.md) | Your framework as a skill | 25 min |
| [8. Subagents](segments/08-subagent-patterns.md) | Specialist delegation | 15 min |
| [9. Production Setup](segments/09-production-checklist.md) | Complete, verified setup | 10 min |
| [10. Team Adoption](segments/10-team-adoption.md) | Rollout playbook | 30 min |

Every segment ends with something you built yourself.

---

## Who This Is For

**This course is for you if:**

- [ ] You use Cursor, Copilot, or similar AI coding tools
- [ ] You want to go beyond autocomplete to building agents
- [ ] You have domain expertise worth encoding (frameworks, patterns, processes)
- [ ] You want your team to adopt AI-assisted development systematically

**This course is NOT for you if:**

- You've never used AI coding tools (start with basics first)
- You just want faster autocomplete (Cursor is fine for that)
- You don't have a specific domain or codebase to apply this to

---

## Why This Works

### 1. Live Build, Not Lecture
I build everything live during the stream. You follow along. No slides-only segments.

### 2. Real Patterns from Production
Every pattern comes from my actual Claude Code setup: 17 custom skills, multiple plugins, LangSmith traces showing real workflows.

### 3. Encode YOUR Expertise
By the end, you've encoded your own framework/process as a Claude Code skill. Not a toy example—your actual workflow.

### 4. Team-Ready
The final segment is a complete team adoption playbook. This isn't just personal productivity—it's how you roll out to your org.

---

## The Evidence

This course uses exported LangSmith traces to show exactly how Claude Code works:

| Trace | What It Shows |
|-------|---------------|
| [Skill Activation](traces/) | How skills load and route |
| [Agent Workflow](traces/) | Multi-step agent execution |
| [MCP Integration](traces/) | External API calls |
| [Subagent Delegation](traces/) | Specialist handoff |

Not conceptual diagrams. Actual traces from production use.

---

## Quick Start

### Before the Livestream

```bash
# 1. Install Claude Code
# Follow: https://claude.ai/code

# 2. Clone this repo
git clone https://github.com/ChaiWithJai/claude-code-mastery.git
cd claude-code-mastery

# 3. Complete pre-setup
cat SETUP.md
```

### During the Livestream

Follow along with each segment. At pause points, build your own version.

### After the Livestream

Complete any exercises you missed. Use the reference guides for lookup.

---

## What Success Looks Like

### By End of Livestream
- [ ] CLAUDE.md documenting your project architecture
- [ ] One working skill with SKILL.md
- [ ] One command added to your skill
- [ ] One domain expertise skill draft
- [ ] Team adoption plan outline

### Within 30 Days
- [ ] Full production setup verified
- [ ] LangSmith tracing active
- [ ] At least 3 custom skills in daily use
- [ ] Team rollout initiated

### Within 90 Days
- [ ] Your team uses Claude Code systematically
- [ ] Custom skills for your domain
- [ ] Measurable productivity gains

**[Self-Assessment Rubric →](assessments/mastery-rubric.md)**

---

## For Teams

**Want to upskill your entire engineering team?**

This course works for:
- **Platform teams** building internal developer tools
- **Engineering orgs** standardizing on AI-assisted development
- **Startups** wanting to maximize developer leverage
- **Agencies** building AI-powered workflows for clients

**[Team Adoption Guide →](FOR-TEAMS.md)**

---

## Repository Structure

```
claude-code-mastery/
├── segments/                 # Livestream content (11 segments)
├── exercises/                # Pause point exercises (5 folders)
├── examples/                 # Reference implementations
│   ├── skills/              # 3 example skills
│   ├── agents/              # Agent patterns
│   ├── commands/            # Command patterns
│   └── plugins/             # Minimal plugin example
├── traces/                   # LangSmith exports
├── references/               # Quick reference guides
├── assessments/              # Self-evaluation rubric
├── FOR-TEAMS.md              # Team adoption playbook
└── COMPLETION.md             # Certificate + LinkedIn templates
```

---

## The Philosophy

### "The Soul Lives in Prompts"

Claude Code isn't about better autocomplete. It's about encoding your expertise.

Your system prompts should be 100-500 lines of domain knowledge. Your skills should make Claude an expert in YOUR stack. Your agents should know YOUR workflows.

Generic AI assistants are commodities. Domain experts are valuable.

### CLAUDE.md is Sacred

`.cursorrules` is a suggestion. `CLAUDE.md` is architecture documentation.

When you write a CLAUDE.md, you're not configuring an AI tool. You're documenting your system for any intelligent reader—human or AI.

### Skills Compound

Every session with Cursor starts fresh. Every skill in Claude Code compounds.

Build once, use forever. Your expertise becomes infrastructure.

---

## FAQ

**How is this different from Cursor/Copilot?**

Cursor/Copilot are autocomplete tools. Claude Code is an agent platform. You can build skills, agents, commands, and integrations that persist across sessions and encode your domain expertise.

**Do I need to uninstall Cursor?**

No. Many developers use both. Claude Code for architecture and agents, Cursor for in-file editing. They complement each other.

**What if I can't attend live?**

The repo contains everything. Watch the recording, work through segments at your own pace, use exercises for practice.

**Is this for beginners?**

No. This assumes you already use AI coding tools and want to go deeper. If you've never used Cursor/Copilot, start there first.

---

## Ready?

The gap between "AI user" and "AI architect" is smaller than you think.

**[Start with Setup →](SETUP.md)**

---

## Work With Me

**For individuals**: This free course covers the full livestream content. If you want personalized coaching on encoding your specific domain expertise, **[reach out](https://linkedin.com/in/jaikbhagat)**.

**For teams**: Team packages include custom skill development for your codebase, live workshops, and adoption tracking. **[Contact for team pricing](mailto:jai@chaiwithjai.com?subject=Claude%20Code%20Mastery%20-%20Team)**.

---

<p align="center">
<strong>Built by <a href="https://linkedin.com/in/jaikbhagat">Jai Bhagat</a></strong><br>
<em>Product Manager • AI Learning Design • 17 Custom Claude Code Skills</em>
</p>

<p align="center">
<a href="https://github.com/ChaiWithJai/claude-code-mastery/stargazers">Star this repo</a> if you ship your first skill.
</p>
