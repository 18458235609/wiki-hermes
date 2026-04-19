# Prompting (提示工程)

## Definition

Prompting is the practice of crafting inputs to an LLM to elicit desired outputs. In the context of Hermes-style agents, prompting encompasses:
- System prompts that define agent behavior
- Task prompts that direct specific actions
- Skill content that augments the prompt at runtime
- Output formatting constraints

## Prompting Techniques

### 1. Chain-of-Thought (CoT)
Ask the model to reason step by step before giving the final answer:
```
Solve this problem. First, identify what is being asked.
Second, determine what information is needed.
Third, work through the solution.
```

### 2. Few-Shot
Provide 2-5 examples of input-output pairs to illustrate the pattern:
```
Example 1:
Input: [input]
Output: [output]
Example 2:
Input: [input]
Output: [output]
Now do this:
Input: [new input]
```

### 3. System Prompt Engineering
Define agent identity and constraints in system prompt:
```
You are a [role] agent that specializes in [domain].
Always [behavior 1]. Never [behavior 2].
When [condition], do [action].
```

### 4. Role Playing
Assign the agent a specific persona:
```
You are a senior [profession] reviewing [artifact].
Your feedback should be [characteristics].
```

### 5. Output Formatting
Constrain output structure:
```
Respond in JSON format:
{"summary": "...", "confidence": 0.0-1.0, "reasoning": "..."}
```

### 6. Constraints
Explicitly state what the agent should NOT do:
```
Do not:
- Use method X (it fails when Y)
- Return raw SQL (always wrap in transactions)
```

## Relationship to Other Concepts

- [[skill]] — Skills are bundles of prompting patterns + procedural knowledge
- [[skill-loading]] — Skills are loaded into the prompt context at runtime
- [[self-reflection]] — Reflection prompts enable the agent to self-evaluate
- [[chain-of-thought]] — CoT is a specific prompting technique

## Hermes-Specific Prompting

Hermes adds:
- **Skills** — reusable prompt bundles that load dynamically
- **Memory** — persistent facts injected into context
- **System prompt** — defines agent-wide behavior
- **Platform-specific prompts** — different behaviors per messaging platform

## Open Questions

- When does prompting hit its ceiling vs. fine-tuning vs. skill modules?
- How to avoid prompt bloat as more skills are loaded?
- Can agents learn to improve their own prompting through experience?
