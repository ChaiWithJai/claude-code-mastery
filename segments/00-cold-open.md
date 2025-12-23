# Segment 0: Cold Open

**Duration**: 5 minutes
**Format**: Live demo, no slides

---

## The Hook

No introduction. No slides. We start coding.

```
"Let me show you something. I'm going to get my daily briefing
with one command."
```

### Live Demo: `/briefing`

Run the `/briefing` command from the Fulcrum plugin:

```bash
cd ~/projects/fulcrum
claude
> /briefing
```

**What happens:**
1. Claude Code loads the briefing command
2. MCP server connects to Google Calendar
3. Agent fetches today's events
4. Agent fetches pending tasks
5. Synthesizes into a morning briefing

**Show the output:**
```markdown
## Morning Briefing - December 22, 2024

### Today's Calendar
- 9:00 AM: Team standup
- 11:00 AM: Design review
- 2:00 PM: 1:1 with Sarah

### Priority Tasks
- [ ] Review PR #234
- [ ] Finish Q4 planning doc
- [ ] Respond to customer escalation

### Suggested Focus
Based on your calendar, you have a 2-hour block from 3-5 PM.
Recommend using this for deep work on the planning doc.
```

---

## The Transformation Reveal

```
"That's not autocomplete. That's not chat.
That's a domain expert that knows my calendar, my tasks, my workflow.

This is the difference between using AI and building with AI."
```

### Show the Transformation

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

---

## The Promise

```
"By the end of this session, you will have:

1. Built your first Claude Code skill
2. A production-ready setup with CLAUDE.md
3. A playbook for rolling this out to your team

Let's start with understanding the architecture."
```

---

## Transition to Segment 1

```
"The first thing you need to understand is that Claude Code
isn't configured with a rules file. It's documented with
architecture. Let me show you what I mean."
```

**[Next: Segment 1 - Architecture Mind Shift →](01-architecture.md)**

---

## Notes for Instructor

### Before This Segment
- Have Fulcrum plugin installed and configured
- Test `/briefing` command works
- Have calendar events for today (real or test)
- Ensure MCP servers are connected

### Key Points to Land
1. This is NOT autocomplete—it's an agent
2. It knows external systems (calendar, tasks)
3. It synthesizes, not just retrieves
4. One command, complex workflow

### If Demo Fails
- Show a recorded trace from LangSmith instead
- Explain what should have happened
- "This is why we cover debugging in Segment 4"
