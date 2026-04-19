# Chain-of-Thought (CoT, 思维链)

## Definition

Chain-of-Thought prompting asks the model to explicitly generate reasoning steps before giving the final answer. Instead of "Input → Output", it becomes "Input → Reasoning → Output".

The key insight: forcing the model to articulate intermediate steps improves accuracy on complex reasoning tasks, even without explicit reasoning training.

## Mechanism

```
Standard:
Q: If 3 cats have 4 kittens each, how many kittens total?
A: 12

Chain-of-Thought:
Q: If 3 cats have 4 kittens each, how many kittens total?
A: Each cat has 4 kittens. There are 3 cats. So 3 × 4 = 12.
The answer is 12.
```

## Variants

### 1. Zero-Shot CoT
```
Q: [question]
A: Let's think step by step.
```
No examples needed — the phrase "Let's think step by step" triggers structured reasoning.

### 2. Few-Shot CoT
```
Q: [example 1 with reasoning]
A: [answer]
Q: [example 2 with reasoning]
A: [answer]
Q: [actual question]
A: [reasoning → answer]
```
Examples condition the model to produce reasoning in the expected format.

### 3. Self-Consistency (CoT + Sampling)
Generate multiple reasoning paths, take the majority vote. Improves robustness:
```
Run CoT N times → Get N answers → Return most common answer
```

### 4. Tree-of-Thought (ToT)
```
        Question
       /    |    \
     Path A Path B Path C
      ↓       ↓       ↓
   Answer   Answer   Answer
      → Majority vote →
```
Explores multiple reasoning branches simultaneously.

## When CoT Helps

- Multi-step arithmetic
- Logical deduction
- Commonsense reasoning
- Code debugging / understanding
- Any task where the answer depends on intermediate conclusions

## When CoT Hurts

- Simple factual recall ("What is the capital of France?")
- Tasks where reasoning introduces opportunities for error
- Very short, constrained outputs
- Tasks the model already handles correctly

## Relationship to Other Concepts

- [[self-reflection]] — Reflection is "second-order" CoT: reasoning about reasoning
- [[prompting]] — CoT is one specific prompting technique
- [[few-shot]] — CoT often uses few-shot examples
- [[error-recovery]] — CoT failures can trigger reflection to identify where reasoning broke down

## Open Questions

- Does CoT always improve accuracy, or does it sometimes make things worse by letting errors accumulate in reasoning?
- How to detect when CoT is going off track before the final answer is produced?
- Is CoT reasoning genuine reasoning or sophisticated pattern matching?
