# Segment 9: Production Setup Checklist

**Duration**: 10 minutes
**Builds**: Verified, complete Claude Code setup

---

## Learning Objectives

By the end of this segment, you will:
1. Have a complete, verified Claude Code setup
2. Know what "production ready" looks like
3. Have a checklist for maintaining your setup

---

## 9.1 The Complete Setup

### Directory Structure

```
~/.claude/                          # User-level (personal)
├── settings.json                   # Claude Code settings
├── skills/                         # Personal skills
│   ├── code-review-preferences/
│   │   └── SKILL.md
│   ├── my-framework/
│   │   └── SKILL.md
│   └── git-workflow-guardrails/
│       └── SKILL.md
├── agents/                         # Personal agents
└── commands/                       # Personal commands

~/projects/my-project/              # Project-level
├── CLAUDE.md                       # Architecture documentation
├── .claude-plugin/                 # Plugin (if sharing with team)
│   └── plugin.json
├── .mcp.json                       # MCP server config
├── skills/                         # Project-specific skills
├── agents/                         # Project-specific agents
└── commands/                       # Project-specific commands
```

---

## 9.2 Verification Checklist

### Core Setup

```bash
# 1. Claude Code installed
claude --version
# Expected: claude-code version X.X.X

# 2. Authenticated
claude auth status
# Expected: Authenticated as user@email.com

# 3. CLAUDE.md exists
cat ~/projects/my-project/CLAUDE.md
# Expected: Your architecture documentation
```

### Skills

```bash
# 4. Skills directory exists
ls ~/.claude/skills/
# Expected: Your skill directories

# 5. Skills are recognized
claude
> /skills
# Expected: Your skills listed

# 6. Skill triggers correctly
> Review this code
# Expected: Your code-review skill activates
```

### Telemetry

```bash
# 7. LangSmith configured
echo $LANGSMITH_API_KEY
# Expected: lsv2_pt_...

echo $LANGSMITH_PROJECT
# Expected: your-project-name

# 8. Traces appearing
# Go to smith.langchain.com
# Check your project for recent traces
```

### MCP (If Configured)

```bash
# 9. MCP config exists
cat .mcp.json
# Expected: Your MCP server configuration

# 10. MCP servers connect
claude
> What's on my calendar today?
# Expected: Real calendar data (if calendar MCP configured)
```

---

## 9.3 Production Readiness

### Minimum Viable Setup

| Component | Status | Required? |
|-----------|--------|-----------|
| Claude Code installed | | Yes |
| Authenticated | | Yes |
| CLAUDE.md for main project | | Yes |
| At least 1 custom skill | | Yes |
| LangSmith tracing | | Recommended |
| Git guardrails | | Recommended |
| MCP integration | | Optional |

### What "Production Ready" Means

1. **Documented**: CLAUDE.md describes your architecture
2. **Customized**: Skills encode your expertise
3. **Safe**: Guardrails prevent mistakes
4. **Observable**: Traces show what's happening
5. **Integrated**: MCP connects to your tools (optional)

---

## 9.4 Quick Fixes

### Common Issues

| Issue | Symptom | Fix |
|-------|---------|-----|
| Skills not loading | `/skills` shows nothing | Check `~/.claude/skills/` directory structure |
| CLAUDE.md ignored | Claude doesn't know project | Ensure file is at project root |
| Traces not appearing | Nothing in LangSmith | Check env vars, restart claude |
| MCP failing | "Server not found" | Check .mcp.json syntax, server installed |
| Commands not working | `/mycommand` not recognized | Check commands/ directory, filename matches |

### Debug Commands

```bash
# Check what Claude sees
claude
> What skills do you have?
> What's in my CLAUDE.md?
> What MCP servers are available?
```

---

## 9.5 Maintenance Checklist

### Weekly

- [ ] Check LangSmith for failed traces
- [ ] Review any new patterns worth encoding
- [ ] Update CLAUDE.md if architecture changed

### Monthly

- [ ] Audit skills—remove unused, update outdated
- [ ] Review guardrails—still relevant?
- [ ] Check MCP connections—still working?
- [ ] Update Claude Code if new version available

### Quarterly

- [ ] Full setup verification (run checklist above)
- [ ] Skill quality review—are they effective?
- [ ] Team sync—share useful skills/patterns
- [ ] LangSmith analysis—identify improvement areas

---

## 9.6 Your Setup Status

### Fill in your status:

| Component | Your Status |
|-----------|-------------|
| Claude Code version | v_____ |
| CLAUDE.md location | _____ |
| Number of skills | _____ |
| Guardrails active | Yes / No |
| LangSmith configured | Yes / No |
| MCP servers | _____ |

### Gaps to Address

List anything missing:
1. _____
2. _____
3. _____

---

## Key Takeaways

1. **Complete setup has 5 components**: Claude, CLAUDE.md, skills, telemetry, guardrails
2. **Verify with checklist**—don't assume things work
3. **Maintain regularly**—setups drift without attention
4. **Debug systematically**—most issues are configuration

---

**[Next: Segment 10 - Team Adoption Playbook →](10-team-adoption.md)**

---

## Notes for Instructor

### Key Points to Land
1. Run through the checklist live
2. Show what "good" looks like at each step
3. Address common issues they'll hit

### Time Management
- This is a verification segment, not a building segment
- Go fast through items that are working
- Pause on common failure points

### If Someone Is Behind
- Point them to specific fix
- They can catch up during team adoption segment
- Share the checklist so they can verify later
