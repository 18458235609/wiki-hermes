---
title: Feedback Loop (反馈回路)
created: 2026-04-19
updated: 2026-04-19
type: concept
tags: [feedback-loop, self-improvement, learning-from-mistakes]
sources: [raw/papers/self-reflection-arxiv-2026.md]
---

## Definition

A feedback loop is a circuit where the output of a system is fed back as input for the next cycle — enabling self-correction and adaptation over time. In AI agents, feedback loops can be:

- **Internal** — the agent's own outputs become inputs for its next reasoning step
- **External** — environment/execution results feed back into the agent's state
- **Human-in-the-loop** — human feedback (explicit or implicit) shapes agent behavior

## Feedback Loop Components

1. **Signal** — what is being measured/evaluated (output quality, goal attainment, error rate)
2. **Sensor** — how the signal is captured (self-reflection, tool return codes, human rating)
3. **Response** — how the agent adjusts based on the signal
4. **Actuator** — the change in behavior that the response triggers

## Relationship to Other Concepts

- [[self-reflection]] — Reflection is the "sensor" in many internal feedback loops
- [[error-recovery]] — Error recovery is the "response" and "actuator" components
- [[learning-from-mistakes]] — Learning requires a feedback loop: error → correction → encoding
- [[skill-acquisition]] — Skills are the long-term result of positive feedback loops

## Human Feedback Types

| Type | Mechanism | Speed |
|------|-----------|-------|
| Explicit rating | Thumbs up/down, Likert scale | Slow |
| Implicit signal | Task completion, follow-up questions | Medium |
| Corrective feedback | "Actually, do X instead" | Medium |
| Delegation pattern | User corrects repeatedly → agent infers pattern | Fast |

## Open Questions

- How to learn from feedback without overfitting to a single user's preferences?
- What's the minimum feedback required to bootstrap a useful loop?
- How to distinguish signal from noise in human feedback?
