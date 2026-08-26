# Release Verification

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development LLC
**Official site:** <https://www.lockedirect.com>
**Transparency snapshot refreshed:** 2026-08-26

## Current release line

The currently documented application release-line revision is `0d27e70`. The previous complete recorded verification sequence was performed against `e09c077` on 2026-08-20.

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
