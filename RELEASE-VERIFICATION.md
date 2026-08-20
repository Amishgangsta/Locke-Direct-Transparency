# Release Verification

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

## Current release

The current public-safe application revision is `e09c077`, which includes the verified mobile Ask Locke behavior after the security release line. The preceding dated project-status record identifies `0960ae6` as the security remediation release; this transparency record uses the later verified revision rather than preserving the stale pointer.

| Check | Result |
|---|---|
| Release revision | `e09c077` |
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

The deployment and health check establish source/deployment and basic runtime availability, not independent security certification, perfect behavior on every device, a controlled real-money transaction, or legal enforceability of every document. Public release records should be read with [Limitations](LIMITATIONS.md).
