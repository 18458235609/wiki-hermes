# Multi-Agent (多代理系统)

## Definition

A multi-agent system is a collection of two or more agents that work together to accomplish goals that exceed the capacity of any single agent. Agents may share goals, have specialized roles, communicate with each other, and coordinate their actions.

Multi-agent systems contrast with single-agent approaches where one agent handles everything sequentially.

## Agent Roles

### Orchestrator / Planner
The parent agent that decomposes the task and coordinates subagents. Responsible for:
- Task decomposition into parallelizable subtasks
- Assigning tasks to appropriate subagents
- Aggregating results
- Handling failures and retrying

### Specialized Agents
Agents with focused roles (e.g., frontend-dev, backend-dev, tester, reviewer). Each specialized agent:
- Has context tailored to its role
- Uses a subset of tools relevant to its function
- Operates independently within its scope

## Multi-Agent Architectures

### 1. Hierarchical (Tree)
```
Orchestrator
├── Subagent A (implements feature)
├── Subagent B (implements feature)
└── Subagent C (tests integration)
```
Parent decomposes → parallel execution → aggregates results.
Used in: subagent-driven-development, MetaGPT-style workflows.

### 2. Supervisor / Escalation
```
Task → Agent A → [success] → done
              → [failure] → Supervisor reviews → assigns to Agent B
```
Failure triggers escalation to a supervisor who reassigns.
Used in: REGREACT (7-agent regulatory extraction).

### 3. Collaborative / Peer-to-Peer
```
Agent A ←→ Agent B ←→ Agent C
     (share context, debate, vote)
```
No central orchestrator; agents communicate directly.
Used in: ChatDev-style collaborative coding.

### 4. Mixture of Agents (MoA)
```
Input → Agent 1 → Agent 2 → Agent 3 → Output
         ↑                        ↓
         ← ← ← (feedback) ← ← ←
```
Agents refine each other's outputs in rounds.
Hermes has `moa` toolset for this pattern.

## Multi-Agent Communication Patterns

| Pattern | Mechanism | Use Case |
|---------|-----------|---------|
| Shared context | Parent passes context to all | Parallel independent tasks |
| Direct messaging | Agents send results to each other | Chained/refinement tasks |
| Blackboard | Shared artifact all agents read/write | Collaborative problem solving |
| Vote/consensus | Agents vote on best output | Ensemble selection |

## Relationship to Other Concepts

- [[delegation]] — Delegation is the primitive for creating multi-agent systems
- [[subagent]] — Each agent in a multi-agent system is a subagent (or peer)
- [[orchestration]] — Coordination of multi-agent execution

## Key Systems

- **MetaGPT** (ICLR 2024) — Multi-agent via "SOP" pipeline: generate docs → assign roles → execute → review
- **ChatDev** — Collaborative software dev with specialized agents (CTO, programmer, reviewer)
- **AutoGen** — Microsoft framework for multi-agent conversation
- **CrewAI** — Role-based agents with goal chaining
- **LangGraph** — Graph-based agent orchestration

## Open Questions

- At what complexity threshold does a task need multi-agent vs. single-agent with better prompting?
- How to prevent agents from giving inconsistent information to each other?
- How to debug multi-agent failures when the failure could be in any agent or their communication?
