---
name: human-copy-style
description: Use this skill whenever writing or editing any customer-facing copy, including marketing text, UI microcopy, emails, landing pages, product descriptions, taglines, blog posts, social posts, or announcements that should sound like a person wrote them. Trigger this even for short asks like "rewrite this product description," "tighten this," or "punch this up," and for any task where the output will be read by customers or prospects. Enforces plainspoken language, varied sentence rhythm, Australian spelling, and removal of common AI tells (em dashes, emojis, filler transitions, generic hype, triple-adjective chains, rule-of-three slogans, and hedged verbs). For website page copy it pairs with portfolio-copywriter, and for campaign pieces like emails, announcements, social posts, and ads with campaign-copywriter; those skills own positioning, structure, proof, and SEO while this skill owns voice. Not for developer documentation, code comments, or legal wording.
---

# Human Copy Style

Write like a person with taste and context, not a model trying to sound helpful.

This skill owns voice: word choice, rhythm, and the removal of AI tells. For portfolio, marketing, and service business websites, `portfolio-copywriter` owns positioning, structure, proof, and SEO; both skills apply to those pages. For marketing emails, announcements, social posts, and ads, `campaign-copywriter` owns structure, offers, and CTAs; both skills apply to those pieces too. `marketing-strategist` owns the planning upstream of any copy. `dot-product` supplies code-grounded product facts when a `.product/` folder exists — prefer its facts over inventing detail.

## Goals

- Sound direct, specific, and useful.
- Prefer concrete nouns and verbs over abstractions.
- Vary sentence length. Some should be short.
- Use contractions when they fit the voice.
- Cut throat-clearing, repeated framing, and summary fluff.
- Preserve the source voice if it already sounds human. Do not flatten a quirky, informal, or brand-specific tone into a neutral default.

## Avoid AI Tells

### Punctuation and symbols
- No em dashes. Use commas, periods, or parentheses instead. For ranges, use "to" or an en dash.
- No emojis. No decorative bullets or symbols.
- Exclamation marks should be rare.

### Filler and transitions
- Avoid "moreover," "furthermore," "in addition," "that said," "having said that."
- Avoid "it's worth noting," "it's important to note," "it goes without saying."
- Avoid "in today's fast-paced world," "gone are the days," "when it comes to."

### Generic hype and buzzwords
- Avoid "game-changing," "robust," "seamless," "cutting-edge," "next-level," "world-class," "best-in-class."
- Avoid "leverage," "unlock," "harness," "empower," "elevate," "transform," "journey," "navigate," "delve," "dive into."
- Avoid "truly," "genuinely," "simply" as intensifiers.

### Structural tics
- No "Not just X, but Y" or "It's not X, it's Y" frames.
- No symmetrical three-part slogans or triple-adjective chains like "clear, concise, and compelling."
- No "Whether you're X or Y..." openers.
- No generic openers like "Certainly," "Here is a polished version," or "I'd be happy to."
- No rhetorical-flourish closers like "The future is here" or "The rest is up to you."

### Hedging and softening
- Avoid "can help you," "may be able to," "designed to." Say what it does.
- Avoid empty warmth, fake encouragement, and corporate uplift.

## Style Rules

- Lead with the point.
- Keep paragraphs tight. Prefer one idea per sentence when clarity improves.
- Use specifics from the product, audience, or page. If a claim could apply to any business, rewrite it.
- Prose often beats a bulleted list in marketing copy. Only use bullets when the content is genuinely a list.
- Read for rhythm and remove lines that sound rehearsed.
- Keep punctuation simple.
- Use Australian English throughout. Defer spelling detail (licence/license, -ise/-our/-re, prose vs symbol boundary) to the `australian-english` skill.

## Before and After

Generic, AI-flavoured:
> Our seamless platform empowers teams to unlock their full potential. Whether you're a startup or enterprise, our cutting-edge tools help you navigate today's fast-paced business landscape — truly a game-changer.

Rewritten:
> A project tool for teams of four to forty. You'll set up your first board in about five minutes.

Generic:
> We're thrilled to announce our new dashboard! It's more robust, more intuitive, and more powerful than ever before.

Rewritten:
> The new dashboard is out. It loads in under a second, shows six months of data by default, and lets you save views.

Generic:
> Unlock the power of seamless collaboration with our innovative suite of tools designed to empower your team.

Rewritten:
> Shared docs, shared inbox, shared calendar. One login.

Generic:
> Whether you're a seasoned developer or just starting your coding journey, our platform has you covered.

Rewritten:
> Works the same on day one and year five. No tier gates, no surprise paywalls.

## Rewrite Pass

1. Cut filler, self-reference, and repeated setup.
2. Replace generic claims with concrete details from the brief or source.
3. Replace em dashes with commas, periods, or parentheses. Remove emojis.
4. Swap buzzwords (leverage, unlock, seamless, robust) for plain verbs.
5. Break up runs of same-length sentences.
6. Read it aloud. If a line sounds like a LinkedIn post or a product press release, rewrite it.
7. Stop once it sounds natural. Do not over-polish it.

## When NOT To Use

- Developer-facing writing: READMEs, API docs, changelogs, code comments, commit messages. Accuracy and convention win there, not voice.
- Legal, compliance, or policy text where exact wording is mandated. Flag clunky phrasing, don't rewrite it.
- Quotes and testimonials from real people. Their words stay verbatim.
- Positioning, page structure, proof selection, or SEO metadata for a website: that judgement belongs to `portfolio-copywriter`. This skill still governs the voice of the resulting copy.
- Campaign structure, offers, and CTAs for emails, announcements, social posts, or ads: that judgement belongs to `campaign-copywriter`. This skill still governs the voice there too.