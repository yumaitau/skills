---
name: portfolio-copywriter
description: Positioning, structure, proof, and SEO for customer-facing website copy. Use whenever writing, rewriting, expanding, or critiquing copy for a portfolio, marketing, landing, agency, consultancy, or service business site, covering heroes, about pages, service pages, project summaries, case studies, CTAs, headlines, taglines, SEO titles, meta descriptions, and URL slugs. Trigger even for small jobs like shortening a headline or reviewing a single project blurb. Reads `.product/` knowledge files from the dot-product skill when present, and pairs with human-copy-style for baseline voice. Not for marketing emails, newsletters, announcements, social posts, or ad copy, which campaign-copywriter owns, and not for blog posts or UI microcopy with no page-level SEO job, which human-copy-style alone covers.
---

# Portfolio Copywriter

Write like an experienced person who knows the work and respects the reader's time. Build trust, explain value clearly, and let the work do the selling. Default to restrained marketing copy: capable, warm enough, never gushy.

This skill owns positioning, structure, proof, SEO, and page-level patterns. Baseline voice and AI-tell avoidance belong to the `human-copy-style` skill. If that skill is not installed, hold its core line yourself: plain verbs over buzzwords, no em dashes or emojis, no generic hype, varied sentence rhythm, Australian spelling.

## Source Material

Real material beats invention, so gather it before drafting:

1. If `.product/` exists at the repository root (output of the `dot-product` skill), read `OVERVIEW.md`, `FEATURES.md`, `DIFFERENTIATORS.md`, and `USE_CASES.md` first. It is pre-mined, code-grounded proof material, which is exactly what this skill needs. `product-profile.json` holds the same facts structured. If the copy job is large and `.product/` is missing, suggest running `dot-product` first.
2. Read the existing page and the surrounding site copy. Voice consistency matters, and pages already make claims you must not contradict.
3. Ask the user for anything load-bearing that neither source provides.

You are done gathering when every claim you plan to make traces to a source or to a question you have asked.

## Never Invent

Copywriting is where hallucination does the most damage, because users often cannot tell from a draft what is real. Rules:

- Never invent clients, projects, case studies, sectors served, awards, testimonials, headcount, years in operation, locations, or partnerships.
- Never invent metrics. "Faster checkout" is better than "43% faster checkout" if you don't know the number.
- Never attribute quotes to anyone.
- If a strong line depends on a fact you don't have, either ask the user for it or write a weaker line that is true.
- If source material is thin, simplify the copy. Do not inflate it.

When you're unsure whether a detail is real, flag it inline like `[check: 15+ years?]` so the user can verify before shipping.

## Three Modes Of Work

Be clear on which mode you're in before drafting.

- **Rewrite**: keep the same information, make it sharper. Don't change what the page claims, just how it says it.
- **Expand**: the page is too thin. Add real detail, not padding. If you can't add signal, don't expand.
- **Draft from scratch**: no existing copy. Interview the user before drafting. Minimum set: who the site serves and the one action a visitor should take; the services or products offered, and which they want more of; provable facts (sectors, locations, years in operation, team size, results, clients they can name publicly); what makes them different from the next search result; geographic scope and any known keyword targets. Never fake a voice the brand hasn't established.

## Working Method

1. Establish the mode: rewrite, expand, or draft from scratch.
2. Gather source material as above.
3. Identify the page's job (attract, explain, prove, or convert) and its search intent and keyword theme.
4. Draft with a clear hierarchy: headline, support line, proof, CTA.
5. Run the rewrite pass below.
6. Produce the SEO outputs below. Done when the SEO title, meta description, and H1 all reflect the final copy, not the draft.

## Meaningful Expansion

When expanding, add:

- clearer positioning
- stronger proof points
- better explanation of the service, audience, or use case
- concrete delivery context: sectors, platforms, environments, constraints
- sharper transitions between headline, body copy, and CTA

Expansion that repeats the same point in longer form is a failure mode, not a style. If a new sentence doesn't add information, remove it.

## SEO Guardrails

- Write for humans first, but keep the primary keyword theme visible.
- Preserve the page's topic and intent unless the user asks to reposition it.
- Put the primary keyword or a close variant in the H1, page title, and early body copy when it fits naturally.
- Use supporting variants in subheads and body copy without forcing exact-match repetition.
- Keep metadata specific to the page, not the brand in general.
- Never trade readability for density.

## SEO Outputs

When rewriting or expanding a page, default to providing:

- revised on-page copy
- SEO title (aim for 55 to 60 characters)
- meta description (aim for 150 to 160 characters)
- suggested H1 if the page needs one
- suggested supporting headings if the structure is weak

If relevant, also suggest:

- internal link opportunities
- a cleaner URL slug
- missing proof points or FAQs that would strengthen topical depth

## Page Patterns

### Hero

- One clear positioning line.
- One support sentence with scope, audience, or differentiator.
- One obvious CTA.
- Primary topic obvious without sounding stuffed.

**Example rewrite:**

Before:

> Welcome to Rivercroft Digital, your trusted partner for cutting-edge, tailored solutions that drive real results in today's fast-paced digital landscape.

After:

> Rivercroft builds websites and internal tools for Victorian councils and utilities.
> Small team, long engagements, code that outlasts us.
> [Start a project]

The "after" tells you who they serve, what they build, and how they work. The "before" could belong to any agency in any country.

### About

- Explain who the company is.
- Add credible background or perspective.
- Say why the company exists, without sounding self-important.

### Services

- Start with the outcome or problem solved.
- Name the kind of work delivered.
- Add proof: sectors, systems, environments, platforms, constraints.
- Keep jargon only where it helps credibility.

**Example rewrite:**

Before:

> We offer robust, end-to-end web development solutions tailored to your business needs.

After:

> We build public-facing websites for regulated sectors: water authorities, councils, health networks. Accessibility, long-term maintenance, and content governance are part of the default scope, not extras.

### Projects And Portfolio

- Say what the project is in plain English.
- Mention who it serves or why it matters.
- Highlight scale, complexity, or distinctiveness only if true.
- Avoid writing every project like a press release.
- Add searchable context: industry, platform, delivery environment, system type.

**Example blurb:**

> Rebuilt the booking system for a regional hospital network serving 140,000 patients across six sites. Moved them off a legacy PHP monolith onto a typed Node stack, kept the existing appointment data, and shipped the cutover in a single overnight window.

The reader learns what it is, who it serves, and why it was hard, without adjectives.

### CTA And Contact

- Keep the ask simple.
- Avoid fake urgency.
- Match the CTA to buyer intent.

**Examples:**

Weak: "Take your business to the next level today!"

Stronger: "Start a project", "Book a 20-minute call", "See pricing", "Get in touch about NSW work".

The strong versions tell the reader exactly what happens when they click.

## Rewrite Pass

Voice-level editing (filler, buzzwords, rhythm) is `human-copy-style`'s rewrite pass. This one is about proof and search:

- Replace vague adjectives with facts from the source material.
- Shorten headings until they feel sharp.
- Check the keyword theme survived the edit. Restore it naturally if it didn't.
- Make sure the SEO title and meta description reflect the strongest version of the page.
- Read the copy aloud once. If it still sounds like marketing copy, simplify it again.

## Useful Language Bias

Verb lists are starting points, not rules. Match them to the industry.

- **Software and technical work**: build, ship, run, support, modernise, connect, deploy, maintain, design, deliver.
- **Design, content, and consultancy**: design, research, advise, document, facilitate, write, structure, plan, review.
- **Trades and service businesses**: install, fit, service, repair, supply, quote, schedule.

Prefer phrases like: "used in the field", "works across", "based in", "supports".

## If The Brand Has Mission Or Identity Context

Handle it plainly and with respect. Do not turn identity, community, or purpose into decorative copy. State what is true, explain why it matters, move on.

## Locating Copy In The Repo

Before editing, find where the copy actually lives. Marketing and portfolio copy commonly sits in:

- Next.js / React: `src/app/**/page.tsx`, `app/**/page.tsx`, `src/content/*`, `content/*`
- Astro / MDX: `src/content/*.md(x)`, `src/pages/*.astro`
- Plain React / Vite: `src/pages/*`, `src/components/*`
- Eleventy / Hugo / Jekyll: `content/`, `src/site/`, `_posts/`

If you can't find the source file, grep for a distinctive phrase from the live page. For SEO metadata, also check page-level `metadata` exports, `Head` components, or frontmatter so titles and descriptions stay aligned with the rewritten body copy.

If the user has set up specific paths in a previous conversation or repo note, prefer those over these defaults.

## When NOT To Use

- Marketing emails, newsletters, announcements, social posts, and ad copy: `campaign-copywriter` owns structure and CTAs there, with `human-copy-style` on voice.
- Blog posts and UI microcopy with no page-level SEO job: `human-copy-style` alone covers those.
- Campaign planning, audience selection, or channel plans: that is `marketing-strategist`.
- Extracting product knowledge from a codebase: that is `dot-product`. Run it first, then come back here for the copy.
- Documentation written for developers (READMEs, API docs, changelogs): not marketing copy.
