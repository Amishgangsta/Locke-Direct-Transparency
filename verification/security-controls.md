# Security Controls Verification

**Verified:** 2026-08-20
**Application revision:** `e09c077`

| Control | Purpose | Current status | Last verified |
|---|---|---|---|
| HttpOnly production customer session | Prevent script access to the customer capability cookie | Implemented and security-tested | 2026-08-20 |
| `__Host-` cookie semantics | Restrict cookie scope and require secure path-wide behavior | Implemented and security-tested | 2026-08-20 |
| Session-bound private capabilities | Prevent a capability from being used in an unrelated browser session | Implemented and security-tested | 2026-08-20 |
| Expiring, hashed, single-use recovery | Reduce recovery replay and plaintext-secret exposure | Implemented and security-tested | 2026-08-20 |
| Payment state and entitlement revocation | Disable new paid operations after refund/chargeback/revocation | Implemented and security-tested; live transaction sequence remains owner work | 2026-08-20 |
| Stripe signature and duplicate-event handling | Reject forged or repeated webhook transitions | Implemented and security-tested | 2026-08-20 |
| Trusted rate-limit identity and bounded memory | Limit abuse without arbitrary forwarding-header trust | Implemented and security-tested | 2026-08-20 |
| Ask Locke session budget | Add a customer-session spend boundary beyond request-source limiting | Implemented and security-tested | 2026-08-20 |
| Safe redacted logging | Reduce PII, secret, and database-detail leakage | Implemented and security-tested | 2026-08-20 |
| HSTS and browser response headers | Reduce transport and browser embedding/content risks | Implemented; live HSTS verified | 2026-08-20 |
| CSP | Restrict script, frame, object, form, and connection sources | Implemented in report/observation mode; tuning remains ongoing | 2026-08-20 |
| Analytics isolation | Keep private workflow data out of pageview analytics | Implemented and security-tested | 2026-08-20 |
