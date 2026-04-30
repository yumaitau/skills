---
name: portfolio-copywriter
description: Use this skill whenever writing, rewriting, expanding, or critiquing customer-facing copy for a marketing website, portfolio site, landing page, agency site, consultancy site, or service business website. Covers hero sections, about pages, service pages, project summaries, case studies, CTAs, headlines, taglines, SEO titles, meta descriptions, and URL slugs. Also use it for small jobs like shortening a headline, sharpening a tagline, writing a single project blurb, or giving feedback on existing copy. Produces grounded, specific, credible copy that avoids marketing theatre and preserves strong SEO fundamentals. Pairs with the human-copy-style skill for baseline voice.
---

# Portfolio Copywriter

Write like an experienced person who knows the work and respects the reader's time. The goal is to build trust, explain value clearly, and let the work do the selling.

Baseline voice and AI-tell avoidance are handled by the human-copy-style skill when available. This skill focuses on what that one does not cover: positioning, structure, proof, SEO, and the specific patterns marketing and portfolio pages need.

## Defaults

- Sound natural, specific, and confident.
- Keep claims proportional to the evidence.
- Prefer proof, examples, and concrete nouns over abstractions.
- Default to restrained marketing copy: capable, warm enough, never gushy.
- When expanding copy, add signal, not padding.
- Use Australian spelling when the repo already does.

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
- **Draft from scratch**: no existing copy. Ask interview questions first. Never fake a voice the brand hasn't established.

## Working Method

1. Read the existing page and surrounding site copy. Voice consistency matters.
2. Identify the page's job: attract, explain, prove, or convert.
3. Identify the search intent and likely keyword theme before rewriting.
4. Pull out the real material: audience, services, sectors, project names, geography, technical strengths, results, constraints, differentiators.
5. If the real material is thin, ask the user before drafting anything heavy.
6. Draft with a clear hierarchy: headline, support line, proof, CTA.
7. Tighten for rhythm. Cut anything that sounds rehearsed.
8. Produce SEO assets that match the rewritten page.

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
- Put the primary keyword or close variant in the H1, page title, and early body copy when it fits naturally.
- Use supporting variants in subheads and body copy without forcing exact-match repetition.
- Keep headings descriptive. They help readers and search engines alike.
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

- Cut filler and slogans.
- Replace vague adjectives with facts.
- Break up runs of long sentences.
- Shorten headings until they feel sharp.
- Check that keyword themes still appear naturally after editing.
- Make sure the SEO title and meta description reflect the strongest version of the page.
- Read the copy aloud once. If it sounds like marketing copy, simplify it again.

## Useful Language Bias

Verb lists are starting points, not rules. Match them to the industry.

- **Software and technical work**: build, ship, run, support, modernise, connect, deploy, maintain, design, deliver.
- **Design, content, and consultancy**: design, research, advise, document, facilitate, write, structure, plan, review.
- **Trades and service businesses**: install, fit, service, repair, supply, quote, schedule.

Prefer phrases like: "used in the field", "built for real-world use", "works across", "based in", "designed for", "supports", "helps".

## If The Brand Has Mission Or Identity Context

Handle it plainly and with respect. Do not turn identity, community, or purpose into decorative copy. State what is true, explain why it matters, move on.

## Locating Copy In The Repo

Before editing, find where the copy actually lives. Marketing and portfolio copy commonly sits in:

- Next.js / React: `src/app/**/page.tsx`, `app/**/page.tsx`, `src/content/*`, `content/*`
- Astro / MDX: `src/content/*.md(x)`, `src/pages/*.astro`
- Plain React / Vite: `src/pages/*`, `src/components/*`
- Eleventy / Hugo / Jekyll: `content/`, `src/site/`, `_posts/`

If you can't find the source file, grep for a distinctive phrase from the live page. For SEO metadata, also check page-level `metadata` exports, `<Head>` components, or frontmatter so titles and descriptions stay aligned with the rewritten body copy.

If the user has set up specific paths in a previous conversation or repo note, prefer those over these defaults.