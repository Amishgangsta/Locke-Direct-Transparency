# Release and storefront evidence — keep historical results distinct

## Public storefront snapshot — October 31, 2026

The current live storefront advertises **134 public product listings** and a four-tier pricing ladder: **FREE ($0), $14.99, $24.99, $49.99**. The pricing page also advertises **one included revision** for free self-guided products and **unlimited revisions for 30 days** for paid tiers. The public Privacy Policy describes browser-local drafts, bounded server assembly, purchased-content retention, and consent-gated public-page analytics.

These items were checked against the publicly served [catalog](https://www.lockedirect.com/agreements), [pricing](https://www.lockedirect.com/pricing), and [privacy policy](https://www.lockedirect.com/privacy). Private source review confirmed the canonical price constants and the validated $0 entitlement branch.

**No new full-suite test run, live payment smoke test, independent penetration test, or Railway deployment verification was performed for this documentation update.** The precise currently deployed Git commit and all current live integrations remain unverified here.

## Historical release evidence — August 2026

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development LLC
**Official site:** <https://www.lockedirect.com>
**Transparency snapshot refreshed:** 2026-08-26

## Previously documented release line (historical)

The application release-line revision documented in August 2026 was `0d27e70`. The previous complete recorded verification sequence was performed against `e09c077` on 2026-08-20.

Post-August-20 releases added the current revision-entitlement model, the standalone Living Will / Health Care Declaration, pinned official/statutory living-will implementations for Connecticut, Illinois, Arizona, Florida, and California, and updated Terms/operator/support wording. Later changes through `0d27e70` also include UI-only fixes.

A fresh complete verification run has not been published in this repository for `0d27e70`. Accordingly, the August 20 test figures below are retained as historical release evidence and are not represented as verification of the later release line.

## Previous complete verification record — 2026-08-20

| Check | Result |
|---|---|
| Verified release revision | `e09c077` |
| Production deployment | Railway deployment completed successfully on 2026-08-20 |
| Migration startup | Passed; migration folder `drizzle` reported `ok` |
| Production server | Started successfully |
| Live health | `https://lockedirect.com/api/health` returned healthy HTTP 200 after canonical redirect handling |
| HSTS | Verified: `max-age=31536000; includeSubDomains` |
| Private cache behavior | Verified: private no-store headers on the health response; private-route handling is implemented in the response proxy |
| Application tests | 848/848 passed |
| Security tests | 98/98 passed |
| Document tests | 376/376 passed |
| Typecheck | Passed |
| Lint | Passed |
| Preflight | Passed in the release verification sequence |
| Production build | Passed in the release verification sequence |
| Dependency audit | Production-only and full `npm audit` both reported 0 vulnerabilities on 2026-08-20 |

## What this does not establish

The August 20 deployment and health check establish source/deployment and basic runtime availability for that verified release, not independent security certification, perfect behavior on every device, a controlled real-money transaction, or legal enforceability of every document. They also do not establish that the same test totals apply unchanged to later revisions. Public release records should be read with [Limitations](LIMITATIONS.md).
