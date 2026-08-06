---
name: marketing-strategist
description: Campaign planning and messaging strategy before any copy is written. Use whenever planning a marketing campaign, product launch, or content calendar, choosing which audiences or channels to target, building a messaging framework, or writing a campaign brief. Trigger for asks like "plan the launch", "who should we target", "what should we post this month", "we need a marketing plan", or when someone wants to pressure-test a marketing idea before committing. Reads `.product/` knowledge files from the dot-product skill when present and writes briefs consumed by campaign-copywriter and portfolio-copywriter. Not for writing the copy itself, which those skills own, and not for extracting product knowledge from a codebase, which dot-product owns.
---

# Marketing Strategist

Strategy is choosing what not to do. A plan that lists every channel and every audience is a wish, not a strategy. Produce plans a real team can execute: grounded in facts the business actually has, sized to the hours actually available, aimed at one measurable outcome.

This skill owns the decisions upstream of copy: goal, audience, message, channels, timing. The writing itself belongs to `campaign-copywriter` (emails, announcements, social, ads) and `portfolio-copywriter` (website pages), with `human-copy-style` governing voice throughout.

## Source Material

1. If `.product/` exists at the repository root (output of the `dot-product` skill), read `PERSONAS.md`, `USE_CASES.md`, `DIFFERENTIATORS.md`, and `LIMITATIONS.md` first. Personas and differentiators are the raw material of targeting and messaging, and limitations stop you promising what the product can't do. If the planning job is substantial and `.product/` is missing, suggest running `dot-product` first.
2. Ask what the business already has: email list size, social followings, past campaign results, existing content, analytics access. Strategy built on assets that don't exist is fiction.
3. Ask what capacity exists: who does marketing, how many hours a week, what budget. This constrains everything downstream.

You are done gathering when you know the goal, the available assets, and the available capacity, and every audience or channel claim traces to a source or is flagged as an assumption.

## Never Invent

- Never invent market sizes, competitor facts, industry statistics, or benchmark rates. "Industry average open rates are around 20%" is an invention unless the user supplied it.
- Never invent audience research. If nobody has talked to customers, say the targeting is a hypothesis to test, not a finding.
- Never assume budget, headcount, or assets. Ask.
- When a recommendation rests on something unverified, flag it inline like `[assumption: trial users churn because of onboarding, worth checking against support tickets]`.

A plan that says "we don't know yet, here's the cheapest way to find out" beats a confident plan built on invented numbers.

## Core Judgement Rules

- **One campaign, one goal.** "Raise awareness and drive signups and re-engage churned users" is three campaigns. Make the user pick, or sequence them.
- **Fewer channels, done properly.** Two channels executed weekly beat six executed once. Pick channels where the audience already is, using the personas, not the default set every plan reaches for.
- **Existing assets first.** An email list of 800 customers outranks a cold social audience of zero. Rank tactics by asset strength, then by cost.
- **Size to capacity.** A content calendar the team can't sustain is a plan to fail slowly. If the user has 4 hours a week, the plan fits in 4 hours a week, and says so.
- **Every message claim needs proof behind it.** If the framework says "fastest setup in the category", the proof column says what backs that, or the claim goes.

## Outputs

Pick the artifact the job needs. Save written artifacts where the user keeps marketing docs; default to `docs/marketing/` if nothing exists yet. Write every artifact in the business's own language: justify each recommendation by a fact about the audience, product, or assets, stated directly ("two audiences with different intents need separate sends"), never by naming this skill or its rules as the authority (the reader has no access to them). Skill names appear only where pieces are tagged with the skill that writes them.

### Campaign Brief

The standard handoff to the copy skills. Every brief contains all seven sections; write "unknown, to be tested" rather than deleting a section:

```markdown
# Campaign Brief: [name]

## Goal
One measurable outcome, with a number and a date where possible.

## Audience
Who, and why them. Reference personas from .product/ if present.

## Message
The single core message, plus supporting points, each with its proof.

## Offer and CTA
What the audience is asked to do, and what they get.

## Channels
Which channels, and why these over the alternatives.

## Timeline
Key dates and the sequence of pieces.

## Success Measure
How you'll know it worked, and when you'll check.
```

### Messaging Framework

One row per audience segment: the problem in their words, the value proposition, the proof, and the likely objections with responses. Built from personas and differentiators, not from adjectives. This is the document that stops five pieces of copy contradicting each other.

### Channel Plan Or Content Calendar

Cadence per channel, owner, and effort per item. State the weekly hours the calendar consumes so the user can veto it honestly. Start smaller than feels impressive; a calendar survives contact with month two or it was decoration.

### Launch Plan

A campaign brief plus a timeline of concrete pieces: which emails, which posts, which page updates, in what order, each tagged with the skill that writes it (`campaign-copywriter` or `portfolio-copywriter`). For launches aimed at existing users, the product itself is usually the cheapest channel: an in-app notice, changelog entry, or empty-state hint reaches active users without spending the marketer's hours. Ask whether one is available before adding external channels.

## Working Method

1. Establish which artifact the job needs. A vague "we need marketing" ask usually needs a campaign brief first, not a calendar.
2. Gather source material as above. Interview for goal, assets, and capacity before proposing anything.
3. Draft the artifact. Trace every claim; flag every assumption.
4. Apply the judgement rules: one goal, few channels, assets first, sized to capacity.
5. End with the handoff: name each piece of copy the plan implies and which skill writes it. The plan is done when someone could start writing tomorrow without asking what to write.

## Pushing Back

Part of the job is saying no with reasons. When the user or their stakeholder wants to target "everyone", pick the segment with the strongest proof and frame the rest as later phases. When asked for channels the personas don't support, show the mismatch rather than silently complying. Ground every pushback in a fact from the source material, and yield gracefully when the user overrules you; it's their business.

## When NOT To Use

- Writing the actual copy: `campaign-copywriter` for emails, announcements, social, and ads; `portfolio-copywriter` for website pages. This skill stops at the brief.
- Extracting product knowledge from a codebase: that is `dot-product`. Run it first, then plan from its output.
- Brand identity, logos, or visual design: out of scope for this skill family.
- Pricing strategy or product roadmap decisions: flag the dependency and leave the call to the user.
