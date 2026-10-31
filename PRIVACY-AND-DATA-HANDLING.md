# Privacy and data handling — accurate retention and transmission boundaries

**Reviewed:** October 31, 2026 against the [live Privacy Policy](https://www.lockedirect.com/privacy) and private implementation descriptions. This document summarizes architecture; the posted policy governs.

Locke Direct's privacy-first approach emphasizes **data minimization, purpose separation, explicit analytics consent, guarded access, and bounded retention**. It does not claim that requested server assembly is browser-only, that purchased content immediately disappears, or that external processors are never involved.

| Information | Intended processing and storage boundary |
|---|---|
| In-progress questionnaire answers | Browser-local while drafting; transmitted for requested server-side assembly. Sensitive answers are not persisted in ordinary draft metadata. |
| Draft metadata | Limited progress metadata, with a documented 30-day expiration window. |
| Completed purchased document and validated purchase answers | Retained to support active purchase access, recovery, revisions and latest deliverables, subject to entitlement/retention lifecycle. |
| Disposable download copies | Temporary, expiring within 24 hours; links are short-lived and single-use under the posted policy. |
| Superseded answers/content | Removed after revision rights end under the documented retention lifecycle; latest deliverables and relevant payment/signing integrity records are retained as stated in the posted policy. |
| Payment credentials | Full card details are processed by Stripe, not stored by Locke Direct. Operational purchase and entitlement data is retained. |
| Ask Locke messages | Customer-entered messages and bounded context go through OpenRouter to a selected model provider on zero-data-retention-requested routes. Locke Direct does not store its own chat transcript. |
| Marketing analytics | Explicit opt-in, limited public page titles and query-free path measurements; excluded from forms, completed documents, paid workflows, and Ask Locke messages. |
| Session and recovery | Scoped secure session handling; hashed, expiring, single-use recovery credentials. |
| Operational diagnostics | Allowlisted/redacted logs; document text, answers, secrets and payment details are not intended as diagnostic payloads. |

## Analytics isolation

Public marketing analytics may use a self-hosted provider and configured Google Analytics 4. The recorded source implementation requires affirmative consent, honors **Do Not Track** and **Global Privacy Control**, and fails closed when consent storage is unavailable. It avoids advertising personalization and restricts measurement to allowlisted public pageviews. Analytics services may still receive technical request metadata (for example an IP address and browser details); the product does **not** claim traffic is wholly anonymous to every processor.

No questionnaire values, Ask Locke content, names, addresses, card information, or completed document text are part of the intended analytics payload. The sensitive workflow routes are excluded from the public measurement component.

## AI processing is separate from analytics

Ask Locke is optional. Its prompt and message context are deliberately narrower than the complete questionnaire and are transmitted to an external provider only when the feature is used. The provider's requested zero-data-retention behavior is distinct from the application's own storage policy.

## Customer documents are not zero-retention

The live policy expressly retains the latest completed purchased content while access is active and stores validated checkout information needed for entitlements and revisions. Older documentation describing all final content as deleted immediately after delivery is **superseded** by this accurate distinction.

## Verification and policy boundaries

These are architecture descriptions compared with accessible private source and the public policy, not a third-party privacy audit. The actual external-service configuration and operations may require additional provider-level verification. For customer rights, deletion requests, and the current contractual policy, see https://www.lockedirect.com/privacy.

[Privacy-first overview](PRIVACY-FIRST.md) · [Security architecture](SECURITY-ARCHITECTURE.md) · [AI boundaries](AI-BOUNDARIES.md).
