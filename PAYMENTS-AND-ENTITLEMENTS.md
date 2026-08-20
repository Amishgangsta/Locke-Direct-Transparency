# Payments and Entitlements

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

## One-time checkout

Locke Direct lists one-time document and package prices. A checkout attempt is bound to the customer browser session and the selected product. The checkout route validates product readiness, price/currency, disclaimer acknowledgment, same-origin conditions, and the configured canonical application URL before creating a Stripe payment session.

Stripe processes payment information. Locke Direct does not store full payment card details. Stripe returns signed lifecycle events to the webhook route.

## Purchase state

The production data model has explicit payment states:

`pending` → `paid` → `refunded` / `partially_refunded` / `disputed` / `chargeback` / `revoked`

The exact legal transition depends on the incoming event and recorded event time. A later event cannot casually reactivate a terminal revoked or charged-back purchase. A dispute that is resolved in the merchant's favor can restore the paid state under the implemented transition rules.

## Entitlement state

Entitlements separately track `active`, `suspended`, `revoked`, and `expired`. Paid confirmation creates an active entitlement. Refunds and chargebacks disable new downloads and other paid-product operations according to the lifecycle state. Partially refunded purchases suspend access rather than silently continuing as fully active. Every protected operation re-checks current entitlement state, download permission, validity, and product availability.

## Webhook handling

The webhook path verifies Stripe signatures, suppresses duplicate event IDs, validates checkout session identity/amount/currency/metadata, and records event ordering. It handles checkout completion, refunds, and dispute creation/closure. The latest source and security tests cover duplicate and reordered event behavior; a controlled database-backed and live-money sequence remains an owner operational verification item.

## Recovery

Recovery is proof of a paid purchase, not a permanent account credential. The recovery secret is stored only as a hash, expires, and can be redeemed once through an atomic update. Successful redemption binds the purchase to the current browser session. A stale, expired, or concurrently redeemed recovery secret is rejected.

## Verification boundary

The latest release verification confirmed configuration and automated lifecycle enforcement. It did not execute a real-money Stripe charge as part of the controlled smoke sequence. That distinction is maintained here deliberately.
