# When to Use Multi-Agent vs Single-Agent

## Question

At what complexity threshold does a task need multi-agent decomposition vs. a single capable agent with better prompting?

## Short Answer

Multi-agent adds overhead (coordination, context passing, aggregation). Use it when:
- Tasks are parallelizable (independent subtasks)
- Different expertise domains are needed
- Failure isolation matters (one subagent failing shouldn't crash everything)
- Multiple roles need to collaborate (review, approve, etc.)

Single agent is better when:
- Task is sequential (output feeds directly into next step)
- Context is shared (subagent would need all parent context anyway)
- Overhead outweighs benefit
- Simpler is sufficient

## Decision Framework

```
Task: Is the work fundamentally parallel?
├── YES → Multi-agent likely worth it
│   ├── Can tasks run independently? → Yes → Multi-agent
│   └── Do they share state? → Yes → Consider pipeline instead
└── NO → Is the task complex enough to need multiple expertise areas?
    ├── YES → Multi-agent (role-based)
    └── NO → Is it simply too long for context?
        ├── YES → Try better prompting or skill first
        └── NO → Single agent
```

## Cost-Benefit Analysis

| Scenario | Approach | Rationale |
|----------|----------|-----------|
| Build full-stack app (frontend + backend + tests + deploy) | Multi-agent (roles) | Large, parallelizable, different expertise |
| Debug a complex race condition | Single agent + skill | Needs full context, not parallel |
| Research X and write report | Multi-agent (researcher + writer) | Independent phases, different focus |
| Generate and review code | Multi-agent (writer + reviewer) | Feedback loop benefits from roles |
| Extract data from 100 PDFs | Single agent + batch | Same task, just parallelize input |

## Key Signals to Escalate to Multi-Agent

1. Agent starts making errors in long tasks (context overflow)
2. Same task repeated 10+ times with same skill
3. Task requires expertise the agent doesn't reliably have
4. Failure in one step ruins the whole task (need isolation)
5. You find yourself copy-pasting context between turns

## Relationship to Other Concepts

- [[multi-agent]] — Architecture
- [[delegation]] — Mechanism for creating multi-agent systems
- [[orchestration]] — Control plane that decides when to decompose

## Sources

Based on Hermes Agent documentation, MetaGPT paper (ICLR 2024), and practical experience.
