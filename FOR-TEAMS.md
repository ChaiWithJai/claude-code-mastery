# Claude Code for Teams

Team adoption guide for engineering leaders.

---

## Why Teams Adopt Claude Code

| Before | After |
|--------|-------|
| Each engineer learns AI coding solo | Shared skills encode team best practices |
| Knowledge leaves when people leave | Expertise compounds in skills repository |
| Inconsistent AI outputs | Standardized outputs matching team patterns |
| "It worked on my machine" | Reproducible, debuggable workflows |
| No visibility into AI usage | LangSmith traces for learning and debugging |

---

## Three Rollout Options

### Option A: Self-Directed (Small Teams, <5 engineers)

**Investment**: 3.5 hours (livestream or async)

**Process**:
1. Each engineer completes the course independently
2. Slack channel for questions
3. Weekly skill-sharing session (30 min)

**Artifacts Produced**:
- [ ] Each engineer has CLAUDE.md in their main project
- [ ] At least 1 shared skill per engineer
- [ ] Team skills repository established

**When to Choose**: Team already experiments with AI tools. Self-motivated learners.

---

### Option B: Cohort-Based (Medium Teams, 5-15 engineers)

**Investment**: 3.5 hours together + 2 weeks practice

**Process**:

**Week 0: Livestream Session**
- Entire team watches together
- Builds skills in real-time during pause points
- Immediate shared context

**Weeks 1-2: Practice Period**
| Day | Activity |
|-----|----------|
| 1-3 | Complete exercises 1-3 |
| 4-5 | Build one domain expertise skill |
| 6-7 | Peer review skills |
| 8-10 | Iterate based on feedback |
| 11-14 | Real workflow integration |

**Artifacts Produced**:
- [ ] Team CLAUDE.md template
- [ ] 3-5 shared domain expertise skills
- [ ] Internal skills repository (git repo)
- [ ] Best practices documented

**When to Choose**: Team has dedicated learning time. Coordination is possible.

---

### Option C: Facilitated (Large Teams or Orgs, 15+ engineers)

**Investment**: Custom engagement

**Process**:
1. **Discovery Call** - Understand team patterns, tech stack, workflows
2. **Custom Skills Design** - Pre-built skills for your domain
3. **Livestream + Workshop** - 3.5 hour session + 1 hour team workshop
4. **Office Hours** - 2x 1-hour sessions for Q&A
5. **Skills Repository Setup** - Turnkey shared skills repo

**Artifacts Produced**:
- [ ] Custom skills matching team patterns
- [ ] Skills repository with CI/CD
- [ ] Onboarding documentation
- [ ] Champions trained (2-3 per team)

**When to Choose**: Need faster time-to-value. Complex workflows. Multiple teams.

**Contact**: [jai@pm-ai-lab.com](mailto:jai@pm-ai-lab.com)

---

## Team Skills Repository

### Structure

```
team-claude-skills/
├── README.md                     # What's in this repo
├── CONTRIBUTING.md               # How to add skills
│
├── code-review/                  # Team code review standards
│   └── SKILL.md
├── pr-standards/                 # PR description format
│   └── SKILL.md
├── architecture-decisions/       # ADR format + principles
│   └── SKILL.md
├── [your-framework]/             # Domain expertise (React, Rails, etc.)
│   └── SKILL.md
└── [your-workflow]/              # Team-specific workflows
    └── SKILL.md
```

### Contribution Flow

```
Engineer writes skill → PR → Team review → Merge → All engineers benefit
```

### Skill Quality Criteria

Before merging, verify:
- [ ] Frontmatter has clear, specific description
- [ ] Essential principles are < 500 words
- [ ] Intake questions prevent ambiguity
- [ ] Examples show expected behavior
- [ ] Tested against 3+ real scenarios

---

## Champions Program

### Who Should Be Champions

- Early adopters already using Claude Code
- Engineers who enjoy teaching
- Those with broad codebase knowledge

### Champion Responsibilities

| Weekly | Monthly |
|--------|---------|
| Answer skill questions | Curate best skills |
| Review skill PRs | Host skill-sharing session |
| Share their workflows | Onboard new engineers |

### Recognizing Champions

- LinkedIn recommendation from leadership
- Internal "Claude Code Champion" badge
- Priority access to new features/updates

---

## Metrics to Track

### Leading Indicators (Week 1-4)

| Metric | Target | How to Measure |
|--------|--------|----------------|
| Completion rate | >80% | Who finished all exercises |
| Skills created | 1 per engineer | Count in skills repo |
| CLAUDE.md adoption | 100% | Check main projects |

### Lagging Indicators (Month 1-3)

| Metric | Target | How to Measure |
|--------|--------|----------------|
| Skill reuse rate | 3+ uses per skill | LangSmith traces |
| Time to first PR | -20% | Git metrics |
| Code review cycles | -1 round | PR analytics |
| Engineer satisfaction | +NPS | Survey |

---

## Common Objections

### "We already use Copilot/Cursor"

Claude Code isn't replacing your IDE AI. It's adding:
- Encoded team expertise (skills)
- Multi-file awareness (agents)
- External tool integration (MCP)
- Debugging visibility (LangSmith)

Many teams use both.

### "This is too much process"

Start with one skill. See the compounding effect. Add more only when you see value.

Minimum viable adoption:
1. One shared CLAUDE.md template
2. One domain expertise skill
3. Weekly 15-min skill share

### "Our engineers will figure it out themselves"

They will learn to use Claude Code. They won't naturally:
- Encode team-specific patterns
- Build reusable skills
- Create observability
- Establish guardrails

The course accelerates the team benefit, not just individual productivity.

### "We can't block 3.5 hours"

Options:
- Watch at 1.5x speed (2h 20m)
- Split across two sessions
- Assign async with Slack sync points

---

## ROI Calculation

### Conservative Estimates

| Factor | Estimate |
|--------|----------|
| Engineer time saved | 30 min/day |
| Working days/month | 20 |
| Monthly hours saved per engineer | 10 hours |
| Fully-loaded hourly rate | $100 |
| Monthly savings per engineer | $1,000 |

### For a 10-person team:
- **Monthly savings**: $10,000
- **Annual savings**: $120,000
- **Course investment**: 3.5 hours × 10 = 35 hours × $100 = $3,500
- **ROI**: 34x in year one

### Harder to Quantify

- Knowledge retention when engineers leave
- Faster onboarding for new engineers
- Reduced context-switching
- Better code review quality

---

## Getting Started

### Option A (Self-Directed)

1. Share course link with team
2. Create #claude-code Slack channel
3. Set deadline (2 weeks recommended)
4. Schedule weekly skill-share

### Option B (Cohort-Based)

1. Schedule 4-hour block for team
2. Send setup instructions 3 days before
3. Watch together, pause for exercises
4. Assign 2-week practice period
5. Review progress at end

### Option C (Facilitated)

Email [jai@pm-ai-lab.com](mailto:jai@pm-ai-lab.com) with:
- Team size
- Primary tech stack
- Current AI tool usage
- Specific pain points

---

## Ready to Start?

1. **Watch the Livestream**: [Link to recording]
2. **Complete the Exercises**: 5 pause points, 21 minutes total
3. **Build Your First Skill**: Use the domain expertise template
4. **Share with Team**: Fork the skills repo, start contributing

Questions? [jai@pm-ai-lab.com](mailto:jai@pm-ai-lab.com)
