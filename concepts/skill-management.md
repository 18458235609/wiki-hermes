# Skill Management (技能管理)

## Definition

Skill management is the practice of creating, maintaining, updating, vetting, and organizing skills over time. It covers the full lifecycle from identifying a need to archiving obsolete skills.

## The Skill Lifecycle

```
Identify → Capture → Test → Load → Maintain → (Archive)
```

### 1. Identify
Notice a recurring task pattern that would benefit from a skill:
- Same complex workflow repeated 3+ times
- A correction or workaround discovered during work
- A new tool or API the agent should know about

### 2. Capture
Codify the knowledge into a SKILL.md file:

```yaml
---
name: new-skill
description: Brief description
---

# Title

## When to Use
...

## Steps
...

## Pitfalls
...
```

Best practices:
- Frontmatter must include `name`, `description`
- Include `related_skills` tags to enable discovery
- Write actionable steps, not abstract principles
- Add a "Pitfalls" section with real gotchas

### 3. Test
Verify the skill works before committing:
- Load it: `/skill new-skill`
- Try it on a real task
- If it fails, patch and retry

### 4. Load
Skills load via:
- Session: `/skill <name>` or `skill_view(name)`
- Cron: pass `skills=[skill-name]` on job creation
- Preload: `hermes -s skill1,skill2`

### 5. Maintain
When to update a skill:
- Found a better approach
- A tool/API changed
- User corrected the agent's approach
- New pitfalls discovered

### 6. Archive
When a skill is fully superseded:
- Move to `_archive/` subdirectory
- Update index.md to remove or mark as archived
- Keep for reference but don't load

## Skill Quality Guidelines

From this environment's experience:

| Dimension | Good | Bad |
|-----------|------|-----|
| Trigger | Clear "when to use" | Vague description |
| Steps | Numbered, concrete | Abstract principles |
| Pitfalls | Real gotchas with fixes | Generic warnings |
| Links | Related skills/pages | No cross-references |
| Scope | One coherent topic | Trying to cover everything |

## Skill Vetting

Before loading an unfamiliar skill, check:
1. Does it have frontmatter with `name` and `description`?
2. Are tags relevant to the current task?
3. Does it have a "Pitfalls" section?
4. Does it link to at least 2 related skills/concepts?

See [[skill-vetter]] for automated security vetting workflow.

## Skill Organization

Skills live in `~/.hermes/skills/`:
- Top-level: general categories (74 skills)
- Subdirectories: skills with multiple files (e.g., `software-development/` has `plan/`, `systematic-debugging/`, etc.)
- Skills with linked files have subdirectories under them

## Open Questions

- What is the right skill granularity? (1 skill per micro-task vs. 1 skill per domain?)
- How to handle conflicting skills for the same task?
- When does a skill need to become a tool vs. stay a skill?
