# Skill Creation (技能创建)

## Definition

Skill creation is the process of capturing procedural knowledge — how to do something — into a skill file. It is distinct from writing documentation; a skill is **actionable**: it tells the agent exactly what to do, in what order, with what pitfalls to avoid.

## When to Create a Skill

Create a skill when:

1. A complex workflow has been figured out through iteration and would be repeated
2. A correction was made that the agent should remember
3. A new tool or API requires specific usage patterns
4. A "gotcha" was discovered that would be painful to rediscover

**Don't create skills for:**
- One-off facts (put in memory instead)
- Trivial tasks that take <2 minutes to re-derive
- Tasks that change frequently (better in context)

## The Skill Creation Process

### 1. Identify the Trigger Condition
Write a clear "When to Use This Skill" section — the condition that tells the agent when this skill is relevant:
```
Use this skill when the user asks to [specific task type].
```

### 2. Capture the Steps
Numbered, imperative steps:
```
1. Do X
2. Do Y
3. If Z, then do W
```

### 3. Include Verification
Always add a step to verify success:
```
4. Verify by checking that [expected outcome] occurred.
```

### 4. Document Pitfalls
This is the most valuable part of a skill — real errors encountered:
```
⚠️ Pitfall: [What goes wrong] → [How to fix it]
```

### 5. Link to Related Skills
At least 2 other skills or concepts:
```
Related: [[related-skill]], [[another-skill]]
```

## Skill Template

```yaml
---
name: task-type
description: Handle [specific task type] end-to-end
version: 1.0.0
author: Hermes Agent
tags: [task-type, workflow]
related_skills: [related-skill]
---

# Task Type Title

## When to Use
Use this skill when [trigger condition].

## Steps
1. [Step 1]
2. [Step 2]
3. [Step 3 — with conditional]

## Verification
Verify success by [checking X].

## Pitfalls
- ⚠️ [Pitfall 1] → [Fix 1]
- ⚠️ [Pitfall 2] → [Fix 2]

## Related
[[related-skill]], [[another-skill]]
```

## Relationship to Other Concepts

- [[skill-management]] — Skill creation is the first phase of the skill lifecycle
- [[skill-acquisition]] — Creation captures what acquisition has produced
- [[self-reflection]] — Reflection identifies when a skill is needed (gap detected)
- [[learning-from-mistakes]] — Mistakes often trigger skill creation

## Open Questions

- At what complexity threshold should something become a skill vs. stay in memory?
- Can the agent autonomously create skills without human review?
- Should skills be versioned and have changelogs?
