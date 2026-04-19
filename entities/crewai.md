# CrewAI

## Overview

CrewAI is a multi-agent framework where agents have explicit roles and collaborate by passing tasks to each other in a defined sequence or hierarchy. It emphasizes role-based agents with specific goals.

**Repository:** crewAI/crewAI
**Type:** Role-based multi-agent orchestration

## Core Concepts

### Role
```python
researcher = Agent(
    role="Research Analyst",
    goal="Find the most relevant market data",
    backstory="Expert at analyzing market trends...",
    tools=[search, browse]
)
```

### Task
```python
task = Task(
    description="Research AI market trends for 2026",
    agent=researcher,
    expected_output="A summary of key market findings"
)
```

### Crew
```python
crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, write_task],
    process="sequential"  # or "hierarchical"
)
crew.kickoff()
```

## Process Modes

### Sequential
```
Researcher → Writer → Editor
(tasks execute in order, output of one feeds next)
```

### Hierarchical
```
Manager
├── Researcher
├── Writer
└── Analyst
(manager delegates to subordinates, aggregates results)
```

## Relationship to Other Entities

- [[autogen]] — Both are multi-agent frameworks; CrewAI is more role-focused, AutoGen is more conversational
- [[metagpt]] — Both use role-based agents; MetaGPT uses SOPs, CrewAI uses goal-driven tasks
- [[hermes-agent]] — Hermes can orchestrate multiple agents; CrewAI is a framework for building such systems

## External Links

- GitHub: https://github.com/crewAI/crewAI
- Docs: https://docs.crewai.com/
