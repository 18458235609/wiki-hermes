# AutoGen

## Overview

AutoGen is Microsoft's multi-agent framework based on agent conversations. Agents converse with each other to solve tasks, with each agent assigned a specific role and capable of specific tool calls.

**Publisher:** Microsoft Research
**Repository:** microsoft/autogen
**Type:** Conversation-based multi-agent framework

## Core Concept: Conversational Agents

AutoGen's fundamental unit is an agent that can send/receive messages:

```
Agent A (User Proxy)
    ↓ sends message
Agent B (Assistant)
    ↓ receives + responds
Agent A (receives response)
```

Agents are defined by:
- **System message** — defines the agent's role
- **Tools** — what the agent can do
- **LLM** — the model powering the agent

## Key Patterns

### Two-Agent Pattern
```
User Proxy Agent ←→ Assistant Agent
```
Simple back-and-forth. User proxy forwards user input; assistant responds with code/answers.

### Group Chat
```
Agent A ↔ Agent B ↔ Agent C
         ↓
    (all connected)
```
Multiple agents in a group chat, with a manager selecting the next speaker.

### Human-in-the-Loop
```
Agent → [pending approval] → Human approves/denies → continues
```
AutoGen supports stopping for human input during agent workflows.

## Comparison with Hermes

| | AutoGen | Hermes |
|-|---------|--------|
| Paradigm | Conversation-based | Tool-calling + skills |
| orchestration | Message passing | Task delegation |
| Scope | Multi-agent conv | Any task type |
| Platform | Python SDK | CLI + gateway |

## Relationship to Other Entities

- [[hermes-agent]] — Hermes uses task delegation; AutoGen uses message passing
- [[metagpt]] — MetaGPT uses SOPs/documents; AutoGen uses free-form conversation
- [[crewai]] — similar role-based approach to AutoGen but with different abstractions

## External Links

- GitHub: https://github.com/microsoft/autogen
- Docs: https://microsoft.github.io/autogen/
