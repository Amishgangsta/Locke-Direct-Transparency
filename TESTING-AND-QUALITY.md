# Testing and Quality

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

## Current automated results

| Suite/check | Result | What it covers at a high level |
|---|---:|---|
| Application test suite | 848/848 passed | Catalog, routing, pricing, readiness, assistant boundaries, product workflows, SEO, and regression coverage |
| Focused security suite | 98/98 passed | Sessions, payments, recovery, rate limiting, safe logging, analytics isolation, headers, entitlement and review controls |
| Document suite | 376/376 passed | Product parity, questionnaire mapping, conditions, package boundaries, PDF/DOCX completeness, rendering and guidance rules |
| TypeScript typecheck | Pass | Static type checking without emitting build files |
| Lint | Pass | Repository lint rules |
| Preflight | Pass | Launch-gating checks including catalog, pricing, publication and related integrity checks |
| Production build | Pass | Production application build in the release verification sequence |
| `npm audit --omit=dev` | 0 reported vulnerabilities | Production dependency audit on 2026-08-20 |
| `npm audit` | 0 reported vulnerabilities | Full dependency audit on 2026-08-20 |

## Test categories

The automated suites include tests for pricing consistency, product readiness, catalog integrity, questionnaire/placeholder parity, deterministic assembly, multi-document packages, PDF/DOCX behavior, jurisdiction flows, customer authorization, payment transitions, session security, recovery security, signing integrity, entitlement revocation, safe logging, and security headers.

Test counts describe automated verification coverage. They should not be interpreted as proof that the software is defect-free, that every jurisdictional outcome is correct, or that a live payment provider sequence has been executed.

## Privacy of the test record

This repository publishes counts and categories, not private test source, customer data, credentials, exploit payloads, proprietary clauses, or detailed bypass procedures.
