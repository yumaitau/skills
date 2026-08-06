# Yuma IT Skills

Public collection of agent skills used internally by Yuma IT.

This repository contains focused instructions that help our AI coding assistants handle repeatable work in a consistent way. The skills are published publicly for reference, but they are written for Yuma IT's internal workflows. Each folder is a standalone skill, with its behaviour defined in a `SKILL.md` file.

## Skills

### `australian-english`

Enforces Australian English in all prose output: documentation, READMEs, changelogs, UI text, emails, reports, code comments, and commit messages. Defines the tricky noun/verb pairs (licence/license, practice/practise, program/programme) and the hard boundary that code identifiers, API names, package names, and conventional filenames like `LICENSE` always keep their original spelling.

Use it whenever writing or editing prose for an Australian audience or team. The copy skills below already require Australian spelling for customer-facing copy; this skill defines the detail and extends the default to everything else, including developer-facing writing.

### `human-copy-style`

Baseline copy style for customer-facing writing. It keeps copy plainspoken, specific, and human, with Australian spelling and guardrails against common AI tells such as generic hype, filler transitions, emojis, em dashes, and over-polished phrasing.

Use it for marketing copy, UI microcopy, emails, landing pages, product descriptions, taglines, blog posts, social posts, and announcements. For website page copy it pairs with `portfolio-copywriter`, which owns positioning, structure, and SEO while this skill owns voice. Not for developer documentation or legal wording.

### `portfolio-copywriter`

Copywriting guidance for portfolio sites, marketing websites, landing pages, agency sites, consultancy sites, and service business websites. It focuses on positioning, proof, structure, SEO fundamentals, and credible page-level copy, and reads `.product/` knowledge files from `dot-product` when they exist.

Use it for hero sections, about pages, service pages, project summaries, case studies, CTAs, headlines, SEO titles, meta descriptions, and URL slugs.

### `dot-product`

Analyses an existing codebase and produces a `.product/` folder of sales-oriented knowledge files: overview, features, use cases, personas, integrations, differentiators, technical profile, limitations, glossary, and a structured `product-profile.json`.

Use it to bootstrap product knowledge for sales reps, demo builders, and AI sales agents — and as the upstream input to `portfolio-copywriter` and `human-copy-style` for downstream copy work.

### `laravel-gate-audit`

Audits Laravel applications for gate and policy usage, then compares referenced abilities against `Gate::define`, `Gate::resource`, policy mappings, policy methods, and authorization hooks.

Use it to find missing gate definitions, undefined policy methods, ability typos, suspicious model/ability mismatches, and dynamic authorization checks that need manual confirmation.

## Repository Structure

```text
skills/
  australian-english/
    SKILL.md
  human-copy-style/
    SKILL.md
  portfolio-copywriter/
    SKILL.md
  dot-product/
    SKILL.md
    references/
      product-profile-schema.md
      translation-patterns.md
  laravel-gate-audit/
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
