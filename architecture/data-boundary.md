# Data Boundary

**Last verified:** 2026-08-20

```mermaid
flowchart LR
  B[Customer browser]
  A[Locke Direct application]
  DB[Operational database/storage]
  ST[Stripe]
  OR[OpenRouter / selected model provider]
  GA[Consent-gated public analytics]

  B -->|questionnaire and requested workflow data| A
  A -->|temporary assembly and operational records| DB
  A <-->|signed payment lifecycle events| ST
  A -->|Ask Locke messages and bounded context only when invoked| OR
  B -->|allowlisted query-free public pageview| GA
  A -->|private routes excluded from analytics| GA
```

This diagram describes data categories and trust boundaries, not a complete network topology. It intentionally omits private hostnames, credentials, internal endpoints, and storage identifiers.
