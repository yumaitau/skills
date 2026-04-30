# `product-profile.json` Schema

The structured form of `.product/`. Designed to be read directly by AI sales agents, demo bots, and lead-qualification tools.

## Goals

- Every claim a sales agent might make should map to one field.
- Every field should be cheap to filter or look up.
- The schema should be flat enough to embed easily and structured enough to query.

## Top-level shape

```json
{
  "name": "string",
  "tagline": "string",
  "category": "string",
  "summary": "string",
  "target_customer": "string",
  "stage": "prototype | early | shipped | mature",
  "stack": {
    "languages": ["string"],
    "frameworks": ["string"],
    "datastores": ["string"],
    "deployment": "string"
  },
  "personas": [
    {
      "id": "kebab-case-id",
      "name": "string",
      "description": "string",
      "primary": true,
      "evidence": ["file path or route"]
    }
  ],
  "features": [
    {
      "id": "kebab-case-id",
      "name": "string",
      "description": "string",
      "area": "string",
      "maturity": "shipped | in-progress | experimental",
      "personas": ["persona-id"],
      "evidence": ["file path or route"]
    }
  ],
  "use_cases": [
    {
      "id": "kebab-case-id",
      "persona": "persona-id",
      "trigger": "string",
      "outcome": "string",
      "features_used": ["feature-id"]
    }
  ],
  "integrations": [
    {
      "name": "string",
      "category": "auth | payments | data | comms | storage | analytics | other",
      "direction": "inbound | outbound | bidirectional",
      "evidence": ["file path or env var"]
    }
  ],
  "differentiators": [
    {
      "claim": "string",
      "evidence": ["file path or route"]
    }
  ],
  "limitations": ["string"],
  "glossary": [
    {
      "term": "string",
      "definition": "string"
    }
  ],
  "open_questions": ["string"]
}
```

## Field rules

- **`id` fields** are kebab-case, stable, and unique within their array. Sales agents reference features and personas by id.
- **`evidence` arrays** must contain at least one entry for any claim. An empty `evidence` array means the claim is unverified — drop it or move it to `open_questions`.
- **`stage`** — overall product maturity, not per-feature.
- **`maturity`** — per-feature; "shipped" only if it's enabled by default in production config.
- **`personas[].primary`** — exactly one persona should be `primary: true`. Others default to false.
- **`limitations`** — plain strings, customer-readable. Honest gaps a sales rep should know before promising something.
- **`open_questions`** — gaps the analysis couldn't resolve from code alone. The sales team or PM should answer these.

## Validation

After writing the file:

1. Confirm it parses as JSON (no trailing commas, no comments).
2. Confirm every `feature-id` referenced in `use_cases[].features_used` exists in `features[]`.
3. Confirm every `persona-id` referenced in `features[].personas` and `use_cases[].persona` exists in `personas[]`.
4. Confirm exactly one persona has `primary: true`.
5. Confirm no `evidence` array is empty.

If any check fails, fix it before declaring the skill done.
