# Skill Vetting (技能审核)

## Definition

Skill vetting is the process of reviewing a skill before loading it — checking for accuracy, security issues, outdated information, and quality standards. Given that skills can come from external sources (hub, community), vetting prevents bad skills from polluting the agent's behavior.

## When to Vet

- Installing a skill from the hub (`hermes skills install`)
- Before creating a new skill based on a third-party source
- When a skill's source material may have changed
- Before delegating to an unfamiliar skill

## Vetting Checklist

### Security
- [ ] Does the skill request any unusual permissions?
- [ ] Does it reference external APIs that could leak data?
- [ ] Are there `requires_env` declarations for sensitive env vars?
- [ ] Does it have a `check_fn` to verify prerequisites?

### Accuracy
- [ ] Are commands/paths verified for the current OS/environment?
- [ ] Are API endpoints current?
- [ ] Are version numbers accurate?
- [ ] Any contradictions with established skills?

### Quality
- [ ] Does it have frontmatter with `name` and `description`?
- [ ] Does it have a "Pitfalls" section?
- [ ] Does it have at least 2 outbound `[[wikilinks]]`?
- [ ] Is the trigger condition ("When to Use") clear?
- [ ] Are tags consistent with the taxonomy in SCHEMA.md?

### Completeness
- [ ] Are all steps numbered and actionable?
- [ ] Is the "Verify" step present?
- [ ] Does it cover error cases?

## Automated Vetting (Hermes Pattern)

The `skill-vetter` skill in this environment provides automated checks. See `~/.hermes/skills/openclaw-imports/skill-vetter/`.

## Source Verification

For skills derived from external sources:
1. Check the source URL/content is still accessible
2. Verify the skill hasn't diverged from its source
3. Note any customizations made for this environment
4. Log source attribution in the skill's `sources` frontmatter

## Open Questions

- Should there be a formal approval process before skills enter the hub?
- How to handle skills that work in one context but not another (e.g., OS differences)?
- Can agents autonomously vet and update skills, or does it require human oversight?
