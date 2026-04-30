# Yuma IT Skills

Public collection of agent skills used internally by Yuma IT.

This repository contains focused instructions that help our AI coding assistants handle repeatable work in a consistent way. The skills are published publicly for reference, but they are written for Yuma IT's internal workflows. Each folder is a standalone skill, with its behaviour defined in a `SKILL.md` file.

## Skills

### `human-copy-style`

Baseline copy style for customer-facing writing. It keeps copy plainspoken, specific, and human, with Australian spelling and guardrails against common AI tells such as generic hype, filler transitions, emojis, em dashes, and over-polished phrasing.

Use it for marketing copy, UI microcopy, emails, landing pages, product descriptions, taglines, blog posts, social posts, and announcements.

### `portfolio-copywriter`

Copywriting guidance for portfolio sites, marketing websites, landing pages, agency sites, consultancy sites, and service business websites. It focuses on positioning, proof, structure, SEO fundamentals, and credible page-level copy.

Use it for hero sections, about pages, service pages, project summaries, case studies, CTAs, headlines, SEO titles, meta descriptions, and URL slugs.

## Repository Structure

```text
skills/
  human-copy-style/
    SKILL.md
  portfolio-copywriter/
    SKILL.md
```

Each `SKILL.md` contains:

- YAML frontmatter with the skill `name` and `description`
- clear instructions for when the skill should be used
- practical rules, examples, and workflow guidance

## Adding A Skill

1. Create a new folder using a short kebab-case name.
2. Add a `SKILL.md` file inside it.
3. Start the file with frontmatter:

```yaml
---
name: your-skill-name
description: Use this skill when...
---
```

4. Write the skill instructions with concrete rules and examples.
5. Keep the description specific. Assistants use it to decide when the skill should load.

## Notes

- These skills are public, but maintained for Yuma IT's internal workflows.
- There is no build step.
- There are no runtime dependencies.
- Skills should stay focused on one repeatable workflow or area of judgement.
- Prefer specific guidance over broad style advice.
