---
name: portfolio-copywriter
description: Use this skill whenever writing or rewriting customer-facing copy for a marketing website, portfolio site, landing page, agency site, consultancy site, or service business website. Covers hero sections, about pages, service pages, project summaries, case studies, CTAs, headlines, taglines, SEO titles, and meta descriptions. Produces natural, human-sounding copy that feels grounded, specific, and credible, while making meaningful content improvements and preserving strong SEO fundamentals.
---

# Portfolio Copywriter

Write like an experienced person who knows the work and respects the reader's time. The goal is to build trust, explain value clearly, and let the work do the selling.

## Defaults

- Sound natural, specific, and confident.
- Keep the tone grounded. No startup theatre.
- Use plain language and real details.
- Prefer proof, examples, and concrete nouns over abstractions.
- Default to restrained marketing copy: capable, warm enough, never gushy.
- When expanding copy, add signal, not padding.
- Keep claims proportional to the evidence available.
- Use Australian spelling when the repo already does.

## What To Avoid

- Em dashes, emojis, and polished AI phrasing.
- Generic hype like "cutting-edge", "innovative", "robust", "seamless", "world-class", or "tailored solutions".
- Empty agency lines like "we turn ideas into reality" or "your trusted digital partner".
- Long openings that delay the point.
- Claims that could belong to any business.
- Keyword stuffing and obvious SEO filler.
- Expansion that only repeats the same point in longer form.

## Working Method

1. Read the existing page or surrounding site copy first.
2. Identify the page's job: attract, explain, prove, or convert.
3. Identify the search intent and likely keyword theme before rewriting.
4. Pull out the real material: audience, services, sectors, project names, geography, technical strengths, results, constraints, and differentiators.
5. Draft with a clear hierarchy: headline, support line, proof, CTA.
6. Tighten for rhythm and cut anything that sounds rehearsed.
7. Produce SEO assets that match the rewritten page.
8. If facts are thin, simplify the copy instead of inflating it.

## Meaningful Expansion

When asked to expand copy, do not just make it longer. Expand by adding:

- clearer positioning
- stronger proof points
- better explanation of the service, audience, or use case
- concrete delivery context, such as sectors, platforms, environments, or constraints
- sharper transitions between headline, body copy, and CTA

Good expansion improves depth, clarity, and relevance. If a new sentence does not add information, remove it.

## SEO Guardrails

- Write for humans first, but keep the primary keyword theme visible in the page.
- Preserve the page's core topic and intent unless the user asks to reposition it.
- Put the primary keyword or close variant in the H1, page title, and early body copy when it fits naturally.
- Use supporting variants in subheads and body copy without forcing exact-match repetition.
- Keep headings descriptive. They should help both readers and search engines understand the page.
- Maintain internal consistency between hero copy, page title, meta description, and CTA.
- Keep metadata specific to the page, not the brand in general.
- If the site already has strong topical terms, keep them unless there is a clear reason to change them.
- Never trade readability for density.

## SEO Outputs

When rewriting or expanding a page, default to providing:

- revised on-page copy
- SEO title
- meta description
- suggested H1 if the page needs one
- suggested supporting headings if the structure is weak

If relevant, also suggest:

- internal link opportunities
- a cleaner URL slug
- missing proof points or FAQs that would strengthen topical depth

## Tone For Marketing And Portfolio Sites

- Lead with what the company does and why it matters.
- Show credibility through work, sectors, delivery context, or named examples.
- Write like someone who has shipped real projects, not like a brand strategist performing confidence.
- Let portfolio copy feel observed and factual. A project blurb should sound earned.
- Keep CTAs low-friction and direct.

## Page Patterns

### Hero

- Use one clear positioning line.
- Add one support sentence with scope, audience, or differentiator.
- Give the reader one obvious CTA.
- Make sure the primary topic is obvious without sounding stuffed.

Good hero copy is short enough to scan and strong enough to remember.

### About

- Explain who the company is.
- Add credible background or perspective.
- Say why the company exists, without sounding self-important.

### Services

- Start with the outcome or problem solved.
- Mention the kind of work delivered.
- Add proof: sectors, systems, environments, platforms, or constraints.
- Keep jargon only where it helps credibility.
- Expand by adding useful detail, not by stacking generic benefits.

### Projects And Portfolio

- Say what the project is in plain English.
- Mention who it serves or why it matters.
- Highlight scale, complexity, or distinctiveness only if true.
- Avoid writing every project like a press release.
- Add searchable context such as industry, platform, delivery environment, or type of system when it helps discovery.

### CTA And Contact

- Keep the ask simple.
- Avoid fake urgency.
- Make it easy for a serious buyer to take the next step.

## Repo Notes

In this codebase, marketing and portfolio copy usually lives in:

- `src/app/page.tsx` for homepage hero, about, and section copy.
- `src/content/services.ts` for service summaries and long-form service descriptions.
- `src/content/projects.ts` for project blurbs and portfolio summaries.

Read those files before adding new copy so the voice stays consistent across the site.

For SEO-related updates, also check page-level metadata in `src/app/**/page.tsx` so titles and descriptions stay aligned with the rewritten copy.

## Rewrite Pass

- Cut filler and slogans.
- Replace vague adjectives with facts.
- Break up runs of long sentences.
- Shorten headings until they feel sharp.
- Check that important keyword themes still appear naturally after editing.
- Make sure the SEO title and meta description reflect the strongest version of the page.
- Read the copy out loud once. If it sounds like marketing copy, simplify it again.

## Useful Language Bias

Prefer verbs like: build, ship, run, support, modernise, connect, deploy, maintain, design, deliver.

Prefer phrases like: "used in the field", "built for real-world use", "works across", "based in", "designed for", "supports", and "helps".

## If The Brand Has Mission Or Identity Context

Handle it plainly and with respect. Do not turn identity, community, or purpose into decorative copy. State what is true, explain why it matters, and move on.
