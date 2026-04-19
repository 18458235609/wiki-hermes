# The Self-Improving Agent Loop

## Question

How do all the self-improvement concepts connect? What creates the "flywheel" where agents get genuinely better over time?

## Synthesis

The self-improvement loop has four interconnected components:

```
1. Experience
   (task executed, result produced)
         ↓
2. Self-Reflection / Feedback
   (evaluate: what worked? what didn't?)
         ↓
3. Learning / Skill Update
   (encode lessons as skills, memory, or improved prompting)
         ↓
4. Next Task
   (applies updated knowledge → better results)
         ↓
      Experience (loop)
```

## Component Roles

### Experience (Context)
The agent encounters a task. Without prior knowledge, it solves it however it can.
This generates an outcome: success, failure, or partial success.

### Self-Reflection
After the experience, the agent asks:
- Did I succeed? Why or why not?
- Was there a more efficient approach?
- What pitfalls did I encounter?
- Would a different strategy have worked better?

This converts raw experience into interpreted data.

### Feedback Loop
External signals also feed back:
- User corrections ("actually do it this way")
- Tool return codes (success/failure)
- Task completion status
- Implicit signals (follow-up questions)

### Learning / Skill Update
Interpreted lessons get encoded:
- **Skills** — procedural knowledge (how to do X)
- **Memory** — factual knowledge (user prefers Y)
- **System prompt** — updated constraints/instructions
- **Prompting templates** — better patterns for next time

### Application
On the next similar task, the agent loads relevant skills/memory, avoiding previous mistakes and applying proven strategies.

## Flywheel Effect

Each loop doesn't just fix one mistake — it compounds:

```
Task 1: Learned skill X → Task 2: Uses skill X + learns skill Y
Task 3: Uses X + Y + learns Z → Task N: Uses accumulated X...Z
```

## Key Enablers

For the flywheel to work:
1. **Errors must be noticed** — self-reflection catches them
2. **Lessons must be encoded** — skills/memory captures them
3. **Context must persist** — skills load when relevant, memory survives sessions
4. **Old knowledge must apply** — skills are reusable, not one-off

## Relationship to Other Concepts

- [[self-reflection]] — Phase 2: evaluation
- [[feedback-loop]] — Phase 2: external signals
- [[learning-from-mistakes]] — Phase 3: encoding errors
- [[skill-acquisition]] — Phase 3: encoding successes
- [[agent-memory]] — Storage for lessons between sessions
- [[skill]] — The durable form of learned procedures

## Sources

Based on agentic AI literature (self-correction, reflective agents) and Hermes design patterns.
