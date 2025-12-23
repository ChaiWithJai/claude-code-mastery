# Segment 10: Team Adoption Playbook

**Duration**: 30 minutes
**Builds**: Rollout plan for your team

---

## Learning Objectives

By the end of this segment, you will:
1. Know the three rollout options
2. Understand how to identify champions
3. Have a concrete adoption plan for your team

---

## 10.1 The Team Problem

### Sound Familiar?

"We bought licenses. Some people love it. Some tried it once. Most are in between."

This is the adoption gap. Individual enthusiasm doesn't become team capability.

### Why Teams Fail at AI Adoption

1. **No shared vocabulary**: "I use Tab, you use Chat, nobody knows what works"
2. **No expertise encoding**: Knowledge stays in individual heads
3. **No guardrails**: One person's mistake becomes everyone's problem
4. **No measurement**: Can't prove value, can't improve

### The Solution

Systematic rollout with structure, champions, and metrics.

---

## 10.2 Three Rollout Options

### Option A: Self-Directed (Low Touch)

**What it is:**
- Share this course repo
- Point people to relevant skills
- Create a Slack channel for questions

**Good for:**
- Small teams (3-5 people)
- High-autonomy cultures
- Already tech-savvy team

**Timeline:** 2-4 weeks (whenever people get to it)

**Risk:** Uneven adoption, no accountability

### Option B: Cohort-Based (Medium Touch)

**What it is:**
- Form cohorts of 5-8 people
- Assign cohort lead (champion)
- 2-week structured timeline
- Weekly check-ins

**Good for:**
- Medium teams (6-20 people)
- Teams that learn together
- Some dedicated time available

**Timeline:** 2 weeks (structured)

**Risk:** Requires champion commitment

### Option C: Facilitated Workshop (High Touch)

**What it is:**
- Internal champion facilitates live sessions
- 2-day intensive workshop
- Everyone builds together
- Production skill by end of day 2

**Good for:**
- Large teams (20+ people)
- High-stakes adoption
- Budget for dedicated time

**Timeline:** 2 days (intensive)

**Risk:** Expensive in time, needs expert facilitator

---

## 10.3 Identifying Champions

### What Makes a Good Champion?

1. **Already uses Claude Code effectively**
   - Has personal skills
   - Understands the value
   - Can demo real workflows

2. **Enjoys teaching**
   - Patient with questions
   - Explains clearly
   - Celebrates others' wins

3. **Has credibility**
   - Team respects them
   - Technical authority
   - Not seen as "pushing trends"

4. **Willing to commit**
   - Time for facilitation
   - Available for questions
   - Owns the outcome

### Champion Responsibilities

| Task | Frequency | Time |
|------|-----------|------|
| Answer questions in channel | Daily | 15-30 min |
| Run weekly check-in | Weekly | 30 min |
| Review team skills | Weekly | 30 min |
| Report progress to leadership | Weekly | 15 min |
| Escalate blockers | As needed | Varies |

**Total commitment:** ~5 hours/week during rollout

---

## 10.4 The Rollout Timeline

### Week 0: Setup

- [ ] Identify 2-3 champions
- [ ] Create shared skills repo
- [ ] Configure team LangSmith project
- [ ] Set up communication channel (Slack/Teams)
- [ ] Manager kickoff: expectations and support

### Week 1: Foundations

- [ ] Everyone installs Claude Code
- [ ] Everyone creates CLAUDE.md for their project
- [ ] Champions create first team skill
- [ ] Daily tips in channel
- [ ] First check-in meeting

### Week 2: Skills

- [ ] Each team member creates one skill
- [ ] Peer review of skills
- [ ] Add skills to shared repo
- [ ] Troubleshoot common issues
- [ ] Second check-in meeting

### Week 3: Integration

- [ ] Add MCP servers for team tools
- [ ] Create team guardrails skill
- [ ] Start using in real work
- [ ] Track first wins
- [ ] Third check-in meeting

### Week 4: Optimization

- [ ] Review LangSmith traces as team
- [ ] Iterate on skills based on usage
- [ ] Document patterns
- [ ] Celebrate completions
- [ ] Manager review meeting

---

## 10.5 Metrics to Track

### Leading Indicators (Track Weekly)

| Metric | How to Measure | Target |
|--------|----------------|--------|
| Setup complete | Count of users with Claude Code working | 100% by week 1 |
| CLAUDE.md created | Count of projects with CLAUDE.md | 100% by week 1 |
| Skills created | Count of skills in shared repo | 1 per person by week 2 |
| Trace volume | LangSmith project activity | Increasing weekly |

### Lagging Indicators (Track Monthly)

| Metric | How to Measure | Target |
|--------|----------------|--------|
| Usage frequency | Daily active users | 80% of team |
| Skill adoption | Skills used in real work | 3+ per person |
| Time saved | Self-reported estimate | 2+ hours/week/person |
| Quality impact | Code review feedback, bug reduction | Measurable improvement |

### Manager Dashboard

```
TEAM: Engineering (8 people)
─────────────────────────────────────────────────────────
         Setup    CLAUDE.md   Skills    Using Daily
Alice    ✓        ✓           3         ✓
Bob      ✓        ✓           2         ✓
Carol    ✓        ✓           1
David    ✓
Eve      ✓        ✓           4         ✓
Frank    ✓        ✓           2         ✓
Grace    ✓        ✓           2         ✓
Henry
─────────────────────────────────────────────────────────
COMPLETION: 6/8 (75%)   AT RISK: David, Henry
```

---

## 10.6 Handling Resistance

### Common Objections

| Objection | Response |
|-----------|----------|
| "I don't have time" | "This saves time. 2 hours of learning saves 4+ hours/week." |
| "My workflow is fine" | "Let's measure. Track your time for a week, then compare." |
| "AI makes mistakes" | "So do humans. Guardrails + review = safer than manual." |
| "I'll learn later" | "The team is learning now. You'll be behind in 2 weeks." |
| "It's just hype" | "Show them your traces. Evidence beats opinion." |

### Resistance Patterns

**The Skeptic**: Wants proof before trying
- Solution: Show traces, show metrics, invite to observe

**The Busy**: Claims no time
- Solution: Start with one skill, 30 min investment

**The Expert**: "I don't need AI"
- Solution: Challenge them to encode their expertise

**The Anxious**: Worried about job security
- Solution: Frame as augmentation, show how it makes them more valuable

---

## 10.7 Your Rollout Plan

### Fill In Your Plan

**Team Size:** _____ people

**Rollout Option:** A / B / C

**Champions:**
1. _____
2. _____

**Timeline:**
- Week 0 (Setup): _____
- Week 1 (Foundations): _____
- Week 2 (Skills): _____
- Week 3 (Integration): _____
- Week 4 (Optimization): _____

**First Team Skill to Create:** _____

**Success Metric:** _____

**Biggest Risk:** _____

**Mitigation:** _____

---

## 10.8 Resources

### For Champions

- [Full course repo](https://github.com/ChaiWithJai/claude-code-mastery)
- [FOR-TEAMS.md](../FOR-TEAMS.md) - Detailed team guide
- [Mastery Rubric](../assessments/mastery-rubric.md) - Track progress

### For Managers

- Weekly status template (in FOR-TEAMS.md)
- ROI calculation guide
- Executive summary template

### For Team Members

- [SETUP.md](../SETUP.md) - Getting started
- [Segments](../segments/) - Self-paced learning
- [Examples](../examples/) - Reference implementations

---

## Key Takeaways

1. **Individual adoption ≠ team adoption**—need structure
2. **Champions are critical**—identify and support them
3. **Measure to prove value**—traces and metrics
4. **Handle resistance with evidence**—not arguments
5. **4 weeks to establish habits**—then it compounds

---

## What's Next?

### For You
- Complete any exercises you missed
- Build your domain expertise skill
- Start using Claude Code in real work

### For Your Team
- Share this course
- Identify champions
- Start week 0 this week

### For Your Career
- Track your Claude Code skills on LinkedIn
- Share wins with your network
- Consider contributing back to this course

---

**[Course Complete! →](../COMPLETION.md)**

---

## Notes for Instructor

### Key Points to Land
1. This is where the business value is—team adoption
2. Champions make or break rollout
3. Metrics prove value (to skeptics and managers)

### Live Exercise
- Have people fill in their rollout plan
- Share one plan with the group
- Discuss adaptations for different team sizes

### Closing Strong
- Thank everyone for attending
- Point to next steps
- Share contact info for questions
- Ask for repo stars and shares
