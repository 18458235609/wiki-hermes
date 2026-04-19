# Skill Loading (技能加载机制)

## Definition

Skill loading is the runtime process by which a skill's content is retrieved and injected into the agent's context so it can use the skill's knowledge during task execution.

## How Hermes Loads Skills

### Via tool (skill_view)
```python
skill_view(name="skill-name")
```
Returns the skill's SKILL.md content plus any linked files.

### Via session command
```
/skill skill-name
```
Loads the skill into the current session context.

### Via CLI preload
```
hermes -s skill1,skill2
```
Preloads skills before the session starts.

### Via cron job
```python
cronjob(action='create', skills=['skill-name'], prompt='...')
```
Loads skills when the scheduled job runs.

## What Happens During Loading

When `skill_view(name)` is called:

1. **Lookup** — Search `~/.hermes/skills/` for the named skill directory
2. **Read SKILL.md** — Parse frontmatter and content
3. **Resolve linked files** — Any files referenced in `linked_files` dict
4. **Return** — Full skill content injected into agent context

## Skill Frontmatter Schema

```yaml
---
name: skill-name           # Unique identifier (lowercase, hyphens)
description: "What this skill covers in one line"
version: 1.0.0            # Semantic version
author: Name              # Who created it
license: MIT              # License
metadata:
  hermes:
    tags: [tag1, tag2]   # Discovery tags
    related_skills: [other-skill]  # Cross-reference
    category: domain     # Optional category grouping
    config:              # Optional skill-specific config schema
      - key: config.key
        description: what this config does
        default: default-value
---

# Content
```

## Relationship to Other Concepts

- [[skill]] — The skill loading mechanism is how [[skill]]s are accessed at runtime
- [[skill-management]] — Loading is the runtime phase of the skill lifecycle
- [[agent-memory]] — Both skill loading and memory inject information into context, but skills are permanent/demand vs. memory is automatic/cross-session
- [[prompting]] — Skill content is essentially prompting templates + procedural knowledge

## Performance Considerations

- Skills are loaded on demand, not preloaded into every session (unless explicitly preloaded)
- Skill content competes for context window space
- Large skills should be split or have their detailed reference material in linked files
- The agent pre-loads skill skill_view into context before tool execution (from hermes-agent skill)

## Lazy Loading Pattern

Best practice: load skills only when needed, not preemptively. The agent should:
1. Encounter a task that matches a skill trigger condition
2. Call `skill_view(name)` to load
3. Follow the skill's instructions
4. Not load skills "just in case"

This avoids context bloat and ensures the right skill fires for the right task.
