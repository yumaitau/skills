---
name: dot-product
description: Use this skill to analyse an existing codebase and produce a `.product/` folder of sales-oriented knowledge files describing what the product does, who it serves, and how it competes. Output is consumed by sales reps, marketing, demo builders, and AI sales agents — not engineers. Trigger when the user asks to "extract product features", "build a product profile", "generate sales docs from the code", "build a sales agent for this product", "what does this app actually do", "summarise this codebase for sales", or asks for files like FEATURES.md, USE_CASES.md, or a product knowledge base. Also use when onboarding a new product into a sales motion or building an AI agent that needs to pitch, qualify, or answer questions about the product. Pairs with human-copy-style and portfolio-copywriter for downstream copy work.
---

# Dot Product

Mine an existing codebase for everything a sales motion needs to know about the product, and write it into a `.product/` folder at the project root. The output is the raw knowledge layer that sales reps, marketing, and AI sales agents read from.

This skill does **discovery and synthesis**, not pitching. The copy here should be plain, factual, and grounded in what the code actually does. Polished pitch language is the job of `human-copy-style` and `portfolio-copywriter` downstream.

## Output

Always write to `.product/` at the **repository root** (alongside `.claude/`, never inside `src/` or a subfolder). Create the folder if missing.

| File | What goes in |
|------|-------|
| `OVERVIEW.md` | One paragraph: what the product is, the category it sits in, the customer it serves, the core promise. Plus a short "at a glance" block (stack, deployment model, maturity signal). |
| `FEATURES.md` | User-facing features grouped by area. Each feature: short name, one-line description, where it lives in the code (file or route), maturity (shipped / in progress / experimental). |
| `USE_CASES.md` | Concrete scenarios: "A {persona} uses this when {trigger} to {outcome}." Build these from real flows in the code, not imagined ones. |
| `PERSONAS.md` | Who uses the product. Infer from roles, permissions, auth flows, onboarding steps, and UI copy. Include a primary persona and any secondary ones. |
| `INTEGRATIONS.md` | Third-party services, APIs, OAuth providers, webhooks, supported platforms, import/export formats. Group by category (auth, payments, data, comms, etc.). |
| `DIFFERENTIATORS.md` | Capabilities that are unusual, surprisingly deep, or worth leading with in a pitch. Conservative — only list things the code actually supports. |
| `TECHNICAL_PROFILE.md` | Stack, hosting/deployment model, data residency hints, auth model, security-relevant features (RBAC, audit logs, encryption), scalability signals. For technical buyers and security questionnaires. |
| `LIMITATIONS.md` | What the product does **not** do, based on what's missing in the code. Important for honest qualification. |
| `GLOSSARY.md` | Domain terms the product uses (from models, copy, routes). Helps a sales agent talk like the team. |
| `product-profile.json` | All of the above as structured data. Schema below. Direct input for AI sales agents. |

If the codebase is small, files can be brief — a few bullets is fine. Don't pad. If a section genuinely has nothing in it, write `_No signal found in code._` rather than inventing.

## Workflow

Run these phases in order. Don't skip discovery to start writing — every claim in the output must trace back to something you read.

### Phase 1 — Map the surface

Build a mental model of what the code exposes. Read, don't guess.

Signal sources, in priority order:

1. **Manifest files** — `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `composer.json`, `Gemfile`, `pubspec.yaml`. Name, description, dependencies, scripts, entry points.
2. **README and `/docs`** — existing positioning. Useful but treat as a hypothesis to verify against the code, not ground truth. READMEs often lag behind reality.
3. **Routes / API surface** — `app/`, `pages/`, `routes/`, `api/`, `controllers/`, route registrations, OpenAPI specs, GraphQL schemas. Each route is a capability.
4. **UI surfaces** — pages, screens, navigation menus, settings panels. The menu is often the cleanest map of features.
5. **Data models** — schemas, migrations, ORM models, Prisma/SQL/Mongoose definitions. The nouns of the domain.
6. **Auth and roles** — middleware, guards, role checks, RBAC tables, permission strings. These reveal personas.
7. **Integrations** — env vars (`.env.example`, `config/`), SDK imports (`stripe`, `twilio`, `okta`, `@aws-sdk/*`), webhook handlers, OAuth flows.
8. **Background jobs / workers** — queues, cron, scheduled tasks. Often hide major capabilities (notifications, billing runs, syncs).
9. **CLI entry points** — `bin/`, `cli.ts`, `main.py`, scripts. Direct user actions.
10. **Tests and E2E flows** — `tests/`, `e2e/`, `cypress/`, `playwright/`. Test names describe intended behaviour in plain language.
11. **UI copy** — strings in components, marketing pages, email templates. The voice the product already has.
12. **Changelog / release notes** — what the team chose to ship and announce.

Use the available tools to gather this efficiently. `Glob` and `Grep` are the safe defaults. Don't commit to a list of features until you've at least skimmed routes, models, and the navigation surface.

### Phase 2 — Cluster signals into features

Group what you found into user-facing features. Rules:

- A feature is something a customer would **name**, not an internal module. "Send invoice reminders" is a feature; "QueueService" is not.
- One feature can span many files. One file can contribute to many features. Don't map 1:1.
- Drop dev-only tooling, internal admin scripts, and deprecated code paths. They don't belong in sales material.
- If two signals describe the same capability from different angles (e.g. a route, a model, and a UI page), merge them into one feature with multiple references.

For each feature, capture:

- Short name (3–5 words, customer-facing)
- One-line description in plain English
- Code reference(s) — file paths or routes, so the claim is verifiable
- Maturity signal (shipped, in progress, experimental) inferred from test coverage, feature flags, TODOs, route comments

### Phase 3 — Translate technical to customer language

This is the step where sales material usually goes wrong. The translation rules below are the spine of the skill.

| Technical signal | Customer-facing framing |
|---|---|
| `POST /api/exports` route | "Export your data" capability |
| `BullMQ` job processing nightly aggregations | "Automated daily reporting" |
| `OAuth2` against Google, Microsoft | "Single sign-on with your existing identity provider" |
| `Stripe` SDK + webhook handlers | "Subscription billing and invoicing" |
| `RBAC` middleware with `admin`, `member`, `viewer` roles | "Role-based access control with three permission tiers" |
| Multi-tenant schema (`organisation_id` on every table) | "Built for teams — isolated workspaces per organisation" |
| WebSocket / SSE channel | "Live updates without page refresh" |
| S3 with presigned URLs | "Secure file uploads and downloads" |

Three rules for translation:

1. **Claims must be proportional to evidence.** A feature flagged behind `EXPERIMENTAL_*` or only enabled in dev is not "shipped". Say "in development" or omit it.
2. **No invented numbers.** Never write "10x faster", "99.9% uptime", "trusted by 500 companies", or any metric the code can't prove. Prefer qualitative claims grounded in what the code does.
3. **No invented integrations.** Only list integrations whose SDK, env var, or API call you actually saw. A `// TODO: add Slack` comment is not an integration.

If the README makes a claim the code doesn't back up, document the claim in `LIMITATIONS.md` as a gap to verify with the team rather than repeating it as fact.

### Phase 4 — Write the files

Write all markdown files first, then generate `product-profile.json` last so it reflects the finished narrative.

Markdown style:

- Plain English. No marketing theatre, no hype adjectives ("powerful", "seamless", "robust", "best-in-class").
- Australian spelling.
- Short sentences. Bullets where they help, prose where bullets feel staccato.
- Include code references (file or route) for any non-obvious claim, formatted like `src/routes/billing.ts:42`. This lets a curious reader verify.
- Avoid emojis, em dashes, and filler transitions ("Furthermore,", "In conclusion,").
- Don't write headings the file doesn't need. If `LIMITATIONS.md` has three bullets, three bullets is the file.

JSON style — see schema in `references/product-profile-schema.md`. Validate that every feature in `FEATURES.md` appears in `product-profile.json` and vice versa.

### Phase 5 — Verify before finishing

Before declaring done, walk back through and check:

- [ ] Every claim in every file traces to a specific file, route, or config you actually read
- [ ] No invented integrations, metrics, customers, or features
- [ ] `LIMITATIONS.md` is honest — at least a couple of items unless the product really is feature-complete
- [ ] `product-profile.json` parses as valid JSON and matches the markdown
- [ ] No internal tooling, dev scripts, or deprecated code leaked into the sales-facing files
- [ ] File paths in references are correct and current

If you find gaps you genuinely cannot resolve from the code alone, list them at the bottom of `OVERVIEW.md` under a `## Open Questions` heading rather than guessing. The sales team would rather see a question than a confident wrong claim.

## When NOT to use

- The user wants engineering documentation (architecture, API reference, contributor onboarding) — that's a different artefact.
- The user wants polished pitch copy ready to publish — run this skill first, then hand the output to `portfolio-copywriter` or `human-copy-style`.
- The codebase is a thin prototype with no real features yet — the output would be padding. Tell the user.
- The user wants competitive analysis or market positioning — this skill describes the product, not the market.
- The product is a library or developer tool whose audience is engineers — write developer-facing docs instead, the sales-agent framing doesn't fit.

## Common Issues

### `.product/` already exists with content
Treat it as prior work. Read it first. Update files in place rather than overwriting blindly. Note in your final summary what you changed and why.

### Codebase is a monorepo with multiple products
Ask the user which product to analyse, or analyse one per top-level package and write `.product/<package-name>/...` for each.

### README contradicts the code
Trust the code. Note the contradiction in `LIMITATIONS.md` or `OPEN_QUESTIONS` so the team can resolve it.

### Heavy use of feature flags
Treat flagged-off features as "in development" unless the flag is on by default in production config. Don't list dark-launched experiments as shipped features.

### No clear navigation or routes (CLI, library, SDK)
The "surface" is the public API or command set. Read the exported symbols, the CLI command tree, and the docs. Personas may be just "developer" — that's fine, say so.

## Examples

### Example 1: SaaS web app

User says: "Build a product profile for this codebase so our sales team can pitch it."

Actions:
1. Map routes (`/api/*`), pages (`app/*`), models (`prisma/schema.prisma`), env vars (`.env.example`), Stripe + Auth0 SDK usage.
2. Cluster into features: workspaces, billing, SSO, exports, audit logs, role-based access.
3. Translate: `Auth0` → "SSO via your identity provider", `Stripe` → "Subscription billing".
4. Write `.product/` with all nine files + JSON.

Result: Sales team has a fact-checked feature list, a personas doc inferred from the role enum, and a JSON file the company's AI demo bot can load directly.

### Example 2: AI sales agent build

User says: "I'm building an AI agent that pitches this product to inbound leads. Generate the knowledge base it should read from."

Actions: Same workflow, with extra attention to `product-profile.json` since the agent will read it programmatically. Make sure features and integrations are tagged with categories the agent can filter on.

Result: The agent loads `.product/product-profile.json` at start-up and can answer "do you support X?" questions accurately.

## References

- `references/product-profile-schema.md` — JSON schema for `product-profile.json`
- `references/translation-patterns.md` — extended technical → customer-facing translation table
