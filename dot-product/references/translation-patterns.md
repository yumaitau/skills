# Translation Patterns

Extended lookup of common technical signals and the customer-facing language they map to. Use these as a starting point — adjust to the product's tone and the audience the sales team is selling to.

## Auth & identity

| Code signal | Customer framing |
|---|---|
| `passport`, `next-auth`, `auth0`, `clerk`, `supabase-auth` | "Sign in with your existing identity provider" |
| OAuth client for Google / Microsoft / Okta | "Single sign-on (SSO) with Google Workspace / Microsoft 365 / Okta" |
| SAML config or `saml2-js` | "Enterprise SSO via SAML" |
| MFA / TOTP libraries (`speakeasy`, `otplib`) | "Multi-factor authentication" |
| Magic-link login flow | "Passwordless sign-in" |
| Role/permission tables, `casl`, `casbin`, custom RBAC middleware | "Role-based access control" |

## Billing & monetisation

| Code signal | Customer framing |
|---|---|
| `stripe` SDK + webhooks | "Subscription billing and self-serve checkout" |
| `paddle`, `chargebee`, `recurly` | Same as above, name the provider only if relevant to the buyer |
| Usage-metering tables, `meter` events | "Usage-based pricing" |
| Coupon / discount logic | "Promotions and discount codes" |
| Tax handling (`stripe-tax`, `taxjar`) | "Tax-compliant invoicing" |

## Data & integrations

| Code signal | Customer framing |
|---|---|
| Webhook receiver endpoints | "Inbound webhooks for real-time events" |
| Outbound webhook delivery | "Outbound webhooks to your systems" |
| CSV / XLSX import & export | "Bulk import and export" |
| OpenAPI spec, public API key management | "Public API for custom integrations" |
| Zapier / Make / n8n connector | "No-code automation via Zapier" |
| iCal feed, ICS generation | "Calendar sync" |

## Comms

| Code signal | Customer framing |
|---|---|
| `sendgrid`, `postmark`, `resend`, `ses` | "Transactional email" |
| `twilio` SMS / voice | "SMS notifications" |
| Slack webhook / app | "Slack notifications" |
| Push notification SDKs (`fcm`, `expo-notifications`, `apn`) | "Mobile push notifications" |

## Storage & files

| Code signal | Customer framing |
|---|---|
| `@aws-sdk/client-s3`, `gcs`, `azure-blob` | "Secure cloud storage for uploads" |
| Presigned URL generation | "Direct, secure file uploads" |
| PDF generation (`puppeteer`, `pdfkit`, `weasyprint`) | "PDF reports and document generation" |
| Image processing (`sharp`, `imagemagick`) | "On-the-fly image transformation" |

## Performance & scale

| Code signal | Customer framing |
|---|---|
| Multi-region deployment config | "Multi-region hosting" |
| Read replicas, sharding | "Built to scale with your usage" — only if backed by load characteristics |
| Background workers (`bullmq`, `sidekiq`, `celery`) | "Asynchronous processing for heavy tasks" |
| WebSockets / SSE | "Live updates without page refresh" |
| Rate limiting middleware | "Per-tenant rate limits" — only relevant for API products |

## Security & compliance

| Code signal | Customer framing |
|---|---|
| Audit-log table or `audit_logs` writer | "Audit logging for compliance" |
| `argon2`, `bcrypt` hashing | Don't surface — table stakes |
| Encryption at rest config (KMS, encrypted columns) | "Encryption at rest" |
| TLS-only ingress | Don't surface — table stakes |
| GDPR-related routes (`/data-export`, `/data-deletion`) | "GDPR-ready data export and deletion" |
| SOC 2 / ISO references in docs | Mention only if you can verify the certification, not just intent |

## Multi-tenancy

| Code signal | Customer framing |
|---|---|
| `organisation_id` / `workspace_id` on every model | "Built for teams — isolated workspaces" |
| Invite flow with email + role | "Invite teammates by email with role assignment" |
| Per-tenant subdomains or custom domains | "Custom domains per workspace" |

## Anti-patterns — don't surface these

These are infrastructure choices, not selling points. Mentioning them looks naive and clutters the doc.

- HTTPS / TLS
- Password hashing
- Use of a database
- Use of a framework (React, Next.js, Django) — unless the buyer is a developer
- Use of git / CI / Docker
- "Cloud-hosted" as a feature

## Yuma-specific overrides

If a Yuma product re-uses a stock pattern but markets it under a specific name, list the override here so future runs of this skill produce consistent language.

_None yet — add as products onboard._
