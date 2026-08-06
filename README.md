# Yuma IT Skills

Public collection of agent skills used internally by Yuma IT.

This repository contains focused instructions that help our AI coding assistants handle repeatable work in a consistent way. The skills are published publicly for reference, but they are written for Yuma IT's internal workflows. Each folder is a standalone skill, with its behaviour defined in a `SKILL.md` file.

## Install

Skills install with the [Skills CLI](https://skills.sh), which needs Node 22.20 or newer. No clone required.

Pick skills interactively:

```bash
npx skills add yumaitau/skills
```

List what is in here without installing anything:

```bash
npx skills add yumaitau/skills -l
```

Install every skill, for every agent the CLI detects:

```bash
npx skills add yumaitau/skills --all
```

Install one skill globally, so it is available in every project:

```bash
npx skills add yumaitau/skills@human-copy-style -g
```

Generate a prompt that uses one skill, without installing it:

```bash
npx skills use yumaitau/skills@dot-product
```

Update installed skills later:

```bash
npx skills update
```

Project installs land in `.agents/skills/` and are symlinked into each agent's own directory, including `.claude/skills/` for Claude Code. Add `-g` to any command above to install at user level instead.

## Skills

### `australian-english`

Enforces Australian English in all prose output: documentation, READMEs, changelogs, UI text, emails, reports, code comments, and commit messages. Defines the tricky noun/verb pairs (licence/license, practice/practise, program/programme) and the hard boundary that code identifiers, API names, package names, and conventional filenames like `LICENSE` always keep their original spelling.

Use it whenever writing or editing prose for an Australian audience or team. The copy skills below already require Australian spelling for customer-facing copy; this skill defines the detail and extends the default to everything else, including developer-facing writing.

```bash
npx skills add yumaitau/skills@australian-english
```

### `human-copy-style`

Baseline copy style for customer-facing writing. It keeps copy plainspoken, specific, and human, with Australian spelling and guardrails against common AI tells such as generic hype, filler transitions, emojis, em dashes, and over-polished phrasing.

Use it for marketing copy, UI microcopy, emails, landing pages, product descriptions, taglines, blog posts, social posts, and announcements. For website page copy it pairs with `portfolio-copywriter`, and for campaign pieces with `campaign-copywriter`; those skills own structure while this one owns voice. Not for developer documentation or legal wording.

```bash
npx skills add yumaitau/skills@human-copy-style
```

### `portfolio-copywriter`

Copywriting guidance for portfolio sites, marketing websites, landing pages, agency sites, consultancy sites, and service business websites. It focuses on positioning, proof, structure, SEO fundamentals, and credible page-level copy, and reads `.product/` knowledge files from `dot-product` when they exist.

Use it for hero sections, about pages, service pages, project summaries, case studies, CTAs, headlines, SEO titles, meta descriptions, and URL slugs.

```bash
npx skills add yumaitau/skills@portfolio-copywriter
```

### `campaign-copywriter`

Structure, offers, CTAs, and channel patterns for standalone marketing pieces: marketing emails, newsletters, launch and release announcements, social posts, and ad copy, including subject lines, preview text, and email sequences. Reads `.product/` knowledge files from `dot-product`, consumes campaign briefs from `marketing-strategist`, and pairs with `human-copy-style` for voice.

Use it for anything sent or posted to an audience. Website pages stay with `portfolio-copywriter`.

```bash
npx skills add yumaitau/skills@campaign-copywriter
```

### `marketing-strategist`

Campaign planning and messaging strategy before any copy is written: campaign briefs, messaging frameworks, audience and channel selection, launch plans, and content calendars sized to the team's real capacity. Reads `.product/` knowledge files from `dot-product` and never invents market data or benchmarks.

Use it to decide the goal, audience, message, and channels, then hand the resulting brief to `campaign-copywriter` or `portfolio-copywriter` for the writing.

```bash
npx skills add yumaitau/skills@marketing-strategist
```

### `dot-product`

Analyses an existing codebase and produces a `.product/` folder of sales-oriented knowledge files: overview, features, use cases, personas, integrations, differentiators, technical profile, limitations, glossary, and a structured `product-profile.json`.

Use it to bootstrap product knowledge for sales reps, demo builders, and AI sales agents — and as the upstream input to `portfolio-copywriter`, `campaign-copywriter`, `marketing-strategist`, and `human-copy-style` for downstream copy and planning work.

```bash
npx skills add yumaitau/skills@dot-product
```

### `laravel-gate-audit`

Audits Laravel applications for gate and policy usage, then compares referenced abilities against `Gate::define`, `Gate::resource`, policy mappings, policy methods, and authorization hooks.

Use it to find missing gate definitions, undefined policy methods, ability typos, suspicious model/ability mismatches, and dynamic authorization checks that need manual confirmation.

```bash
npx skills add yumaitau/skills@laravel-gate-audit
```

## Repository Structure

```text
skills/
  australian-english/
    SKILL.md
  human-copy-style/
    SKILL.md
  portfolio-copywriter/
    SKILL.md
  campaign-copywriter/
    SKILL.md
  marketing-strategist/
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
