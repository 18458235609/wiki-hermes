# MetaGPT

## Overview

MetaGPT is a multi-agent framework where agents扮演 specific software team roles (e.g., Product Manager, Architect, Developer, Tester). Agents collaborate by generating structured documents (SOPs) that other agents consume, rather than chatting in free-form.

**Paper:** "Meta Programming for A Multi-Agent Collaborative Framework"
**Venue:** ICLR 2024 (Oral, Top 1.2%)
**Repository:** geekan/MetaGPT

## Core Innovation: SOP-Driven Agents

Unlike chat-based multi-agent systems, MetaGPT agents generate formal artifacts:

```
User Request
    ↓
Product Manager → Writes SPEC.md
    ↓
Architect → Designs system architecture based on SPEC
    ↓
Project Manager → Creates project plan
    ↓
Developers → Implement code from spec
    ↓
Testers → Write and run tests
```

Each agent has a defined role with specific output format. Agents "speak" through structured documents, not free-form messages.

## Key Design Decisions

1. **Roles with defined outputs** — PM writes specs, Architect writes design docs, etc.
2. **SOP as backbone** — the pipeline enforces a software development methodology
3. **Code and test generation** — end-to-end from spec to working code
4. **Minimal chat** — communication via structured artifacts, not conversation

## Relationship to Other Entities

- [[hermes-agent]] — Hermes is a general agent; MetaGPT is a specialized multi-agent coding framework
- [[multi-agent]] (concept) — MetaGPT exemplifies the hierarchical/role-based architecture
- [[autogen]] — Microsoft's multi-agent framework (conversation-based, different from SOP)
- [[crewai]] — another role-based multi-agent framework

## External Links

- Paper: https://arxiv.org/abs/2308.00352
- GitHub: https://github.com/geekan/MetaGPT
