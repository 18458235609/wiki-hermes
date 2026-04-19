# When to Create a Skill vs Improve Prompting

## Question

A pattern keeps appearing. When should I capture it as a skill vs. just improving the system prompt or using better prompting?

## Short Answer

**Create a skill when:**
- It's a PROCEDURE (how to do X step by step)
- It has specific pitfalls/traps that are non-obvious
- It needs to be loaded on-demand, not always active
- It has verification steps that are non-obvious

**Improve system prompt when:**
- It's a GLOBAL behavior (always/never do X)
- It's an identity/role definition
- It's a constraint that always applies
- It's about tone/style/communication

**Use better prompting when:**
- It's a new task type you haven't solved yet (experiment first)
- The pattern isn't stable enough to codify
- You want to validate the approach before skillifying it

## Decision Matrix

| Aspect | Skill | System Prompt | In-Context Prompt |
|--------|-------|---------------|-------------------|
| Type | Procedure | Global rule | Example |
| Persistence | Permanent | Session | Turn |
| Load | On-demand | Always-on | Per-task |
| Change frequency | Low | Very low | High |
| Complexity | Medium-High | Low | Low |
| Best for | Workflows, gotchas | Identity, constraints | New patterns |

## The "3 Times Rule"

If you've done the same complex task 3+ times with the same approach:
1. Create a skill to capture it

If you're still figuring out the best approach:
1. Use in-context prompting to experiment
2. Once stable → skill

## Skill Creation Trigger Checklist

- [ ] Does it require 3+ steps?
- [ ] Are there pitfalls that caused errors before?
- [ ] Is the verification non-obvious?
- [ ] Would it be loaded on-demand, not always?
- [ ] Will it be reused 3+ times?

If 3+ yes → skill.
If fewer → in-context prompting or system prompt addition.

## Relationship to Other Concepts

- [[skill-creation]] — How to create a skill
- [[skill]] — What skills are
- [[prompting]] — The alternative

## Sources

Based on Hermes skill system experience and this environment's 74 installed skills.
