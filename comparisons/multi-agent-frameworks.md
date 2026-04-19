# Multi-Agent Frameworks Comparison

## Overview

Compare major multi-agent frameworks by their core paradigm, communication model, and best-fit use cases.

## Framework Summary

| Framework | Paradigm | Communication | Orchestration | Best For |
|-----------|----------|---------------|---------------|----------|
| **MetaGPT** | SOP/Role-based | Structured docs (SPECs) | Pipeline | End-to-end software dev |
| **AutoGen** | Conversational | Free-form messages | Message passing | Flexible multi-agent conv |
| **CrewAI** | Role-based | Task passing | Sequential/Hierarchical | Goal-oriented workflows |
| **LangGraph** | Graph-based | State passing | Graph edges/nodes | Complex stateful workflows |
| **Hermes** | Task-delegation | Skill-based | Subagent dispatch | General-purpose, any task |

## Detailed Comparison

### Communication Model

| | MetaGPT | AutoGen | CrewAI | LangGraph | Hermes |
|-|---------|---------|--------|-----------|--------|
| Model | Artifacts/docs | Messages | Tasks | State | Context + skills |
| Structure | Highly structured | Free-form | Semi-structured | Arbitrary graph | Prompt + context |

### Autonomy

| | MetaGPT | AutoGen | CrewAI | LangGraph | Hermes |
|-|---------|---------|--------|-----------|--------|
| Agent autonomy | Fixed pipeline | High (agents decide) | Medium (role-defined) | Per-node defined | High (subagent) |
| Human oversight | Minimal | Optional | Optional | Checkpoint-based | Approval gates |

### Use Case Fit

| Use Case | Best Choice |
|----------|-------------|
| Full-stack app from spec | MetaGPT |
| Multi-agent research debate | AutoGen |
| Structured business process | CrewAI |
| Complex cyclic workflows | LangGraph |
| General-purpose CLI automation | Hermes |
| Coding agent delegation | Claude Code (via Hermes) |

## Key Insight

**MetaGPT** = agents that "read and write specs"
**AutoGen** = agents that "talk to each other"
**CrewAI** = agents that "pass tasks"
**LangGraph** = agents that "update shared state"
**Hermes** = agents that "execute skills and delegate"

## Sources

- MetaGPT: ICLR 2024, arxiv:2308.00352
- AutoGen: microsoft/autogen GitHub
- CrewAI: crewAI/crewAI GitHub
- LangGraph: langchain-ai/langgraph GitHub
