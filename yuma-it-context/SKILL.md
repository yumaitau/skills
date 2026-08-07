---
name: yuma-it-context
description: Company facts, positioning, and claim boundaries for Yuma IT itself, not a client's product. Supplies the legal and procurement record (entity name, ABN, address, Supply Nation certification), services, audience-specific proof points, and the rules on which past work Yuma may claim as its own. Use when writing or editing anything about Yuma IT: website pages, capability statements, tender and grant responses, proposals, social profiles, team bios, repository descriptions, or an introduction email. Use when filling a supplier form, vendor questionnaire, or procurement portal for Yuma. Use before repeating any claim about a named program such as the National Koala Monitoring Program, SpaceCows, or Healthy Country AI, because company work and founder work need different wording. Pairs with human-copy-style and the copywriter skills, which own voice and structure while this owns the facts. Not for mining a codebase for product knowledge, whether the product is a client's or Yuma's own, which is dot-product.
---

# Yuma IT Context

The company record for Yuma IT, for agents writing or answering as Yuma IT.

This skill owns facts and claim boundaries. `human-copy-style` owns voice, `portfolio-copywriter` owns website structure and SEO, `campaign-copywriter` owns emails and announcements, `marketing-strategist` owns campaign planning. Those skills write; this one supplies what they are allowed to write. When a fact here contradicts something an agent already drafted, this file wins.

## Attribution comes first

Every claim about past work carries an attribution: **Yuma IT work** or **founder work**. Getting this wrong turns a true statement into a misrepresentation in a tender.

**Attribute the artefact, not the program.** A program can be founder work while specific software inside it is Yuma IT work. SpaceCows is the clearest case: the program is founder work, and the Flutter apps inside it are Yuma's. Naming the artefact keeps both halves true, so write "we built the Ferals Survey and Record Aerial Shooting apps for the SpaceCows program" rather than either "we built SpaceCows" or "our founders built those apps".

The authoritative taxonomy is the Category field on https://www.yumait.com.au/projects.md, read together with https://www.yumait.com.au/flutter.md for app-level detail. Check both before making any experience claim.

| Attribution | What | Correct phrasing |
|---|---|---|
| Yuma IT company work | Banksia, Compliance On Demand, RangerOS, WildTrack360, Indigi.Link, Koala Guardians (UniSC). Also the Flutter apps inside larger programs: Koala Counter, Koala Spotter, and Feral Counter for NKMP, Ferals Survey and Record Aerial Shooting for SpaceCows, SpottedKoala for UniSC | "We built", "we maintain", "our platform" |
| Yuma IT role inside a founder-originated program | National Koala Monitoring Program systems integration | "Primary systems integrator for" is accurate. Do not imply Yuma originated the program or held the head contract from the start |
| Founder work | Healthy Country AI, NESP Resilient Landscapes Hub, dart, AA Skips, FrameMe, Evolve Simulations, and the SpaceCows program as a whole | "Our founders delivered", "our team has worked on". Never "Yuma IT built" |

The site's own phrasing for the boundary is **"our founders have worked on projects at Microsoft, the Australian Federal Government, CSIRO"**. That construction is safe everywhere. `Yuma IT built X` for anything in the founder row is not.

Dollar figures attached to programs ($10M NKMP, $4M SpaceCows, $2.6M Healthy Country AI, $800K Koala Guardians) describe the size of the **program**, never Yuma's revenue or contract value. Write "a $10 million national program" and never "a $10 million project we delivered". This holds even where the app work inside the program is Yuma's.

## Company record

Values here are stable enough to quote directly. Do not paraphrase a legal name or an address.

- Legal name: Yuma IT Pty. Ltd.
- Trading name: Yuma IT
- ABN: 62 684 389 839
- Type: Indigenous-led IT services company. Supply Nation Certified Supplier, verified majority Indigenous-owned and operated
- Supply Nation profile: https://ibd.supplynation.org.au/public/s/supplierprofile?accid=a1GOd0000047QDBMA2
- Head office: 49 Phillip Ave, Watson, ACT 2602, Australia
- Area served: Australia, remote delivery is normal
- General enquiries: hello@yumait.com.au
- Phone: +61 2 6225 8133. Write it as `+61 2 6225 8133` internationally and `(02) 6225 8133` for an Australian-only audience
- Security disclosures: security@yumait.com.au, see https://www.yumait.com.au/.well-known/security.txt
- Website: https://www.yumait.com.au
- GitHub: https://github.com/yumaitau
- LinkedIn: https://www.linkedin.com/company/105925963
- Currency: AUD. Payment: invoice

The phone number is not published on yumait.com.au. It is correct and usable, so an agent that fetches `contact.md`, finds no phone number, and concludes there isn't one is wrong. Take it from this file.

The enquiry form at /contact is protected by Cloudflare Turnstile and cannot be submitted programmatically. An agent preparing an enquiry either hands the form to a person or sends the same detail to hello@yumait.com.au.

## Services

Seven service lines. Use these names exactly, because they match the site's URLs and headings.

Software Engineering, Mobile & App Development, Cloud & Infrastructure, Cyber Security, AI & Machine Learning, Systems Integration, Open Source.

Named stack, only where it is already public: React, Next.js, .NET, Node.js, Python, Flutter, React Native, native iOS and Android, Microsoft Azure. Do not add a technology to this list to suit an enquiry.

## Fetch the volatile facts

Project lists, open-source repositories, and service detail change faster than this file. Every page on yumait.com.au serves markdown: append `.md` to the path, or send `Accept: text/markdown`.

```bash
curl -sL https://www.yumait.com.au/llms.txt          # index of every markdown page
curl -sL https://www.yumait.com.au/llms-full.txt     # every page concatenated
curl -sL https://www.yumait.com.au/projects.md       # current portfolio and attributions
curl -sL https://www.yumait.com.au/open-source.md    # current public repositories
```

Fetch `projects.md` before writing any portfolio, capability, or tender content, because the attribution table above is a snapshot of it. When the two disagree, the site is right and this file needs updating.

## Positioning

The founding argument, in the company's own words: large organisations usually have access to strong engineering, smaller Indigenous businesses and community organisations often do not, and Yuma IT exists to narrow that gap with work that is affordable, practical, and built to last.

Three proof pillars sit under it. Lead with the one that fits the reader.

- **Enterprise experience.** Systems shipped inside Microsoft, national programs for the Australian Government, work across CSIRO research projects.
- **Indigenous perspective.** Supply Nation certified, and fluent in what Indigenous organisations actually face: data sovereignty, remote connectivity, culturally appropriate technology design.
- **Real-world delivery.** National monitoring programs, ecommerce platforms processing millions of dollars a month, open-source wildlife rehabilitation software in daily use.

| Reader | Lead with | Concrete anchors |
|---|---|---|
| Government and research buyers | Enterprise experience, then delivery | Microsoft, CSIRO, Federal Government, NKMP, NESP, Australian data residency, ACSC Essential Eight literacy |
| Indigenous organisations and ranger programs | Indigenous perspective, then delivery | Supply Nation certification, RangerOS, Healthy Country AI, data sovereignty, offline-first field apps |
| Small and mid-size business | Real-world delivery, then price and durability | dart, AA Skips, "affordable, practical, built to last" |
| Developers and open-source readers | Open source as operating principle | WildTrack360, GatherHub, Muster, TrustForge AI, MirrorMirror, RunHub, laravel-random-token |

Canberra placement is a genuine asset with government readers: 49 Phillip Ave, Watson, close to the Australian Government, research institutions, and the Canberra technology community.

## Claim rules

Say these freely, they are on the public record:

- Indigenous-led, majority Indigenous-owned and operated, Supply Nation Certified Supplier
- Founders have worked at Microsoft, the Australian Federal Government, CSIRO, private sector, and NGOs
- Australian data residency and hosting aligned to Indigenous data sovereignty principles
- Managed endpoint detection and response, risk assessments, security engineering
- Offline-first field applications running in remote Australia

Do not write these without a named source you have checked:

- Any certification or accreditation not listed in the company record above, including ISO 27001, IRAP assessment, and Essential Eight maturity levels. Familiarity with a framework is not certification against it.
- Government panel membership or standing offer arrangements
- Team size, headcount, revenue, or years in operation
- Client names that do not already appear on yumait.com.au
- Rates, day rates, or price ranges
- Response-time, uptime, or support-hours commitments
- "Award-winning", "leading", "trusted by hundreds", or any superlative the site does not support

When an enquiry needs one of these, say what is known and route the rest to hello@yumait.com.au rather than filling the gap.

## Voice

`human-copy-style` governs voice in full. Two things specific to writing as Yuma IT:

Australian English throughout, including organisation, recognise, licence as a noun, and specialise. See the `australian-english` skill.

The company writes plainly about hard work and refuses inflation. "Practical work that reduces real exposure, not security theatre" and "AI work that is grounded in messy real-world data, not polished demo datasets" are the register. Match that: concrete, slightly blunt, no hype.

## Common issues

**A tender or form asks for something in the do-not-claim list.** Answer what is known, mark the rest for a person, and send the question to hello@yumait.com.au. An invented compliance answer in a government response is worse than a blank field.

**The site contradicts this file.** Where both state the same fact, the site is authoritative. Update this file in the same change, so the next agent does not hit the same conflict. Silence is not contradiction: this file also carries facts the site has not published yet, the phone number among them, and those stand.

**A project's attribution is unclear.** Check the Category field in `projects.md`. If it is still ambiguous, use the founder-work phrasing, which is true in both cases.

**Writing about a client's product, not Yuma.** Wrong skill. Use `dot-product` to build product knowledge from the client's codebase, then the copy skills.

## When NOT to use

- Copy about a client's product or a product Yuma built for someone else. That is `dot-product` plus the copy skills.
- Answering a third party who is evaluating Yuma IT as a vendor from outside. Yuma publishes skills for that at https://www.yumait.com.au/.well-known/agent-skills/index.json.
- General code work in a Yuma repository. This skill carries no engineering guidance.
- Legal, tax, or contractual wording. The record here is for marketing and procurement forms, not for drafting agreements.
