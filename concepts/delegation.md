# Delegation (任务委托)

## Definition

Delegation is the practice of a parent agent handing off a subtask to a child agent (subagent) for independent execution. The parent retains oversight but the subagent works in isolation with its own context, tools, and session.

In Hermes, delegation is implemented via the `delegate_task` tool call.

## Two Delegation Patterns in Hermes

### Pattern 1: delegate_task (In-Process Subagent)

```
parent agent → delegate_task() → subagent (same process, isolated context)
```

- Subagent gets a fresh context with only what the parent passes in
- Subagent cannot access parent's tools directly (parent passes specific toolsets)
- Results returned to parent as a result array
- Max iterations default: 50 (configurable)
- Max 3 concurrent children (configurable)

### Pattern 2: Spawn Hermes Process (Out-of-Process)

```
parent agent → terminal(tmux/ssh) → hermes process (fully independent)
```

- Full process isolation — separate sessions, configs, tools
- Can run interactively via tmux PTY
- More overhead than delegate_task, but true independence
- Used for long-lived autonomous missions

## When to Delegate

Delegate when:
- Tasks are independent and can run in parallel
- You need fresh context (no state pollution from parent)
- Tasks are reasoning-heavy and would benefit from isolated context
- You need to run 2-3 tasks concurrently

Don't delegate when:
- Tasks are tightly coupled (subagent output feeds directly into next subagent's input)
- Overhead of context creation outweighs benefit
- Task requires parent's accumulated state

## Relationship to Other Concepts

- [[subagent]] — The entity being delegated to
- [[orchestration]] — Orchestration is the parent-level coordination of multiple delegates
- [[workflow]] — Delegation is the primitive; workflows compose delegations
- [[task-planning]] — Planning decides what to delegate and how to decompose

## delegate_task API Reference

```python
delegate_task(
    goal="What the subagent should accomplish",
    context="All background info, constraints, file paths, error history",
    toolsets=['terminal', 'file'],  # Subset of parent's toolsets
    tasks=[  # Batch mode: up to 3 parallel subagents
        {"goal": "...", "context": "...", "toolsets": [...]},
        {"goal": "...", "context": "...", "toolsets": [...]},
    ],
    max_iterations=50,  # Per subagent
    acp_command="claude",  # ACP-capable agent type
)
```

## Open Questions

- What is the optimal subagent granularity? (Too fine = overhead, too coarse = lost parallelism)
- How to handle subagents that fail in ways the parent can't diagnose?
- When does delegation overhead exceed the benefit of parallelism?
