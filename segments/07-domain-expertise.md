# Segment 7: Domain Expertise Encoding

**Duration**: 25 minutes
**Builds**: Your framework/process as a Claude Code skill

---

## Learning Objectives

By the end of this segment, you will:
1. Understand how to encode repeatable processes as skills
2. Know the framework encoding pattern
3. Build a domain expertise skill for YOUR workflow

---

## 7.1 The Philosophy

### You Have Expertise

Things you do repeatedly:
- A decision framework you apply
- A checklist you follow
- A process you've refined
- Questions you always ask

**This expertise is valuable.** It's why you're good at your job.

### Claude Doesn't Have Your Expertise

Generic Claude knows general things. It doesn't know:
- Your team's coding standards
- Your company's positioning framework
- Your deployment checklist
- Your interview methodology

### The Solution: Encode It

Turn your expertise into a skill. Claude becomes an expert in YOUR domain.

---

## 7.2 The Framework Encoding Pattern

### Structure

```markdown
<framework_overview>
What is this framework?
When should it be used?
What are the key components?
</framework_overview>

<principles>
The core beliefs that drive the framework.
These are ALWAYS true when using this approach.
</principles>

<process>
Step-by-step methodology.
How do you actually apply this?
</process>

<templates>
Output formats.
What should the deliverable look like?
</templates>

<examples>
Good and bad examples.
What does success look like?
</examples>

<anti-patterns>
Common mistakes.
What should we avoid?
</anti-patterns>
```

---

## 7.3 Example: PMM Best Practices

### From pmm-best-practices/SKILL.md

```markdown
<framework_overview>
## What This Is
B2B product marketing expertise based on April Dunford's positioning
methodology and proven messaging frameworks.

## When to Use
- Creating positioning strategy
- Writing messaging frameworks
- Reviewing marketing assets
- Developing ICP profiles
</framework_overview>

<principles>
## Core PMM Philosophy

### 1. POSITIONING IS PIGEONHOLING
You can't be everything to everyone. Own a specific place in YOUR
customer's mind, not the general market.

### 2. CUSTOMER PERCEPTION IS REALITY
It doesn't matter what you think you are. It matters what customers
perceive you to be.

### 3. CLARITY OVER CLEVERNESS
Boring and clear beats clever and confusing every time. If a
12-year-old can't explain it, simplify.

### 4. PROBLEMS BEAT OUTCOMES
"Reduce deployment time by 50%" beats "Improve developer
productivity." Specific problems > generic business outcomes.

### 5. POINT SOLUTION BEFORE PLATFORM
Win one use case completely before expanding. Dominant in a niche
beats mediocre across categories.
</principles>

<process>
## The Positioning Process

### Step 1: Competitive Alternative
What would customers use if you didn't exist?
NOT: "Other CRMs"
YES: "Spreadsheets and email"

### Step 2: Unique Attributes
What can you do that alternatives can't?
List 3-5 genuinely differentiating capabilities.

### Step 3: Value (So What?)
For each attribute, answer "So what does that mean for the customer?"
Attribute → Capability → Benefit → Value

### Step 4: Customer Characteristics
Who cares most about this value?
What makes them ideal customers?

### Step 5: Market Category
What frame of reference helps customers understand you fastest?
</process>

<templates>
## Positioning Statement Template

For [target customer]
Who [statement of need or opportunity]
[Product name] is a [market category]
That [key benefit/compelling reason to believe]
Unlike [competitive alternative]
We [primary differentiation]
</templates>

<anti-patterns>
## Common Mistakes

### 1. INSIDE-OUT POSITIONING
Starting with what you built instead of customer problems.
Wrong: "We have AI-powered analytics"
Right: "Teams waste 10 hours/week on manual reporting"

### 2. FEATURE DUMPING
Listing features without connecting to value.
Wrong: "SSO, RBAC, audit logs, SOC2"
Right: "Enterprise security that passes compliance audits"

### 3. COMPETITOR BASHING
Defining yourself by what competitors lack.
Wrong: "Unlike [Competitor], we actually work"
Right: "Built specifically for [your unique use case]"
</anti-patterns>
```

---

## 7.4 Example: Business Model Canvas Stress Test

### From bmc-stress-test/SKILL.md

```markdown
<framework_overview>
## The 7 Stress Tests

Based on Ash Maurya's methodology for validating business models.

| # | Stress Test | Purpose | Key Output |
|---|-------------|---------|------------|
| 1 | Mission | Define YOUR success criteria | MSC |
| 2 | Clarity | Deconstruct assumptions | Lean Canvas |
| 3 | Problem | Validate customer pain | Problem interviews |
| 4 | Solution | Validate solution fit | Solution interviews |
| 5 | Goes To Market | Validate channel | Acquisition experiments |
| 6 | Revenue | Validate willingness to pay | Pricing experiments |
| 7 | Growth | Validate scale | Growth model |
</framework_overview>

<quick_start>
## Rapid Viability Test (5 Minutes)

### Step 1: Goal Sizing
What's your Minimum Success Criteria (MSC)?
- Revenue goal: $_____/year
- Timeline: _____ years

### Step 2: Customer Sizing
- Average revenue per customer: $_____
- Customers needed: _____ (= MSC / avg revenue)

### Step 3: Market Sizing
- Early adopter segment: _____ people
- Realistic capture rate: _____%
- Achievable customers: _____

If achievable < needed, your business model needs work.
</quick_start>
```

---

## 7.5 Your Turn: Encode Your Expertise

### Step 1: Choose Your Domain

What process do you do repeatedly?

**Examples:**
- Sprint planning ritual
- Customer interview synthesis
- Technical decision documentation
- Incident post-mortem
- Code architecture review
- Hiring interview framework
- Feature specification template

### Step 2: List the Components

1. **Principles**: What are the core beliefs?
2. **Process**: What are the steps?
3. **Templates**: What's the output format?
4. **Anti-patterns**: What mistakes should we avoid?

### Step 3: Write the Skill

```markdown
# ~/.claude/skills/my-framework/SKILL.md

---
name: my-framework
description: Use when [specific trigger]. Applies [your framework name] methodology.
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
[Explanation]

### 2. [PRINCIPLE NAME]
[Explanation]

### 3. [PRINCIPLE NAME]
[Explanation]
</principles>

<process>
## The Process

### Step 1: [Name]
[What to do]

### Step 2: [Name]
[What to do]

### Step 3: [Name]
[What to do]
</process>

<templates>
## Output Format

[Template structure]
</templates>

<anti-patterns>
## Common Mistakes

### 1. [ANTI-PATTERN NAME]
[What's wrong and why]

### 2. [ANTI-PATTERN NAME]
[What's wrong and why]
</anti-patterns>
```

---

## Pause Point #5

**Task**: Build a domain expertise skill

**Duration**: 5 minutes

**Focus on**:
- Frontmatter with good trigger description
- At least 3 principles
- At least 3 process steps
- At least 1 anti-pattern

**Don't worry about**:
- Perfection (iterate later)
- Templates (add later)
- References (add later)

**Just get the core expertise written down.**

---

## 7.6 Testing Your Expertise Skill

### Trigger It

```bash
claude
> Help me with [domain task that should trigger your skill]
```

### Verify Behavior

- Does it ask clarifying questions?
- Does it follow your principles?
- Does it use your process?
- Does it avoid your anti-patterns?

### Iterate

- Add missing principles
- Clarify confusing steps
- Add examples
- Expand anti-patterns

---

## Key Takeaways

1. **Your expertise is valuable**—encode it
2. **Use the framework pattern**: principles, process, templates, anti-patterns
3. **Start with the core**—iterate to complete
4. **Test and refine**—skills improve with use
5. **This compounds**—every skill makes Claude smarter in YOUR domain

---

**[Next: Segment 8 - Subagent Patterns →](08-subagent-patterns.md)**

---

## Notes for Instructor

### Key Points to Land
1. Everyone has expertise worth encoding
2. The framework pattern is universal
3. Start rough, iterate to polish

### Live Build
- Pick a domain YOU know well
- Type the skill live
- Show how it works

### If Time Is Short
- Focus on principles + process
- Skip templates and anti-patterns
- Have them finish async
