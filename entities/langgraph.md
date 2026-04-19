# LangGraph

## Overview

LangGraph is a library for building stateful, multi-actor applications with LLMs, built on top of LangChain. It models workflows as graphs where nodes are computational steps and edges define control flow.

**Publisher:** LangChain
**Repository:** langchain-ai/langgraph
**Type:** Graph-based agent orchestration

## Core Model: Graph = States + Edges

### State
```python
class AgentState(TypedDict):
    messages: list
    current_agent: str
    task_result: str
```

### Nodes (Agents/Tools)
```python
def research_agent(state):
    # Do research
    return {"research": "...", "current_agent": "writer"}

def writer_agent(state):
    # Write based on research
    return {"output": "...", "current_agent": "research"}
```

### Edges (Control Flow)
```python
graph.add_edge("research", "write")  # direct
graph.add_conditional_edges(         # conditional
    "research",
    should_continue,
    {"continue": "write", "end": END}
)
```

## Key Strengths

- **Stateful** — graph maintains state across turns
- **Cyclic** — supports loops (unlike DAG-based systems)
- **Fault-tolerant** — can checkpoint and resume from any node
- **Human-in-the-loop** — can interrupt graph for approval

## Relationship to Other Entities

- [[autogen]] — Both support multi-agent; LangGraph uses graph semantics, AutoGen uses conversation
- [[hermes-agent]] — LangGraph is a framework for building agents; Hermes is an agent that could use LangGraph-style orchestration
- [[workflow]] (concept) — LangGraph is a concrete workflow implementation tool

## External Links

- GitHub: https://github.com/langchain-ai/langgraph
- Docs: https://langchain-ai.github.io/langgraph/
