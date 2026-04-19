# Task Planning (任务规划)

## Definition

Task planning is the cognitive process of decomposing a complex goal into a sequence of actionable steps, determining dependencies, and deciding how to execute them (sequentially, in parallel, or conditionally).

Planning is distinct from execution — it's the "think before acting" phase.

## Planning vs. Execution

| Phase | Focus | Output |
|-------|-------|--------|
| Planning | What, in what order, with what resources | Task list / plan |
| Execution | Do the work | Implementation, test results |
| Review | Did it work? | Pass/fail, issues found |

## Task Decomposition Strategies

### 1. Linear Decomposition
Simple sequential steps:
```
Task A → Task B → Task C
```
When tasks are fully dependent (each needs the previous output).

### 2. Parallel Decomposition
Independent tasks:
```
Task A ──┬
Task B ──┼──→ Aggregate → Done
Task C ──┘
```
When tasks can run simultaneously.

### 3. Hierarchical Decomposition
Group related tasks:
```
Project
├── Phase 1
│   ├── Task A
│   └── Task B
└── Phase 2
    ├── Task C
    └── Task D
```
When tasks have natural phases or groupings.

### 4. Conditional Decomposition
```
If X → Task A
Else → Task B
```
Runtime decision based on state.

## Planning Triggers

1. **Explicit request** — user says "make a plan"
2. **Implicit need** — complex task detected, agent decides to plan before acting
3. **Failure recovery** — task failed, agent plans around the failure
4. **Change detection** — environment changed, agent replans

## The Hermes Planning Skill

From `writing-plans` skill:
- Plans should be in markdown with numbered steps
- Each step should be verifiable
- Include prerequisites and constraints
- Link to relevant skills

## Plan Quality Criteria

A good plan:
- ✅ Has clear success criteria for each step
- ✅ Identifies dependencies (what must come first)
- ✅ Is appropriately granular (not too high-level, not micro-managed)
- ✅ Has verification steps (how to confirm each step worked)
- ✅ Anticipates failure modes

A bad plan:
- ❌ Vague steps ("do X well")
- ❌ No dependency ordering
- ❌ All steps at same granularity
- ❌ No way to verify success

## Relationship to Other Concepts

- [[workflow]] — A plan defines a workflow
- [[orchestration]] — Orchestration executes the plan
- [[delegation]] — Delegation assigns planned tasks to subagents

## Open Questions

- When should an agent plan vs. act directly? (planning has overhead)
- Can agents learn to plan better over time from experience?
- How to handle planning when the goal itself is underspecified?
