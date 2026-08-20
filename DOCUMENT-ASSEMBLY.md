# Document Assembly

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

## Assembly model

The authoritative legal-document path uses maintained structures and content rather than unrestricted model generation.

```text
Product definition
        +
Questionnaire definition
        +
Validated customer answers
        +
Jurisdiction/state content where applicable
        ↓
Validated assembly process
        ↓
Canonical rendered document representation
        ↓
PDF / DOCX / named package outputs
```

The source implementation maintains document structures, question definitions, conditions, and release-gated content. Answers control the values and authored alternatives that are eligible for a document. The application validates completeness, authored conditional requirements, numeric bounds, and selected consistency checks before final generation.

## Shared representation and exports

PDF and DOCX originate from a shared parsed document representation. The renderers preserve headings, paragraphs, lists, tables, execution blocks, and the final document block. Export verification checks that content and execution sections survive the conversion. A document that cannot be rendered completely should fail rather than silently return a truncated artifact.

Some products contain one document; others are document sets or packages. A package is split into separately named outputs and delivered as a package rather than being treated as one long document. The package boundary and ordering are tested.

## Questionnaire boundaries

Questionnaire fields are mapped intentionally to document content. A question can be required for workflow logic without being rendered into the signed document. For example, a workflow may need an answer to decide whether a branch is applicable while the answer itself is not operative text. This distinction is maintained so that the interview can collect process facts without silently placing every process fact into the legal instrument.

## Preview and final generation

Preview and final output use the same release-gated content authorities. Final generation re-checks the product's customer-facing readiness and the customer's active entitlement. Required placeholders, blocking consistency warnings, and missing content prevent final generation. A database product row alone cannot authorize an unfinished product.

## Why deterministic assembly matters

Deterministic assembly makes document structure and clause selection inspectable and testable independently from probabilistic AI responses. It also permits parity tests across questionnaires, source structures, preview content, rendered output, and PDF/DOCX exports. This does not remove the need for customer review or professional legal advice where appropriate; it describes how the software constructs the artifact.

This document intentionally omits proprietary templates, clause text, questionnaire schemas, prompt text, source filenames, and implementation code.
