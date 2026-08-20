# Security Architecture

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

This document describes implemented control categories at an architectural level. It is not a penetration-test report, certification, or claim of absolute security.

| Control | Threat or category | General mechanism | Current verification |
|---|---|---|---|
| Customer session boundary | Cross-browser capability reuse | Production customer sessions use an HttpOnly, Secure, `__Host-` cookie with path-wide scope and SameSite=Lax behavior. Private capabilities require the server-derived session hash. | Automated security tests passed; production header behavior recorded |
| Session rotation | Reuse after sensitive rebinding | Security-sensitive recovery can rotate the customer session rather than preserving an old browser credential. | Automated security tests passed |
| Purchase and entitlement checks | Unpaid, expired, withdrawn, or revoked access | Generation, revision, signing, and download paths use the canonical paid-entitlement check, product availability, download flag, and validity window. | Automated security tests passed |
| Payment lifecycle | Refund, dispute, and chargeback access | Signed Stripe events transition purchase state and update entitlement state. Refunds and chargebacks disable new paid-product operations; duplicate events and event ordering are handled. | Source and security regression tests passed; database-backed/live money sequence remains owner work |
| Recovery credentials | Replay and browser rebinding | Recovery secrets are stored as hashes, have expiry/status, and are redeemed atomically once. | Automated security tests passed |
| Request-source rate limiting | Repeated expensive requests | Trusted client identity handling is used instead of accepting an arbitrary forwarding chain. Memory fallback is bounded and production uses shared storage. | Regression tests cover spoofed forwarding, operator bypass, disabled mode, expiry, and high cardinality |
| Customer-session assistant budget | IP rotation and inference spend | Ask Locke has a request-source limit and a separate customer-session budget. | Automated security tests passed |
| Input and output envelopes | Prompt injection and malformed model output | Request messages, fields, answers, catalog slugs, recommendations, and fill suggestions are bounded and allowlisted. | Assistant and security tests passed |
| Webhook authenticity | Forged payment transitions | Stripe webhook signatures are verified before lifecycle processing; event IDs are recorded for duplicate suppression. | Automated security tests passed |
| Signing integrity | Undetected document alteration | First-party signing records include SHA-256 hashes for the signed body and complete record, plus consent and signer metadata. A purchase has one final signing record. | E-sign and security tests passed |
| Response headers | Browser-side attack surface | Production responses set HSTS, `X-Content-Type-Options: nosniff`, frame denial, Referrer-Policy, Permissions-Policy, CSP, and private no-store handling on private routes. | Source and live header checks passed; CSP configuration remains under observation and tuning |
| Safe logging | PII and credential leakage through logs | Error records use an allowlisted, redacted shape; request bodies, document text, credentials, and database details are withheld. | Security tests passed |
| Analytics isolation | Sensitive data sent to analytics | Marketing pageview collection is allowlisted, query-free, consent-gated where applicable, and not mounted in private workflows. | Security tests passed |
| Development simulation gate | Production entitlement minting | Payment simulation requires the explicit development deployment authority and feature conditions; it is unavailable by default outside the intended tier. | Security tests passed |

## Security is an ongoing process

The current production record identifies remaining work: durable scheduled retention verification, controlled database-backed and live payment lifecycle smoke tests, application-wide OpenRouter/document/storage/emergency budgets, continued CSP observation and tuning, review of capability-bearing GET URLs, and remaining document, AI privacy, XSS, CI, and infrastructure audits. These are not hidden behind this summary.

The repository does not publish exact rate-limit values, secret formats, private endpoints, bypass research, exploit payloads, internal hostnames, or infrastructure topology that would materially assist abuse.
