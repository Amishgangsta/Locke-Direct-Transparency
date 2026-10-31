# Locke Direct — system and workflow overview

**Public storefront observed:** October 31, 2026 · **Implementation:** private, source-reviewed; no source distributed here.

Locke Direct is a privacy-conscious legal-document assembly platform for consumers and small businesses, combining **guided interviews**, **optional Ask Locke assistance**, **jurisdiction context**, and **deterministic outputs**. The production application runs on Railway; paid purchases use Stripe.

## User journey

1. **Choose a product:** browse 134 public listings or ask Ask Locke to identify an existing relevant product.
2. **Select the applicable jurisdiction:** state first when required; county/address context for products that need it.
3. **Answer questions:** Self-Guided captures facts the customer already knows; higher tiers add clause choices, issue identification, contingencies, role-specific prompts, and coordinated document schedules.
4. **Validate and preview:** required answers and consistency rules are applied to maintained content, not left to free-form model generation.
5. **Unlock with appropriate entitlement:** a $0 product follows the validated free entitlement path; $14.99 / $24.99 / $49.99 products proceed through paid Stripe checkout. Server-verified disclaimer acceptance is required.
6. **Receive outputs:** download PDF and editable DOCX, use supported first-party signing functions, and access the revision allowance for the selected tier.

## Engineering boundaries

| Boundary | Responsibility |
|---|---|
| Customer browser | Local draft interaction and questionnaire answers before server-side assembly |
| Document application | Input validation, jurisdiction decisions, maintained clause/structure assembly, and export |
| Product authorities | Separate canonical price, readiness, public catalog registration and disclosure authorities |
| Assistant | Optional document recommendations and field help, parsed into catalog/field-constrained suggestions; no authority over final legal clauses |
| Database/storage | Purchase, entitlement, revision, signing-integrity and permitted completed-content retention |
| Stripe | Paid payment processing, with signed lifecycle events; no full card storage in the app |
| OpenRouter / model provider | Requested Ask Locke messages and bounded context on ZDR-requested routes |
| Marketing analytics | Consent-controlled, allowlisted public-page metrics without form, payment, document or assistant messages |

## Guidance depth is deliberate

**Free Self-Guided:** known facts and essentials → **Customized:** define selected terms → **Advanced:** surface issues and contingencies → **Complete Package:** assess the user's role and coordinate companion documents. Price reflects help/scope, not the importance of someone's legal situation.

## Key implementation assurances and limits

Final documents are assembled by deterministic rules from maintained content, jurisdiction support, and validated answers. PDF and DOCX share a rendered representation. Private workflow routes are excluded from marketing-page analytics. Customer content is processed and retained as described in the [live Privacy Policy](https://www.lockedirect.com/privacy); it is not accurate to call the system entirely browser-only or zero-retention.

[Ask Locke and guided workflows](ASK-LOCKE-AND-GUIDED-WORKFLOWS.md) · [Privacy-first architecture](PRIVACY-FIRST.md) · [Payments and entitlements](PAYMENTS-AND-ENTITLEMENTS.md).
