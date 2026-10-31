# Locke Direct — current public workflow diagram

**Dated public catalog/pricing observation:** October 31, 2026. This high-level flow omits private routes, secrets, and internal infrastructure detail.

```mermaid
flowchart TD
  U[Customer] --> C[Public catalog: 134 products]
  U -. optional discovery .-> L[Ask Locke: document picker]
  L -. available product suggestion .-> C
  C --> Q[State-aware, plain-English questionnaire]
  Q -. optional constrained form help .-> H[Ask Locke: field guidance]
  H -. schema-checked suggestion .-> Q
  Q --> V[Required-field and consistency validation]
  V --> A[Deterministic document assembly]
  A --> P[Preview and disclaimer]
  P --> E{Canonical product price}
  E -->|Free, $0| F[Validated free entitlement]
  E -->|Paid tier| S[Stripe checkout]
  S --> R[Verified paid entitlement]
  F --> D[PDF, DOCX, supported e-sign and revisions]
  R --> D
  Q -. excluded .-> X[Marketing analytics]
  D -. excluded .-> X
```

Marketing analytics runs only in a separately gated public marketing context, with affirmative consent and an allowlisted query-free pageview contract; private document and Ask Locke content are not eligible analytics events.

[System overview](../SYSTEM-OVERVIEW.md) · [Privacy-first architecture](../PRIVACY-FIRST.md) · [AI boundaries](../AI-BOUNDARIES.md).
