# Skill (技能系统)

## Definition

A skill is a reusable, documented knowledge module that an AI agent can load on demand to handle a specific task type or domain. Skills in Hermes are stored as markdown files in `~/.hermes/skills/`, each containing:

- **Metadata** — name, description, version, author, tags (YAML frontmatter)
- **Content** — instructions, patterns, commands, pitfalls, references
- **Optional linked files** — scripts, templates, reference docs

Currently 74 skills installed in this environment.

## Skill Anatomy

```yaml
---
name: skill-name
description: One-line description of what this skill covers
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [tag1, tag2]
    related_skills: [other-skill]
---

# Skill Title

## Overview
What this skill does and when to use it.

## Key Concepts
...

## Step-by-Step
...

## Pitfalls
...
```

## Relationship to Other Concepts

- [[skill-management]] — Skills are created, updated, and maintained through management
- [[skill-acquisition]] — Skill acquisition is the process of building new skills
- [[agent-memory]] — Skills are a form of procedural memory (compiled from repeated success)
- [[prompting]] — Skills encode prompting patterns and instructions

## Skill vs Other Knowledge Forms

| Form | Persistence | Update Frequency | Scope |
|------|-------------|-----------------|-------|
| System prompt | Per-session | Rare | Global |
| Context window | Per-turn | Every turn | Current task |
| Memory | Cross-session | Every session | Facts/preferences |
| **Skill** | Permanent | On-demand | Task patterns/procedures |
| Fine-tuned weights | Permanent | Expensive | Stable capabilities |

## Hermes Skill Ecosystem

- **74 skills** currently installed
- Categories: `devops`, `mlops`, `data-science`, `github`, `research`, `media`, `software-development`, `autonomous-ai-agents`, etc.
- Skill discovery: `hermes skills list`, `hermes skills search QUERY`
- Skill loading: `/skill <name>` in session or `skill_view(name)` tool call
- Publishing: `hermes skills publish PATH` to share via skills hub
