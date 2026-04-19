# System Prompt (系统提示)

## Definition

The system prompt is the foundational instruction layer that defines an agent's identity, capabilities, constraints, and default behaviors. Unlike user prompts which change per task, the system prompt persists across the session and sets the agent's baseline configuration.

In Hermes, the system prompt is composed of:
1. Base system instruction
2. Loaded skills (skill content injected)
3. User profile / memory context
4. Platform-specific instructions (gateway)

## System Prompt Components

### 1. Identity & Role
```
You are [agent type], an AI assistant that specializes in [domain].
You are helpful, knowledgeable, and direct.
```

### 2. Behavioral Constraints
```
Never make up facts. If you're uncertain, say so.
Always verify before taking actions that modify data.
```

### 3. Capability Definitions
```
You have access to:
- File system (read/write/search)
- Terminal (run shell commands)
- Web search (search and browse)
```

### 4. Style/Tone
```
Be concise. Prioritize substance over verbosity.
Use Chinese for communication with the user.
```

### 5. Platform Context (gateway)
```
This conversation is from [platform].
Respond appropriately for this platform's norms.
```

## System Prompt vs. User Prompt

| | System Prompt | User Prompt |
|-|---------------|-------------|
| Scope | Global (session-wide) | Task-specific |
| Control | Agent/developer sets | User provides |
| Persistence | Across all turns | Current turn only |
| Content | Identity, constraints, skills | The actual task |

## System Prompt Engineering

### Layering Principle
System prompts work best when layered from general to specific:
1. Core identity (broadest)
2. Domain expertise
3. Task-specific instructions
4. Format/output constraints

### Avoid Overloading
- Too many constraints → model ignores some
- Too verbose → key instructions buried
- Contradictory instructions → unpredictable behavior

### Skill Injection
Skills add their content to the system prompt when loaded. Best practice:
- Skill content should be self-contained
- Skills should not contradict the base system prompt
- Load skills only when relevant (not preemptively)

## Relationship to Other Concepts

- [[prompting]] — System prompt is the broadest layer of prompting
- [[skill]] — Skills inject content into the system prompt
- [[role-playing]] — Role is typically defined in the system prompt
- [[memory]] — User profile and memory context are part of the system prompt

## Open Questions

- How to maintain system prompt freshness as the environment changes?
- Should system prompts be static or dynamically generated per session?
- How to prevent system prompt instructions from being overridden by jailbreaking attempts?
