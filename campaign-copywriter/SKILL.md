---
name: campaign-copywriter
description: Structure, offers, CTAs, and channel patterns for standalone marketing pieces sent or posted to an audience. Use whenever writing, rewriting, or critiquing marketing emails, newsletters, product launch or release announcements, social posts, or ad copy, including subject lines, preview text, and email sequences. Trigger even for small jobs like tightening a subject line or reviewing one LinkedIn post. Reads `.product/` knowledge files from the dot-product skill when present, consumes campaign briefs from marketing-strategist, and pairs with human-copy-style for baseline voice. Not for website page copy with a page-level SEO job, which portfolio-copywriter owns, and not for deciding the campaign's goal, audience, or channels, which marketing-strategist owns.
---

# Campaign Copywriter

Every piece has one message, one audience, and one action. If you can't name all three before drafting, you're not ready to draft. Campaign copy interrupts someone's inbox or feed, so earn the interruption: say something true and useful, then get out.

This skill owns structure, offers, CTAs, and channel patterns for standalone marketing pieces. Baseline voice and AI-tell avoidance belong to the `human-copy-style` skill. If that skill is not installed, hold its core line yourself: plain verbs over buzzwords, no em dashes or emojis, no generic hype, varied sentence rhythm, Australian spelling.

## Source Material

Real material beats invention, so gather it before drafting:

1. If a campaign brief exists (the `marketing-strategist` skill writes them, usually under `docs/marketing/`), read it first. It names the goal, audience, message, and channel, which are exactly the decisions you should not be making mid-draft. If the job is a full campaign and no brief exists, suggest running `marketing-strategist` first; for a single piece, just ask the user for goal, audience, and desired action.
2. If `.product/` exists at the repository root (output of the `dot-product` skill), read `OVERVIEW.md`, `FEATURES.md`, and `DIFFERENTIATORS.md` for code-grounded product facts.
3. Read past sent campaigns or published posts if the user can share them. Existing pieces set the voice and reveal what claims have already been made.
4. Ask the user for anything load-bearing that no source provides.

You are done gathering when the goal, audience, and action are named, and every claim you plan to make traces to a source or to a question you have asked.

## Never Invent

- Never invent metrics, customer names, testimonials, review scores, subscriber counts, or results.
- Never invent urgency or scarcity. "Offer ends Friday", "only 3 spots left", and "prices going up soon" are lies unless the user confirmed them. A CTA without a deadline is better than a fake deadline.
- Never invent discount codes, prices, or offer terms. Confirm the exact offer before writing around it.
- Never claim a feature does something you can't trace to `.product/`, the brief, or the user.
- If a strong line depends on a fact you don't have, ask for it or write a weaker line that is true.

When unsure whether a detail is real, flag it inline like `[check: is the webinar actually on the 14th?]` so the user can verify before sending. Sent email cannot be edited, so the bar is higher than for a web page.

## One Message Per Piece

Before drafting, write down: the one thing the reader should remember, and the one action they should take. Everything in the piece supports those two or gets cut. If the user hands you three announcements for one email, either pick the lead and demote the rest to short mentions, or propose splitting into separate sends.

## Channel Patterns

### Marketing Email

- Subject line: aim under 50 characters so it survives mobile truncation. Say what's inside; the email delivers what the subject promised. Offer 2 to 3 options.
- Preview text complements the subject rather than repeating it. Write it deliberately or the client will grab the first body line.
- The first two lines carry the point. Assume the reader sees nothing below the first scroll.
- One CTA per email, appearing at most twice. Two different CTAs halve both.
- Sign off as a person where the brand allows it. "Reply to this email" is a legitimate CTA and often outperforms a button.

### Newsletter

- Multiple items are fine, but ordered by what the audience cares about, not by internal pride.
- Each item is self-contained: what it is, why the reader would care, one link.
- Cut any item that exists only to fill space. A short newsletter that's all signal trains people to open the next one.

### Launch And Release Announcements

Structure: what shipped, who it's for, what changes for them, how to get it. In that order, in plain terms.

**Example rewrite:**

Before:

> We're thrilled to announce the launch of our revolutionary new Scheduled Exports feature, designed to empower teams to take their reporting to the next level!

After:

> Scheduled exports are live. Pick any dashboard, set a schedule, and the CSV lands in your inbox. No more Monday-morning screenshots. It's on every plan now, under Dashboard, then Export.

The "after" tells an existing user what it is, what it replaces, and where to find it. The "before" could announce anything.

### Social Posts

- One idea per post. Lead with the hook that is true, not the hook that is loud.
- Write for the platform: LinkedIn truncates around the first 150 characters, so the opening line does the work; X posts cap at 280; longer thoughts belong in a thread or an article, not a screenshot of text.
- Hashtags: two or three relevant ones at most, or none. A hashtag wall reads as spam.
- Don't cross-post identical text to every platform. Adapt the framing or post to fewer platforms.
- When asked for "viral" content, aim for shareable-because-useful: a specific lesson, a real number the user approved, a before-and-after. Manufactured controversy and engagement bait damage trust with the audience these businesses actually serve.

### Ad Copy

- Headline states the offer or the outcome. Body adds one proof point. That's usually all the space there is.
- Respect platform limits: Google responsive search ads take 30-character headlines and 90-character descriptions; assume roughly 125 characters of Meta primary text show before truncation. Write to survive the cut.
- The CTA and the landing page must match. Don't write "Book a free audit" for a page whose form says "Contact us".
- Provide the required variants (multiple headlines and descriptions) rather than one perfect line, and make them mixable: each headline must make sense next to each description.

## Sequences

When writing an email sequence, each email advances the story rather than repeating the last one louder. Map the sequence before writing email one: what each send says, what it asks, and what happens if the reader already acted. Reference the brief's stages if one exists. A three-email sequence where email two is email one reworded is a two-email sequence.

## CTA Rules

- The CTA says what happens on click: "Start a free trial", "Read the changelog", "Book a 20-minute call", "Reply with your postcode".
- Match the ask to the relationship. Cold audiences get low-commitment asks; existing customers can be asked for more.
- No fake urgency, per Never Invent. Real deadlines, stated plainly, work fine.

## Rewrite Pass

Voice-level editing (filler, buzzwords, rhythm) is `human-copy-style`'s rewrite pass. This one is about message and action:

- Name the piece's one message and one action. Cut every line serving neither.
- Check every claim, number, name, date, and offer term traces to a source. Flag anything that doesn't.
- Check the subject line still matches the body after edits.
- Check the CTA survives skim-reading: a reader who only sees the subject, first line, and button should still know what's on offer.
- Read it as the recipient, not the sender. If the piece opens with the company instead of the reader, invert it.
- Keep the deliverable in the business's language. Explain choices and flag gaps in terms of the audience and the facts, not by citing this skill or its rules; the client never reads the skill.

## When NOT To Use

- Website page copy, landing pages, heroes, service pages, SEO titles, or meta descriptions: `portfolio-copywriter` owns those. A landing page an ad points to is website copy, even when written alongside the campaign.
- Choosing the campaign goal, audience, channels, or calendar: that judgement belongs to `marketing-strategist`. If those decisions are missing, get them first.
- Transactional email (receipts, password resets, notification templates) and UI microcopy: `human-copy-style` alone covers those.
- Blog posts and long-form content with no send-or-post job: `human-copy-style` covers voice; there is no campaign structure to add.
- Extracting product knowledge from a codebase: that is `dot-product`. Run it first, then come back here for the copy.
