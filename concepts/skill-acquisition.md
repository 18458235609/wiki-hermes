---
title: Skill Acquisition (技能获取)
created: 2026-04-19
updated: 2026-04-19
type: concept
tags: [skill-acquisition, skill, self-improvement, skill-management]
sources: [raw/papers/memory-arxiv-2026.md]
---

## Definition

Skill acquisition is the process by which an AI agent develops the ability to reliably perform a new capability — whether that's a new task type, a better way of doing an existing task, or leveraging a new tool.

In the context of Hermes-style agents, skill acquisition typically means building reusable, documented skill modules that can be loaded on demand.

## Acquisition Pathways

### 1. Prompting (in-context)
The skill lives entirely in a prompt/system message. No weight changes. Fast to create, but消耗 context window and requires explicit instructions every time.

### 2. Fine-tuning
Train model weights on examples of the skill. High upfront cost, but fast inference. Good for frequently-used, stable skills.

### 3. Skill Modules ( Hermes Pattern)
Reusable code + prompt bundles stored in a skill directory. Can be loaded dynamically. The approach used by Hermes Agent.

### 4. Learning from Feedback
The agent observes outcomes of its actions and updates its internal strategy (via [[feedback-loop]]). This is the "learning" form of skill acquisition.

## Relationship to Other Concepts

- [[agent-memory]] — Memory of past successes enables skill formation
- [[feedback-loop]] — Feedback loops signal when a skill needs updating
- [[self-reflection]] — Reflection helps identify when a skill is missing or failing

## The Hermes Skill Lifecycle

1. **Identify** — A recurring task pattern is noticed
2. **Capture** — The knowledge is codified into a skill file (SKILL.md)
3. **Test** — The skill is verified to work reliably
4. **Load** — Skill is loaded when needed via skill_view
5. **Maintain** — Skill is updated as the domain evolves

## Open Questions

- When to upgrade from prompting to fine-tuning to skill modules?
- How to avoid skill bloat (too many skills, hard to find the right one)?
- Can agents autonomously acquire skills without human codification?
