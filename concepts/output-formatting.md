# Output Formatting (输出格式控制)

## Definition

Output formatting constrains how the model structures its response — requiring it to return data in a specific schema, language, or structural pattern. Formatting constraints turn free-form text into machine-readable output.

## Common Formats

### JSON
```
Respond in valid JSON matching this schema:
{
  "summary": "string (1-2 sentences)",
  "confidence": "number (0.0-1.0)",
  "reasoning": "string (why confidence is this value)"
}
```

### Structured Text
```
Format your response as:
## Summary
[one paragraph]

## Key Points
- [point 1]
- [point 2]
- [point 3]

## Next Steps
1. [action 1]
2. [action 2]
```

### Tables
```
Present as a markdown table:
| Criterion | Option A | Option B |
|-----------|----------|----------|
| Speed | Fast | Slow |
| Cost | Low | High |
```

### Code Blocks
```
Return as a code block with language tag:
```python
# code here
```
```

### Separators
```
Format as:
TITLE: [title]
DATE: [date]
BODY: [content]
---
```

## Enforcement Mechanisms

### 1. Implicit (Prompt)
Rely on the model to comply with format instructions. Works well but model can drift.

### 2. Grammar/Regex Constraints
Tools like `outlines`, `guidance`, or `instructor` use constrained decoding to force valid output:

```python
from outlines import models, generate, json

model = models.openai("gpt-4o")
schema = {"name": str, "age": int}
output = generate.json(model, schema)("Generate a person.")
```

### 3. Post-Processing
Prompt for format, then parse and validate. Re-prompt if invalid.

## Formatting + Few-Shot

Combines well with few-shot — show the format in examples:

```
Example response:
```json
{"action": "retry", "reason": "timeout"}
```

Example response:
```json
{"action": "escalate", "reason": "permission denied"}
```
```

## Relationship to Other Concepts

- [[prompting]] — Output formatting is a sub-discipline of prompting
- [[few-shot]] — Few-shot examples are often used to teach output format
- [[chain-of-thought]] — Format constraints can coexist with reasoning steps

## Common Failure Modes

| Failure | Cause | Fix |
|---------|-------|-----|
| JSON invalid | Model hallucinated comma or bracket | Use constrained decoding |
| Wrong schema keys | Unclear schema definition | Provide exact key names and types |
| Format drift | Long response, model forgets | Remind mid-generation |
| Language mix | Multi-lingual context | Explicitly state output language |

## Open Questions

- When is implicit prompting sufficient vs. when should constrained decoding be used?
- How to balance format strictness with the model's ability to reason?
- Can format constraints be combined with CoT, or do they interfere?
