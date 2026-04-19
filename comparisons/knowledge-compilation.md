# Knowledge Compilation Methods

## Overview

Compare methods for giving agents persistent knowledge: skills, fine-tuning, RAG, and prompting. Each has different cost/speed/reusability tradeoffs.

## Methods Overview

| Method | Persistence | Update Cost | Inference Speed | Reuse |
|--------|-------------|-------------|-----------------|-------|
| **System prompt** | Per-session | Low (edit text) | Normal | None (ephemeral) |
| **In-context (few-shot)** | Per-turn | Low (add examples) | Normal | None |
| **RAG** | Query-time | Low (add docs) | Slower (search) | Per-query |
| **Skill** | Permanent | Medium (edit SKILL.md) | Normal | Permanent, on-demand |
| **Fine-tuning** | Permanent | High (retrain) | Normal | Permanent, always-on |

## When to Use Each

### System Prompt
- Global agent behavior (identity, constraints)
- Things that should always apply
- **Don't use for:** task-specific knowledge that changes

### Few-Shot / In-Context
- New task types not covered by existing skills
- One-off patterns
- Format teaching
- **Don't use for:** frequently repeated patterns (use skills instead)

### RAG (Retrieval-Augmented Generation)
- Large document sets
- Knowledge that changes frequently
- Situational awareness
- **Don't use for:** procedural knowledge (skills are better)

### Skills (Hermes Pattern)
- Procedures / how-to knowledge
- Repeated workflows
- Discovered tricks and pitfalls
- **Don't use for:** factual knowledge (memory is better)

### Fine-Tuning
- Stable capabilities that should always be present
- Domain-specific language patterns
- High-volume, low-latency requirements
- **Don't use for:** frequently changing knowledge

## Decision Framework

```
Is the knowledge PROCEDURAL (how to do something)?
├── YES → Does it need to always be available?
│   ├── YES → Fine-tune
│   └── NO → Is it repeated often?
│       ├── YES → Skill
│       └── NO → Few-shot / In-context
└── NO (factual) → Is it large document set?
    ├── YES → RAG
    └── NO → Memory
```

## Relationship to Other Concepts

- [[skill]] — Skills are the Hermes-specific implementation of procedural knowledge persistence
- [[agent-memory]] — Memory handles factual/cross-session knowledge
- [[prompting]] — Prompting (few-shot, system prompt) is the ephemeral knowledge layer

## Sources

- Hermes skill system (based on this environment's 74 installed skills)
- RAG literature (2023-2026)
- Fine-tuning best practices (Hugging Face, Axolotl docs)
