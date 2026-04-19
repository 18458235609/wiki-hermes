---
title: Error Recovery (错误恢复)
created: 2026-04-19
updated: 2026-04-19
type: concept
tags: [error-recovery, self-improvement, debugging]
sources: [raw/papers/self-reflection-arxiv-2026.md]
---

## Definition

Error recovery is the process by which an AI agent detects that something went wrong — a tool call failed, an output is incorrect, a plan is no longer viable — and adapts its strategy to recover and continue toward the goal.

Error recovery is distinct from mere error detection. Detection identifies that a problem exists; recovery determines what to do about it.

## Failure Modes

Common categories of failures agents encounter:

| Mode | Description | Typical Recovery |
|------|-------------|-----------------|
| Tool failure | API timeout, permission denied, malformed output | Retry with backoff, try alternative tool |
| Logical error | Reasoning led to wrong conclusion | Trigger [[self-reflection]], revise plan |
| Env change | State changed mid-execution | Re-query state, replan |
| Ambiguity | Input unclear or underspecified | Ask for clarification or try multiple interpretations |

## Relationship to Other Concepts

- [[self-reflection]] — Reflection provides the self-diagnostic capability that drives recovery
- [[debugging]] — Debugging is error recovery applied to code/logic tasks
- [[feedback-loop]] — Recovery is the action side of a feedback loop

## Key Papers

- **REGREACT** (2026) — self-correcting multi-agent pipelines for structured information extraction, uses 7 specialized agents that self-correct collectively
- **Self-Correcting RAG** (2026) — self-correcting retrieval augmented generation via constrained optimization
- **CAPTCHA Solving** (2026) — self-corrective training data generation for GUI agents

## Open Questions

- How to balance recovery attempts vs. giving up and escalating?
- When should an agent rollback vs. forward (try to salvage the current plan)?
- How to avoid recovery loops (error → recover → new error → recover...)?
