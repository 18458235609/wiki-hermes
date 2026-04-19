---
title: Learning from Mistakes (错误中学习)
created: 2026-04-19
updated: 2026-04-19
type: concept
tags: [learning-from-mistakes, error-recovery, self-improvement, memory]
sources: [raw/papers/self-reflection-arxiv-2026.md, raw/papers/memory-arxiv-2026.md]
---

## Definition

Learning from mistakes is the capability that allows an AI agent to treat errors not just as failures to recover from, but as events that change its future behavior — either immediately (within a session) or across sessions (via [[agent-memory]]).

This is distinct from [[error-recovery]]: error recovery is about fixing the current failure; learning from mistakes is about preventing future similar failures.

## Mechanisms

### In-Session Adaptation
When an error is detected, the agent:
1. Logs what went wrong and why
2. Adjusts strategy for the remainder of the current task
3. Optionally creates a [[skill]] or updates a skill to encode the lesson

### Cross-Session Learning
Errors encountered in previous sessions are stored in memory and consulted when facing similar tasks.

## Relationship to Other Concepts

- [[error-recovery]] — Error recovery handles the immediate failure; learning handles the future
- [[self-reflection]] — Reflection is the mechanism that converts errors into lessons
- [[feedback-loop]] — The feedback from a mistake feeds back into future behavior
- [[agent-memory]] — Memories of mistakes are the substrate of this learning

## Failure Modes

| Failure Mode | Description |
|-------------|-------------|
| Same mistake twice | Error was corrected but not stored; no memory update |
| Over-correction | Agent becomes too conservative after one error |
| Wrong lesson learned | Agent attributes failure to the wrong cause |
| Forgetting | Memory of mistakes degrades or is lost over time |

## Open Questions

- How to distinguish genuine root causes from symptoms?
- How to avoid the agent learning spurious correlations from a single error?
- Should all mistakes be remembered, or only statistically significant patterns?
