# Locke Direct

> Public technical reference for Locke Direct. This repository contains documentation, not application source code.

**Operator:** Locke Development LLC  
**Official site:** <https://www.lockedirect.com>  
**Support:** support@lockedirect.com  
**Repository type:** Public technical and operational reference  
**Source code:** Not included  
**Last verified:** 2026-08-20

## What Locke Direct is

Locke Direct is a consumer self-service legal-document preparation platform. A customer selects a document or package, selects a jurisdiction where the workflow requires it, completes a structured plain-language questionnaire, reviews the result, completes a one-time purchase, and receives supported deliverables such as PDF and DOCX. Available products also expose revision and first-party electronic-signing functions within their defined scope.

The final document is assembled from maintained document structures, clause content, questionnaire answers, and applicable jurisdiction data. The core legal-document assembly path is deterministic; it is not an unrestricted request for an AI model to invent a legal instrument from scratch.

## What Locke Direct is not

- Locke Direct is not a law firm and does not represent customers as legal counsel.
- It does not provide legal advice or guarantee that a document is valid or enforceable in a particular situation.
- Ask Locke is an assistance layer for document selection and form guidance, not the authoritative legal-document generator.
- This repository is not an open-source distribution of the product and contains no proprietary application source, templates, prompts, customer records, or credentials.

## Current production snapshot

These figures were checked against the private production implementation, current tests, and the production deployment record on 2026-08-20.

| Item | Verified state |
|---|---|
| Curated catalog | 117 products |
| Production availability | 117 available; 0 remaining in a non-available readiness state |
| Price levels | $5.99, $29.99, $49.99, $99.99 |
| Application tests | 848/848 passed |
| Focused security tests | 98/98 passed |
| Document tests | 376/376 passed |
| TypeScript typecheck | Passed |
| Lint | Passed |
| Launch preflight | Passed |
| Production build | Passed in the recorded release verification sequence |
| Dependency audit | `npm audit --omit=dev`: 0; full `npm audit`: 0 on 2026-08-20 |
| Hosting | Railway, verified from the production deployment record |
| Payment processor | Stripe, configured in production; no real-money transaction was part of the latest controlled verification sequence |
| Security headers | HSTS, `X-Content-Type-Options`, frame denial, referrer and permissions policies verified |
| Search indexing | Enabled for the production site |
| Production application revision | `e09c077` |

The four price-level counts are 21 products at $5.99, 62 at $29.99, 18 at $49.99, and 16 at $99.99. Product count and document count are different: some products deliver multi-document packages.

## Business identity and contact

Locke Direct is operated by **Locke Development LLC**, a Tennessee limited liability company. The current Locke Direct customer-support mailbox is **support@lockedirect.com**.

The public Terms of Use and other policy pages remain the controlling source for customer-facing legal terms. This repository does not replace those policies.

## High-level architecture

```mermaid
flowchart TD
  C[Customer browser] --> W[Public Locke Direct web application]
  W --> P[Product and jurisdiction selection]
  P --> Q[Structured plain-language questionnaire]
  Q --> V[Validation and applicable rules]
  V --> A[Deterministic document assembly]
  A --> R[Shared rendered document representation]
  R --> E[PDF / DOCX / package export]
  W -. assistance only .-> L[Ask Locke]
  L -. recommendations and form guidance .-> W
```

## Documentation index

- [System overview](SYSTEM-OVERVIEW.md)
- [Document assembly](DOCUMENT-ASSEMBLY.md)
- [AI boundaries](AI-BOUNDARIES.md)
- [Security architecture](SECURITY-ARCHITECTURE.md)
- [Privacy and data handling](PRIVACY-AND-DATA-HANDLING.md)
- [Payments and entitlements](PAYMENTS-AND-ENTITLEMENTS.md)
- [Jurisdiction model](JURISDICTION-MODEL.md)
- [Testing and quality](TESTING-AND-QUALITY.md)
- [Product catalog](PRODUCT-CATALOG.md)
- [Limitations](LIMITATIONS.md)
- [Release verification](RELEASE-VERIFICATION.md)
- [Facts](FACTS.md)
- [Responsible disclosure](RESPONSIBLE-DISCLOSURE.md)
- [Architecture diagrams](architecture/README.md)
- [Verification records](verification/README.md)
- [Changelog](CHANGELOG.md)

## Independent verification resources

- [Official Locke Direct site](https://www.lockedirect.com)
- [Public product catalog](https://www.lockedirect.com/agreements)
- [Privacy policy](https://www.lockedirect.com/privacy)
- [Terms](https://www.lockedirect.com/terms)
- [Refund policy](https://www.lockedirect.com/refund-policy)
- [This repository's commit history](https://github.com/Amishgangsta/Locke-Direct-Transparency/commits/main)

The production implementation is maintained in a separate private repository. Implementation-derived statements in this repository are identified as maintainer-verified rather than independently audited. Publicly observable evidence includes the official site, public policies, catalog, this repository, and its commit history.

## Corrections

If information in this repository appears inaccurate, incomplete, or outdated, open a GitHub issue with the relevant source or observation. Do not put credentials, customer information, exploitable security details, or proof-of-concept attacks in a public issue. Verified corrections will be incorporated into the documentation history.
