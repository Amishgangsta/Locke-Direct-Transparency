# System Overview

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

## Service components

Locke Direct combines a public web application, a curated product catalog, structured questionnaires, a jurisdiction model, deterministic document assembly, purchase and entitlement controls, and delivery services. The customer-facing application is hosted on Railway. Stripe processes payment events. Ask Locke uses OpenRouter and a selected model provider only when the customer invokes the assistance feature. Public marketing analytics are isolated from private product workflows.

## Customer path

1. A customer selects a product from the public catalog.
2. The workflow asks for state first when jurisdiction is relevant, followed by county or address context when the product requires more local information.
3. The customer completes a structured questionnaire. Authored visibility, requiredness, validation, and consistency rules govern the workflow.
4. The application produces a preview from the same maintained content and assembly model used for final output.
5. Checkout creates a pending purchase and requires the current platform disclaimer acknowledgment.
6. Stripe confirmation changes the purchase to paid and creates an active entitlement.
7. Final generation, revision, signing, and download paths re-check the entitlement, product availability, session binding, and relevant expiration state.
8. PDF and DOCX exports are produced from the shared rendered representation. Multi-document products are delivered as named document packages.

## Trust boundaries

| Boundary | Responsibility |
|---|---|
| Browser | Holds questionnaire answers and draft interaction state where the workflow allows; sends only the data needed for server assembly or requested assistance |
| Locke Direct application | Validates inputs, applies catalog and jurisdiction decisions, assembles documents, enforces sessions and entitlements, and mediates external services |
| Database/storage | Holds operational records, purchase and entitlement state, selected draft metadata, expiring generated content, and integrity records according to the retention design |
| Stripe | Processes payment information and emits signed lifecycle events; full card details are not stored by Locke Direct |
| OpenRouter/model provider | Receives Ask Locke prompts and bounded context when the customer uses the feature; it is not the source of final legal-document structure |
| Analytics | Receives limited, consent-gated public marketing pageview data; private workflows are excluded |

See [architecture diagrams](architecture/README.md) for the system, document, AI, and data flows.

## Product and readiness authorities

The production implementation keeps pricing, product readiness, public page registration, and disclaimer wording as separate authorities. A product is not purchasable merely because a database row exists; the customer-facing readiness decision must also permit it. Unknown products fail closed. This separation is intended to prevent copy, pricing, or database drift from silently making unfinished content purchasable.

## Operational identity

The official public service is `www.lockedirect.com` (the apex redirects to the canonical host). The public health response exposes only a minimal healthy/unhealthy status. Detailed operational checks require an operator-controlled path and are not part of this public documentation.
