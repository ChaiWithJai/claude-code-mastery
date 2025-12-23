# Claude Code Mastery Rubric

Self-assessment to verify your understanding and capabilities.

---

## How to Use This Rubric

Rate yourself on each dimension:
- **0 - Not Started**: Haven't attempted this yet
- **1 - Awareness**: Understand the concept, haven't done it
- **2 - Attempted**: Tried it, still learning
- **3 - Competent**: Can do it with reference materials
- **4 - Proficient**: Can do it confidently
- **5 - Mastery**: Can teach others, handle edge cases

**Passing Score**: Average of 3.0 or higher

---

## Dimension 1: Architecture Understanding

| Skill | 0 | 1 | 2 | 3 | 4 | 5 |
|-------|---|---|---|---|---|---|
| Explain what CLAUDE.md is for | | | | | | |
| Describe progressive disclosure (L1/L2/L3) | | | | | | |
| Distinguish skill vs agent vs command | | | | | | |
| Explain when to use skill vs raw prompt | | | | | | |
| Describe how MCP servers work | | | | | | |

**Subtotal**: ___ / 25

### Self-Check Questions

1. A colleague asks "What's CLAUDE.md?" How do you answer in one sentence?
2. When does L2 content get loaded? When does L3?
3. You need to encode team coding standards. Skill or agent? Why?

---

## Dimension 2: Skill Development

| Skill | 0 | 1 | 2 | 3 | 4 | 5 |
|-------|---|---|---|---|---|---|
| Write SKILL.md frontmatter | | | | | | |
| Create essential_principles section | | | | | | |
| Design intake questions | | | | | | |
| Build routing table | | | | | | |
| Use references for L3 content | | | | | | |

**Subtotal**: ___ / 25

### Self-Check Questions

1. Write the frontmatter for a skill that helps with database migrations.
2. Why is the intake section important?
3. Your skill is 2000 words. What should you move to references?

---

## Dimension 3: Plugin Structure

| Skill | 0 | 1 | 2 | 3 | 4 | 5 |
|-------|---|---|---|---|---|---|
| Create plugin.json manifest | | | | | | |
| Organize agents/ directory | | | | | | |
| Create namespaced commands | | | | | | |
| Configure .mcp.json | | | | | | |
| Write setup.sh for dependencies | | | | | | |

**Subtotal**: ___ / 25

### Self-Check Questions

1. What's the difference between a skill in ~/.claude/skills and one in a plugin?
2. How do you namespace commands to avoid conflicts?
3. Your MCP server needs an API key. Where does it go?

---

## Dimension 4: Domain Expertise Encoding

| Skill | 0 | 1 | 2 | 3 | 4 | 5 |
|-------|---|---|---|---|---|---|
| Identify what to encode | | | | | | |
| Extract principles from experience | | | | | | |
| Write anti-patterns section | | | | | | |
| Create framework overview | | | | | | |
| Design checklist patterns | | | | | | |

**Subtotal**: ___ / 25

### Self-Check Questions

1. What framework/methodology do you use daily that isn't captured in AI tools?
2. What's the most common mistake juniors make in your domain?
3. Write 3 principles for your area of expertise in imperative form.

---

## Dimension 5: Observability & Debugging

| Skill | 0 | 1 | 2 | 3 | 4 | 5 |
|-------|---|---|---|---|---|---|
| Configure LangSmith tracing | | | | | | |
| Read trace output | | | | | | |
| Identify skill activation in traces | | | | | | |
| Debug why skill didn't trigger | | | | | | |
| Optimize based on token counts | | | | | | |

**Subtotal**: ___ / 25

### Self-Check Questions

1. Your skill isn't triggering. What do you check first?
2. A trace shows 5000 tokens for L2 load. Problem?
3. How do you know if your skill's principles were actually used?

---

## Dimension 6: Safety & Guardrails

| Skill | 0 | 1 | 2 | 3 | 4 | 5 |
|-------|---|---|---|---|---|---|
| Identify dangerous operations for your team | | | | | | |
| Write NEVER/ALWAYS patterns | | | | | | |
| Create confirmation workflows | | | | | | |
| Design human-in-the-loop checkpoints | | | | | | |
| Document recovery procedures | | | | | | |

**Subtotal**: ___ / 25

### Self-Check Questions

1. What git operations should never be automated on your team?
2. Write a NEVER statement for your most risky operation.
3. When should Claude stop and ask before proceeding?

---

## Dimension 7: Team Adoption

| Skill | 0 | 1 | 2 | 3 | 4 | 5 |
|-------|---|---|---|---|---|---|
| Explain value to skeptical colleague | | | | | | |
| Set up shared skills repository | | | | | | |
| Create skill contribution guidelines | | | | | | |
| Train a new engineer on skills | | | | | | |
| Measure adoption success | | | | | | |

**Subtotal**: ___ / 25

### Self-Check Questions

1. Colleague says "I can just use prompts." What's your response?
2. What's in CONTRIBUTING.md for a skills repo?
3. What metrics show skills are actually being used?

---

## Scoring Summary

| Dimension | Score | Max |
|-----------|-------|-----|
| 1. Architecture Understanding | | 25 |
| 2. Skill Development | | 25 |
| 3. Plugin Structure | | 25 |
| 4. Domain Expertise Encoding | | 25 |
| 5. Observability & Debugging | | 25 |
| 6. Safety & Guardrails | | 25 |
| 7. Team Adoption | | 25 |
| **Total** | | **175** |
| **Average** (Total ÷ 35) | | **5.0** |

---

## Interpretation

| Average | Level | Next Step |
|---------|-------|-----------|
| 0-1.0 | Beginner | Rewatch segments, complete all exercises |
| 1.1-2.0 | Developing | Focus on hands-on practice |
| 2.1-3.0 | Competent | Build more skills, help teammates |
| 3.1-4.0 | Proficient | Contribute to community, teach others |
| 4.1-5.0 | Master | Create advanced patterns, mentor teams |

---

## Practical Verification

Beyond self-assessment, verify with evidence:

### Minimum Viable Completion
- [ ] CLAUDE.md exists in main project
- [ ] At least 1 skill with working SKILL.md
- [ ] Skill triggers correctly on intended input
- [ ] Can read LangSmith trace for that skill

### Recommended Completion
- [ ] 3+ skills covering different workflows
- [ ] 1 domain expertise skill with original principles
- [ ] Guardrails skill for risky operations
- [ ] LangSmith project with meaningful traces

### Full Mastery
- [ ] Plugin with skills + agents + commands
- [ ] Shared skills repository for team
- [ ] Documented patterns for others to follow
- [ ] Trained at least 1 other person

---

## Skill Gap Analysis

For dimensions scoring below 3:

| Dimension | Recommended Action |
|-----------|--------------------|
| 1. Architecture | Rewatch Segment 01, redo Exercise 1 |
| 2. Skill Development | Rewatch Segment 02, study example skills |
| 3. Plugin Structure | Rewatch Segment 03, study minimal-plugin |
| 4. Domain Expertise | Rewatch Segment 07, redo Exercise 5 |
| 5. Observability | Rewatch Segment 05, set up LangSmith |
| 6. Safety | Rewatch Segment 06, redo Exercise 4 |
| 7. Team Adoption | Read FOR-TEAMS.md, practice explaining |

---

## Reassessment

Schedule reassessment:
- **Initial**: After completing all exercises
- **Week 2**: After daily use for one week
- **Month 1**: After building 3+ skills
- **Month 3**: After team adoption (if applicable)

Track your growth over time.
