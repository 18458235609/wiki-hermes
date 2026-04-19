# Subagent (子代理)

## Definition

A subagent is an agent spawned by a parent agent to execute a specific subtask independently. The subagent operates with:
- **Isolated context** — only the information passed by the parent
- **Limited toolsets** — only the tools the parent authorizes
- **Own session** — no memory of prior parent sessions
- **Bounded iteration** — max turns limit prevents infinite loops

## Subagent vs Parent Agent

| Dimension | Subagent | Parent Agent |
|-----------|---------|-------------|
| Context | Fresh, provided by parent | Accumulated from session |
| Memory | None (stateless across sessions) | Cross-session via memory tool |
| Tools | Subset authorized by parent | Full toolset |
| Lifespan | One task (bounded) | Long-lived (session) |
| Creation | `delegate_task` call | User starts |

## Subagent Design in Hermes

From `subagent-driven-development` skill:

### Three-Role Pattern
1. **Implementer** — executes the actual task
2. **Spec Reviewer** — verifies implementation matches spec
3. **Quality Reviewer** — checks code quality, style, best practices

### Context Passing Principle
> "Read the plan ONCE. Extract everything. Don't make subagents read the plan file — provide the full task text directly in context."

This prevents the subagent from:
- Needing to search for context
- Operating on stale/missing information
- Wasting iterations on file I/O

## Relationship to Other Concepts

- [[delegation]] — Delegation is the act of creating and using a subagent
- [[multi-agent]] — Multiple subagents working together form a multi-agent system
- [[orchestration]] — The parent that coordinates subagents is the orchestrator

## Subagent Constraints

Subagents cannot:
- Call `delegate_task` recursively (max depth enforced)
- Access parent's memory or session state
- Ask clarifying questions (must request via context)
- Use tools not passed in `toolsets`

Subagents CAN:
- Read/write files within their scope
- Run terminal commands
- Use browser, web search
- Create artifacts for the parent to review

## Open Questions

- Should subagents be homogeneous (same model) or heterogeneous (specialized models)?
- How to handle subagents that partially complete but then fail?
- Can subagents spawn their own subagents (recursive delegation)?
