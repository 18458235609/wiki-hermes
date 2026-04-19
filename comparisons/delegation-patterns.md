# Delegation Patterns

## Overview

Compare Hermes's two delegation mechanisms: `delegate_task` (in-process) vs spawning a full Hermes process (out-of-process).

## Comparison Table

| Dimension | `delegate_task` | Spawn hermes process |
|-----------|-----------------|---------------------|
| **Isolation** | Separate context, same process | Fully independent process |
| **Context** | Fresh, parent-provided | No parent context (needs full prompt) |
| **Tools** | Subset controlled by parent | Full tool access |
| **Memory** | None (stateless) | Independent session |
| **Overhead** | Low | High |
| **Use case** | Quick parallel subtasks | Long autonomous missions |
| **Max concurrent** | 3 (configurable) | Limited by system resources |
| **Interactive** | No | Yes (via tmux PTY) |

## When to Use Each

### Use delegate_task when:
- Tasks are independent (can run in parallel)
- You need to pass specific context/tools
- Quick turnaround (minutes)
- Batch processing (3 at a time max)
- Subagent should not persist state

### Use spawn hermes process when:
- Long-lived autonomous agent
- Full CLI interactivity needed
- Complete isolation required (different config/profile)
- Agent needs its own memory
- Hours/days of work

## Relationship to Other Concepts

- [[delegation]] — The parent concept that encompasses both patterns
- [[subagent]] — delegate_task creates subagents; spawn creates independent agents
- [[workflow]] — Workflows often use delegation patterns

## Code Examples

### delegate_task
```python
delegate_task(
    goal="Fix the login bug in src/auth.py",
    context="Bug: session not persisting after redirect...",
    toolsets=['terminal', 'file'],
    max_iterations=20
)
```

### Spawn hermes process
```python
terminal(command="tmux new-session -d -s long-task 'hermes'", timeout=10)
terminal(command="tmux send-keys -t long-task 'Build the entire CI/CD pipeline' Enter")
```
