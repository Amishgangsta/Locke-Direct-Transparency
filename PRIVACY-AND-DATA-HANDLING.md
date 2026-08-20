# Privacy and Data Handling

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

The live [Privacy Policy](https://www.lockedirect.com/privacy) is the governing consumer-facing policy. This document summarizes implementation-derived data flows and distinguishes processing, transmission, storage, retention, and analytics.

| Data category | Purpose | Where handled | Third party | Retention/current boundary |
|---|---|---|---|---|
| Browser-local draft answers | Let a customer complete and revise a questionnaire | Customer browser and server assembly request when output is requested | None for browser storage itself | Answers are designed to remain browser-local and are not persisted in draft metadata; server transmission occurs for assembly |
| Draft metadata | Resume limited workflow state and authorize operations | Locke Direct application/database | Railway operates the service | Non-sensitive progress metadata has a documented expiration window |
| Generated document text | Deliver a requested preview or final file | Locke Direct application/database/storage | Railway operates the service | Final generated content is temporary and is deleted after the single-use download or scheduled retention window, subject to operational cleanup |
| Payment information | Complete a purchase | Stripe checkout/payment systems | Stripe | Locke Direct does not store full payment card details; purchase and entitlement records remain for operation and support |
| Purchase and entitlement records | Prove payment, revisions, download state, and lifecycle | Locke Direct application/database | Railway operates the service; Stripe supplies lifecycle events | Retained according to operational and privacy requirements |
| Ask Locke messages and bounded context | Provide document selection and form guidance | Browser, Locke Direct route, OpenRouter, selected model provider | OpenRouter and selected provider | Current implementation does not store the conversation on Locke Direct servers; provider routing and retention are governed by configured route controls and the Privacy Policy |
| Customer session | Bind private capabilities to the browser session | HttpOnly browser cookie and server-side hash | Railway operates the service | Cookie has a finite production lifetime; sensitive rebinding can rotate it |
| Recovery information | Restore a paid purchase to a browser | Locke Direct application/database | Railway operates the service | Recovery secrets are hashed, expiring, and single-use after redemption |
| Signing records | Preserve consent, signer metadata, signed text hashes, and final-record integrity | Locke Direct application/database and delivered record | Railway operates the service | Retained as purchase/signing evidence according to operational policy |
| Operational logs | Diagnose errors and protect service | Locke Direct logging path | Railway operates the service | Safe, redacted records; document content, questionnaire answers, credentials, and database details are excluded |
| Marketing pageview data | Understand visits to public information and catalog pages | Marketing analytics component and configured analytics service | Isolated self-hosted analytics and, when configured, Google Analytics 4 | Consent-gated where configured; query-free allowlisted paths only |

## Analytics boundary

Analytics is mounted in the marketing shell, not the shared private application root. Pageviews are limited to allowlisted public information/catalog routes. The payload is query-free and does not include questionnaire answers, names, addresses, Ask Locke messages, payment information, or document contents. Google advertising features, Signals, and ad personalization are disabled in the current implementation.

## AI transmission boundary

Ask Locke is different from analytics. When a customer invokes it, the message and bounded functional context are sent to OpenRouter and the selected model provider. A customer should not put information into Ask Locke that they do not want processed for that assistance request. See [AI Boundaries](AI-BOUNDARIES.md).

## Policy and implementation caveat

Implementation-derived statements can change. If the live Privacy Policy and this technical summary diverge, the discrepancy should be reported and the consumer-facing policy should be treated as governing until corrected.
