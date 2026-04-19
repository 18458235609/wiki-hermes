---
title: Agent Memory (Agent 记忆系统)
created: 2026-04-19
updated: 2026-04-19
type: concept
tags: [memory, self-improvement, learning-from-mistakes]
sources: [raw/papers/memory-arxiv-2026.md]
---

## Definition

Agent memory refers to mechanisms that allow an AI agent to retain information across sessions, episodes, or tasks — so that past experiences can inform future behavior. This is fundamental to agents that need to improve over time.

Memory is distinct from context window — context is ephemeral (per-session); memory is persistent.

## Memory Architectures

### Episodic Memory
Records specific experiences: what the agent did, what happened, what the outcome was. Useful for learning from past successes and failures.

### Semantic Memory
Structured knowledge extracted from episodes: patterns, facts, generalizable rules. This is where "lessons learned" live.

### Working Memory
Active, transient state during task execution — what the agent is currently considering. This is the context window.

### Procedural Memory
How to do things — encoded as skills, prompting templates, or fine-tuned weights. This is the compiled form of repeated successful behaviors.

## Key Papers

- **Adaptive Memory Crystallization** (2026) — autonomous agents in dynamic environments that crystallize memories over time
- **Drawing on Memory** (2026) — dual-trace encoding improves cross-session recall for LLM agents
- **Persistent Identity in AI Agents** (2026) — multi-anchor architecture for resilient memory and continuity
- **Constraint-Aware Corrective Memory** (2026) — memory for drug discovery agents that corrects errors

## Relationship to Other Concepts

- [[learning-from-mistakes]] — Memory is the storage substrate for lessons learned
- [[feedback-loop]] — Memory closes the loop over time (feedback across sessions)
- [[skill-acquisition]] — Frequently successful behaviors can be compiled into skills

## Open Questions

- What is the right granularity for memories? (full episodes vs. summarized insights)
- How to avoid memory corruption / conflicting memories over time?
- When should memories be forgotten vs. retained?
- How to balance memory storage cost vs. retrieval benefit?
