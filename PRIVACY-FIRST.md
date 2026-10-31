# Privacy-first design: Locke Direct

**The product differentiator:** useful guided legal-document preparation **without turning a customer's private document, questionnaire, or AI conversation into marketing analytics**.

Locke Direct's privacy architecture is based on **separation of purpose**: create the user's document; protect purchase/signing rights; provide optional AI help; measure permitted public marketing pages. Those jobs have distinct boundaries.

## Five practical protections

1. **Draft locally:** answers remain browser-local during normal drafting. They move to the server when document assembly is requested, rather than being automatically reported as analytics events.
2. **Keep private routes out of analytics:** marketing analytics is restricted to approved public paths and a query-free pageview contract. It excludes questionnaire answers, documents, names, payment details and Ask Locke messages.
3. **Make analytics optional:** the source-reviewed gating requires affirmative user approval and respects rejection, DNT, GPC and unavailable storage. It avoids session replay, heatmaps and ad personalization in the documented configuration.
4. **Constrain AI assistance:** Ask Locke is invoked voluntarily, uses a bounded context and requests zero-data-retention provider processing. Its recommendations are catalog/field-constrained; deterministic assembly remains separate.
5. **Protect entitlements and downloads:** server-scoped sessions, access rechecks, hashed time-limited recovery tokens, signing integrity and short-lived downloadable artifacts protect legitimate document access.

## Example: a customer preparing a lease

A customer begins in the browser, chooses a state and fills out the lease interview. The answers are sent to the application for requested assembly, **not sent to marketing analytics**. The assembled document is displayed for review; paid access uses Stripe, while free items have a no-charge entitlement path. Purchased final content may be retained so the customer can revisit deliverables and use revisions; disposable download copies and access links expire under the published policy.

If the customer chooses to use Ask Locke for help, only the voluntarily supplied chat text and bounded relevant context go to OpenRouter and a model provider; this is an external AI transmission, not a local-only process.

## Why the boundary matters

The system is designed to avoid conflating **product usage** with **marketing surveillance** or conflating **AI responses** with authoritative legal drafting. It offers a disciplined engineering approach to privacy-sensitive consumer software.

## Precise limits

Privacy-first does **not** mean no server processing, no records, no third-party processors, or certified security. Operational records, purchased content, payments and provider transmissions exist within defined purposes. The [live privacy policy](https://www.lockedirect.com/privacy) details retention and processors; this repository publishes architecture and historical evidence, not a formal audit.

[Security controls](SECURITY-ARCHITECTURE.md) · [Full data-handling detail](PRIVACY-AND-DATA-HANDLING.md) · [Ask Locke](AI-BOUNDARIES.md).
