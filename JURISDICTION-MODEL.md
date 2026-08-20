# Jurisdiction Model

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

## State-first workflow

For jurisdiction-aware workflows, Locke Direct asks for state before the remainder of the jurisdiction context. County and address information are requested where the workflow needs more local context. The application does not silently infer a required state selection from an arbitrary request or host value.

## State content and rules

The private implementation maintains a canonical state registry, state-specific content packs, jurisdiction gate questions, and jurisdiction decision logic. A selected state is passed through the workflow and attached to the assembly context when applicable. The resulting document still depends on the customer's answers and the product's authored scope.

General-form exceptions are differentiated from products that require a state instance. A general form is not presented as state-specific merely because the customer is located in a state. Products that require jurisdiction context are blocked until the required authored jurisdiction information is available.

## Operational responsibility

Jurisdiction-specific requirements change. Maintaining state and local content is an ongoing operational responsibility; automated tests establish structural and workflow invariants but do not constitute a legal opinion, a guarantee of enforceability, or a substitute for current legal review.

This repository deliberately does not publish statute packs, proprietary clause text, full questionnaires, or state-specific legal content.
