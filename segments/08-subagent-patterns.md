# Segment 8: Subagent Patterns

**Duration**: 15 minutes
**Builds**: Understanding of specialist delegation

---

## Learning Objectives

By the end of this segment, you will:
1. Know when to use subagents vs. single agent
2. Understand context isolation benefits
3. See real subagent patterns from production

---

## 8.1 Why Subagents?

### The Problem with One Agent

```
Main Agent Context:
├── CLAUDE.md (500 tokens)
├── Skill 1 (300 tokens)
├── Skill 2 (400 tokens)
├── Skill 3 (350 tokens)
├── Conversation history (2000 tokens)
├── Current task context (1000 tokens)
└── Total: 4,550 tokens
```

As context grows:
- Response quality decreases
- Irrelevant information interferes
- Costs increase
- Latency increases

### The Subagent Solution

```
Main Agent:
├── Coordination logic
├── Routing decisions
└── Final synthesis

Subagent 1 (Specialist A):
├── Focused context
├── Deep expertise in A
└── Returns structured output

Subagent 2 (Specialist B):
├── Different context
├── Deep expertise in B
└── Returns structured output
```

Each specialist works with clean, focused context.

---

## 8.2 When to Use Subagents

### Use Subagents When:

**1. Context Isolation Needed**
- Different domains shouldn't pollute each other
- Security review shouldn't see marketing context
- Legal review has different principles than code review

**2. Parallel Analysis**
- Multiple perspectives needed simultaneously
- Each perspective requires different expertise
- Results need to be synthesized

**3. Deep Specialization**
- Specialist needs 500+ lines of prompts
- Main agent would be overwhelmed
- Quality matters more than speed

**4. Tool Access Scoping**
- Specialist needs dangerous tools
- Main agent shouldn't have access
- Principle of least privilege

### Don't Use Subagents When:

- Task is simple (single domain)
- Speed is critical (subagents add latency)
- Context is already small
- You're over-engineering

---

## 8.3 Real Example: PMM Agent

### The Architecture

```
PMM Main Agent
│
├── Tool: analyze_homepage
│   └── Calls: homepage-analyst subagent
│
├── Tool: evaluate_positioning
│   └── Calls: positioning-analyst subagent
│
├── Tool: detect_anti_patterns
│   └── Calls: anti-pattern-detector subagent
│
└── Tool: synthesize_report
    └── Uses outputs from all subagents
```

### The Subagents

```python
SUBAGENTS = {
    "positioning-analyst": {
        "description": "Deep positioning analysis using April Dunford methodology",
        "system_prompt": POSITIONING_SPECIALIST_PROMPT,  # 400 lines
        "tools": ["web_fetch", "extract_claims"]
    },
    "homepage-analyst": {
        "description": "Homepage teardown and conversion analysis",
        "system_prompt": HOMEPAGE_SPECIALIST_PROMPT,  # 350 lines
        "tools": ["screenshot", "extract_text", "analyze_layout"]
    },
    "anti-pattern-detector": {
        "description": "Identify common PMM mistakes",
        "system_prompt": ANTI_PATTERN_PROMPT,  # 250 lines
        "tools": ["pattern_match"]
    }
}
```

### Why It Works

Each specialist:
- Has deep, focused expertise (their system prompt)
- Gets clean context (no pollution from other domains)
- Returns structured output (main agent synthesizes)

---

## 8.4 The Subagent Pattern

### Definition

```python
subagent = {
    "name": "specialist-name",
    "description": "When to use this specialist",
    "system_prompt": """
        [100-500 lines of domain expertise]

        You are a specialist in [domain].

        Your job is to:
        1. [Specific task 1]
        2. [Specific task 2]
        3. [Specific task 3]

        Return your analysis in this format:
        {
            "findings": [...],
            "confidence": 0.0-1.0,
            "recommendations": [...]
        }
    """,
    "tools": [tool1, tool2],
    "return_schema": OutputSchema
}
```

### Invocation

```python
# From main agent
result = await invoke_subagent(
    name="positioning-analyst",
    input={
        "company_url": "https://example.com",
        "context": "B2B SaaS"
    }
)

# Use result in main agent
positioning_score = result["confidence"]
findings = result["findings"]
```

---

## 8.5 Human-in-the-Loop

### The Risk

Subagents can take actions. Some actions are dangerous:
- Creating public content
- Sending emails
- Modifying production data
- Making financial decisions

### The Solution: Interrupts

```python
# Configure interrupts
interrupt_on = {
    "create_positioning_canvas": True,  # Always ask
    "publish_to_blog": True,            # Always ask
    "send_email": True,                 # Always ask
}

# In execution
if action in interrupt_on:
    approval = await request_human_approval(
        action=action,
        context=context,
        risk_level="high"
    )
    if not approval:
        return {"status": "cancelled", "reason": "User declined"}
```

### User Experience

```
Claude: I've analyzed the positioning and prepared a canvas.

        Before I create the final document, please review:

        [Preview of canvas]

        Proceed? [Yes] [No] [Edit first]
```

---

## 8.6 When You'll Need This

### Now (After This Course)
- You probably don't need subagents yet
- Single skills and agents are sufficient
- Focus on encoding expertise first

### Later (When Complexity Grows)
- You have 10+ skills competing for context
- You need parallel specialist analysis
- Quality in specific domains is suffering
- You're building production agent systems

### Signs You Need Subagents
1. Responses are getting worse as you add more skills
2. You need contradictory principles for different tasks
3. You want specialists who don't see each other's context
4. You're building a product, not personal tooling

---

## Key Takeaways

1. **Subagents isolate context**—specialists focus on their domain
2. **Use for deep specialization**—when you need 500+ lines of prompts
3. **Human-in-the-loop for risky actions**—require approval
4. **Don't over-engineer**—start simple, add complexity when needed
5. **This is advanced**—most users don't need it yet

---

**[Next: Segment 9 - Production Setup Checklist →](09-production-checklist.md)**

---

## Notes for Instructor

### Key Points to Land
1. Subagents are for ISOLATION, not just organization
2. Most people don't need them yet
3. When you do need them, you'll know

### Show, Don't Build
- Show the PMM agent architecture
- Show a trace of subagent invocation
- Don't live-code subagents (too complex for this format)

### Common Questions
- "Should I use subagents?" → Probably not yet
- "How do I know when I need them?" → Context pollution symptoms
- "Is this like microservices?" → Similar concept, different implementation
