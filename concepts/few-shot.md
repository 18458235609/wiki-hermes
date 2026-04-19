# Few-Shot Prompting

## Definition

Few-shot prompting provides 2-5 examples of input-output pairs in the prompt, allowing the model to infer the pattern without explicit instruction. The examples "show" the task rather than "tell" it.

## Format

```
Example 1:
Input: [input text]
Output: [output text]

Example 2:
Input: [input text]
Output: [output text]

Example 3:
Input: [input text]
Output: [output text]

Now do this:
Input: [actual input]
Output:
```

## Why It Works

Language models are strong pattern matchers. Examples:
- Demonstrate the output format
- Clarify domain-specific conventions
- Show edge cases and how to handle them
- Set the style/tone of the response

## Example Use Cases

### Translation
```
Example:
English: "Hello"
French: "Bonjour"

English: "Thank you"
French: "Merci"

English: "Good morning"
French:
```

### Classification
```
Example:
Text: "Just finished an amazing workout!"
Sentiment: Positive

Text: "This is taking forever..."
Sentiment: Negative

Text: "The meeting is at 3pm"
Sentiment: Neutral

Text: "Can't believe they cancelled"
Sentiment:
```

### Data extraction
```
Example:
Text: "John Doe, CEO of Acme Inc, born 1985"
JSON: {"name": "John Doe", "title": "CEO", "company": "Acme Inc", "year_of_birth": 1985}

Text: "Jane Smith, CTO at TechCo, 1990"
JSON:
```

## Key Design Decisions

### Number of Examples
- 2-3 examples usually sufficient
- More examples help with edge cases but consume context
- Diminishing returns beyond 5

### Diversity
- Examples should cover the range of input types
- Include at least one edge case
- Avoid examples that are too similar to each other

### Order
- Order from simple to complex → model builds confidence
- Order from complex to simple → model gets context first
- Randomize if there's no natural progression

## Relationship to Other Concepts

- [[prompting]] — Few-shot is a specific prompting technique
- [[chain-of-thought]] — CoT can be combined with few-shot (few-shot CoT)
- [[output-formatting]] — Few-shot is often used to teach output format

## Limitations

- Examples consume significant context window
- Quality of examples directly affects quality of output
- Hard to cover all edge cases in examples
- Works better for some tasks (format) than others (novel reasoning)

## Open Questions

- Is few-shot learning genuine generalization or just retrieval from context?
- How to select the minimum set of examples that covers the task?
- Can the model learn from examples it generated itself (self-taught few-shot)?
