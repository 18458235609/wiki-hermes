# Role-Playing (角色扮演)

## Definition

Role-playing prompting assigns the agent a specific identity, expertise, or perspective. It frames the interaction as the agent "being" someone — a persona that shapes how it interprets requests and formulates responses.

## Common Role Patterns

### Expert Persona
```
You are a senior [profession] with 20 years of experience in [domain].
Your expertise is [specific skill]. You are known for [trait].
```

### Critique / Reviewer
```
You are a [role] reviewing [artifact]. Your job is to find weaknesses.
Be specific, be harsh, be constructive.
```

### Socratic Teacher
```
You are a Socratic tutor. Never give the answer directly.
Always respond with a question that guides the student to reason through it.
```

### Character / Persona
```
You are [character] from [source].
You speak in their voice, with their mannerisms and knowledge.
```

## Why Role-Playing Works

1. **Focuses context** — the role narrows the space of valid responses
2. **Sets tone/style** — different roles demand different communication styles
3. **Encodes expertise** — the role brings embedded knowledge of the domain
4. **Creates psychological distance** — easier to give harsh feedback "as a reviewer"

## Role Composition

Roles can be layered:

```
You are a senior software architect.
You specialize in distributed systems at scale.
You are reviewing this design from a reliability perspective.
```

Each layer adds:
- Breadth (architect)
- Depth (distributed systems)
- Lens (reliability)

## Role Constraints

Roles can also constrain behavior:

```
You are a security-focused engineer.
Never suggest patterns that could introduce vulnerabilities.
Always flag potential security concerns.
```

## Relationship to Other Concepts

- [[prompting]] — Role-playing is a prompting technique
- [[system-prompt]] — System prompt often defines the agent's primary role
- [[few-shot]] — Role + few-shot = examples in the character's voice
- [[chain-of-thought]] — Can use "As a [role], my reasoning is..." to apply domain reasoning

## Risks

- **Role drift** — agent gradually forgets or softens the role
- **Stereotyping** — roles can encode biases
- **Contradicting core capabilities** — a role may ask the model to do things it's not capable of
- **Jailbreaking** — "role-play" frames can sometimes be used to bypass safety guidelines

## Open Questions

- How to maintain role consistency over long conversations?
- Can roles be dynamically switched mid-conversation without confusion?
- Is explicit role assignment better than implicit framing ("As an expert...")?
