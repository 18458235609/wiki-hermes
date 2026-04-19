---
title: Self-Reflection (自我反思)
created: 2026-04-19
updated: 2026-04-19
type: concept
tags: [self-reflection, self-improvement]
sources: [raw/papers/self-reflection-arxiv-2026.md]
---

## Definition

Self-reflection is the ability of an AI agent to evaluate its own reasoning, outputs, and actions — then explicitly reason about where it may have gone wrong. It is distinct from Chain-of-Thought (CoT) reasoning in that reflection is **second-order**: the agent thinks about its own thinking, not just through a problem.

## How It Works

Typical self-reflection implementations:

1. **Generate** — produce an initial response or action plan
2. **Reflect** — a dedicated reflection prompt or module evaluates the output against criteria (correctness, completeness, style)
3. **Revise** — the agent incorporates the reflection feedback to produce a better output

Examples in literature:
- **Self-Correcting RAG** (2026) — reformulates retrieval and generation as constrained optimization, self-correcting hallucinations
- **REGREACT** (2026) — 7-agent pipeline with self-correction for regulatory info extraction
- **Cross-Domain Query Translation** (2026) — multi-agent framework with reflection-based reasoning

## Why It Matters

Without reflection, an agent commits the same errors repeatedly. Reflection closes the loop between generation and evaluation, enabling the agent to:

- Catch hallucinations before they propagate
- Retry failed sub-tasks adaptively
- Learn which strategies work in which contexts

## Relationship to Other Concepts

- [[error-recovery]] — Self-reflection is the cognitive mechanism that enables error recovery
- [[feedback-loop]] — Reflection is a form of internal feedback loop
- [[chain-of-thought]] — CoT is the prerequisite; reflection builds on top of it

## Open Questions

- At what cost/complexity does self-reflection stop being worthwhile?
- Can reflection be trained (fine-tuned) vs. always prompted?
- How to avoid infinite reflection loops (agent second-guessing itself)?

## Sources

- [Self-Correcting RAG (2026)](http://arxiv.org/abs/2604.10734v1)
- [REGREACT (2026)](http://arxiv.org/abs/2604.12054v1)
- [Cross-Domain Query Translation (2026)](http://arxiv.org/abs/2604.13353v1)
