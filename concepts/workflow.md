# Workflow (工作流)

## Definition

A workflow is a defined sequence of steps that accomplishes a goal. In the context of AI agents, a workflow is either:
1. **Static** — a predetermined sequence of actions (like a pipeline)
2. **Dynamic** — a sequence determined at runtime based on state (agent-driven)

Workflows are implemented in Hermes via:
- `delegate_task` composition (orchestration)
- Skill patterns (canned workflows encoded as skills)
- The `cronjob` tool (time-triggered workflows)

## Workflow as Skill

Many workflows in Hermes are encoded as skills with a consistent structure:

```yaml
# When to Use — trigger condition
# Steps — numbered sequence
# Verification — how to confirm success
# Pitfalls — known failure modes
```

Example: `subagent-driven-development` skill defines a 3-step-per-task workflow:
1. Dispatch implementer subagent
2. Dispatch spec compliance reviewer
3. Dispatch quality reviewer

## Workflow Characteristics

### Granularity
- **Macro workflow** — entire project lifecycle (plan → implement → test → deploy)
- **Meso workflow** — single phase (implement → review → fix)
- **Micro workflow** — single action with retry logic

### Trigger
| Trigger | Mechanism |
|---------|-----------|
| On-demand | User invokes or agent decides |
| Scheduled | `cronjob` tool at defined interval |
| Event | Webhook triggers (`webhook subscribe`) |
| Pipeline | Output of one step triggers next |

### Human-in-the-Loop
- **Fully automated** — no human intervention
- **Approval gate** — human approves before proceeding (Hermes gateway pending-approval pattern)
- **Human fallback** — agent tries, fails, escalates to human

## Workflow vs. Orchestration

- **Workflow** = the recipe (what steps, in what order)
- **Orchestration** = the execution engine (who does what, when, with what tools)

A workflow can be orchestrated by a single agent executing steps sequentially, or by an orchestrator delegating steps to subagents.

## Relationship to Other Concepts

- [[orchestration]] — Orchestration executes workflows
- [[delegation]] — Delegation is how subagents perform workflow steps
- [[task-planning]] — Planning decides if a task warrants a workflow

## Common Workflow Patterns

### TDD (Test-Driven Development)
```
Write failing test → Run (verify FAIL) → Write minimal code → Run (verify PASS) → Refactor
```

### Subagent-Driven Development
```
Read plan → Extract tasks → Per-task: implement → spec review → quality review → Repeat
```

### Research Workflow
```
Gather sources → Extract key findings → Synthesize → Write report
```

### Cron Workflow
```
Trigger (schedule) → Execute task → Deliver result → Log
```

## Open Questions

- How to make workflows adaptive (change sequence based on intermediate results)?
- When does a workflow become sophisticated enough to be called an agent?
- How to version workflows as requirements change?
