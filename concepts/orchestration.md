# Orchestration (编排)

## Definition

Orchestration is the parent-level function of coordinating multiple subagents — deciding what gets delegated when, how results aggregate, what happens on failure, and when to stop.

Orchestration is not about what each subagent does; it's about the control plane: scheduling, routing, and result aggregation.

## Core Orchestration Responsibilities

### 1. Task Decomposition
Break a complex goal into subtasks that can execute independently:
- Identify dependencies (what must happen before what)
- Determine which tasks can run in parallel
- Size tasks appropriately (not too fine, not too coarse)

### 2. Delegation
Assign each subtask to a subagent with:
- Full context needed to execute
- Appropriate toolset authorization
- Clear success criteria
- Error handling instructions

### 3. Monitoring
Track subagent progress:
- Poll for completion (batch results)
- Detect failures early
- Handle timeout (max_iterations exceeded)

### 4. Aggregation
Combine subagent results:
- Merge outputs into coherent whole
- Resolve conflicts between subagent results
- Present final result to user

### 5. Recovery
Handle failures:
- Retry subagent on failure
- Escalate to human if unrecoverable
- Gracefully degrade if partial results are acceptable

## Orchestration vs. Direct Execution

| | Direct (Single Agent) | Orchestrated (Multi-Agent) |
|-|---------------------|--------------------------|
| Complexity | Simple tasks | Complex, multi-phase tasks |
| Context | All in one place | Distributed across subagents |
| Parallelism | Sequential | Can run in parallel |
| Overhead | Low | Higher (coordination cost) |
| Failure isolation | None | Subagent failure doesn't crash whole system |
| Debugging | Easier | Harder (which agent failed?) |

## Orchestration Patterns

### Fan-Out / Fan-In
```
Task → [A] → [B] → [C] → Result
         ↑       ↑       ↓
         ← ← ← ← ← ← ← ←
```
Dispatch all → wait for all → aggregate.

### Pipeline
```
Input → Agent1 → Agent2 → Agent3 → Output
```
Each agent's output is the next agent's input.

### Supervisor / Escalation
```
Worker fails → Supervisor reviews → reassigns or escalates
```

## Relationship to Other Concepts

- [[delegation]] — Orchestration uses delegation as its primary primitive
- [[subagent]] — Orchestration coordinates subagents
- [[multi-agent]] — Orchestration is what makes multi-agent systems coherent
- [[workflow]] — Workflow defines the sequence; orchestration enforces it

## Open Questions

- How to make orchestration decisions at runtime (dynamic decomposition) vs. static planning?
- When should orchestration be done by an LLM vs. a deterministic script?
- How to test orchestration logic without running full multi-agent experiments?
