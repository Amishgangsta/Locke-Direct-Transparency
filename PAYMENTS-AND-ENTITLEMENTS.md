# Payments, free access, and revision entitlements

**Updated for public pricing:** 2026-10-31 · **Operator:** Locke Development LLC · [Live pricing](https://www.lockedirect.com/pricing)

## Four-tier entitlement model

| Product tier | One-time price | Included revision terms | Checkout |
|---|---:|---|---|
| Self-Guided | **FREE ($0)** | **1 revision** | Validated no-charge entitlement; no Stripe charge |
| Customized | **$14.99** | Unlimited revisions for **30 days after purchase** | Stripe |
| Advanced | **$24.99** | Unlimited revisions for **30 days after purchase** | Stripe |
| Complete Package | **$49.99** | Unlimited revisions for **30 days after purchase** | Stripe |

The paid 30-day period is a revision window, **not a subscription**. A completed paid purchase retains the revision terms applicable to that purchase, even if later catalog pricing changes. Existing historical purchases may carry original price/entitlement rules.

## Free-document path — source-reviewed

For a $0 catalog product, the same customer-session, document validation, disclaimer-acceptance, purchase and entitlement checks precede the no-charge completion. The checkout route explicitly detects a zero-cent purchase and completes it through the internal purchase-entitlement transition, returning `mode: "free"`. **There is no Stripe payment session or card charge for that free branch.** Product readiness and entitlement rules still apply. A free product is not an unrestricted bypass of application controls.

## Paid checkout — source-reviewed

For paid products, the server checks the selected product, validated questionnaire answers, current readiness, applicable price, browser-scoped purchase identity, and explicit disclaimer acceptance before initiating a Stripe payment session. Signed Stripe webhooks and idempotent lifecycle processing update purchase and entitlement state. Entitlements govern generation, revision, signing and download. Refund, dispute and chargeback handling can restrict access.

## Recovery and customer control

Recovery secrets are hashed, time-limited and single-use for browser rebinding. The product offers PDF and DOCX downloads and limited first-party e-signing; signing is not represented as independent multi-party identity authentication.

## Evidence boundary

Prices and revision terms were observed on the live site October 31, 2026; the $0 branch was reviewed in the private application's checkout source. No live real-money charge, refund, chargeback or complete production end-to-end sequence was executed for this documentation change. See [Security architecture](SECURITY-ARCHITECTURE.md), [Privacy-first boundaries](PRIVACY-FIRST.md), and [Historical release verification](RELEASE-VERIFICATION.md).
