---
name: australian-english
description: Enforces Australian English in all prose output, including documentation, READMEs, changelogs, UI text, error messages, emails, reports, code comments, and commit messages. Use whenever writing or editing prose in a project that targets an Australian audience or team, whenever the user asks for Australian English, AU spelling, or -ise endings, or complains about American spellings, and even when nobody mentions spelling at all, since agents default to US English. Covers the tricky noun/verb pairs (licence/license, practice/practise, program/programme), the -ise, -our, and -re families, and the hard boundary that code identifiers, API names, package names, and conventional filenames like LICENSE always keep their original spelling. The copy skills already mandate Australian spelling for customer-facing copy and defer here for the detail; this skill is primary for developer-facing prose. Not for projects with a documented US or British English convention, and never for respelling quoted text or code.
---

# Australian English

Australian English is the default for every sentence of prose you write. American spelling in prose is a bug; American spelling in code is correct and untouchable.

In this pack, `human-copy-style`, `portfolio-copywriter`, and `campaign-copywriter` already require Australian spelling for customer-facing copy. This skill defines the detail and extends the default to everything else, including the developer-facing writing those skills exclude.

## The Boundary

Everything you write is either prose or a symbol. Prose gets Australian English. Symbols keep the exact spelling their platform, author, or convention gave them, because respelling them breaks code and links:

- identifiers, function, variable, and class names, API parameters, CSS properties, config keys (`color`, `center`, `initialize`, `normalize`)
- package, dependency, and product names
- conventional filenames (`LICENSE`, `CHANGELOG`), URLs, and slugs
- direct quotes, legal excerpts, and proper nouns (the US "Department of Labor")

When prose refers to a symbol, keep the symbol verbatim and write the prose around it in Australian English: "set `color` to change the border colour".

## Spelling — the traps

You already know the -ise, -our, and -re families (organise, colour, centre). These are the cases that still go wrong:

| Trap | Rule |
|------|------|
| licence / license | Noun takes c, verb takes s. "An MIT licence", "licensed under MIT". Compounds follow the same rule (a sublicence, to sublicense). The repo file stays `LICENSE`. |
| practice / practise | Noun takes c, verb takes s. "Best practice", "practise the demo". |
| program / programme | Software is always "program". "Programme" is for TV, events, and schedules. |
| meter / metre | Distance is "metre"; a measuring device is a "meter". |
| Double-l inflections | travelling, modelling, cancelled, labelled, enrolled. But single l in enrolment and instalment. |
| fulfil, skilful | Single l in the base word; fulfilment, but fulfilling. |
| defence, offence | Nouns take c; "defensive" keeps the s. |
| Legitimate -ize words | size, resize, capsize, prize, seize are not part of the -ise family. Leave them. |
| focused | Preferred over "focussed" in Australian style guides. |

Dates in prose read day-first: "6 August 2026" or 06/08/2026. ISO 8601 (2026-08-06) stays wherever code, filenames, or data formats expect it.

## Verification

After writing or editing prose files, run this over the files you touched:

```bash
rg -ni '\b(colors?|behaviors?|centers?|favorites?|catalogs?|gray|defense|offense|canceled|traveled|labeled|modeling|fulfill|enrollment|installment|licenses?|\w+izations?|\w+iz(es?|ed|ing))\b' <files>
```

Every hit must be one of: inside a code span, identifier, filename, or URL; a proper noun or quote; a legitimate -ize word (size, resize, capsize, prize, seize); a correct verb use of "license"; or fixed. You are done when every hit is accounted for.

## Common Issues

### Spell checker flags colour, organise, licence
The dictionary is set to US English. Point it at Australian English instead, for example `"cSpell.language": "en-AU"` in VS Code settings or `"language": "en-AU"` in `cspell.json`.

### Existing file is consistently American English
If the project documents a US English convention, follow it (see When NOT to Use). If it is just drift in an Australian project, fix the prose you are already editing and offer a whole-repo pass as a separate task rather than silently converting everything.

### User or reviewer asks to "fix" a code identifier's spelling
Renaming `color` to `colour` in code breaks the API contract and every caller. Explain the prose/symbol boundary and change only the surrounding prose.

## Examples

### Example 1: changelog entry touching a code setting

User says: "Write a changelog entry for the new colorScheme setting that lets users customize dashboard colors."

Result:

> Added the `colorScheme` setting. Users can now customise dashboard colours from Settings, and their choice is synchronised across devices.

The identifier keeps its US spelling; every prose word is Australian.

### Example 2: licensing section

User says: "Add a licensing section to the README."

Result:

> This project is distributed under the MIT licence. See the `LICENSE` file in the repository root. Commercial use is permitted, and companies are licensed to embed the library in their own products.

Noun "licence", verb "licensed", filename `LICENSE` untouched.

## When NOT to Use

- The project documents a US or British English convention, or the user asks for one. The documented convention wins.
- Quoted text, legal excerpts, and other people's words. They stay verbatim.
- Non-English text and translation tasks.
- Renaming anything in code. The boundary above is absolute even when the whole codebase is Australian-owned.
