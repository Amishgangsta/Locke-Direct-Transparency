# Ask Locke — guided assistance with constrained AI authority

**Public experience observed:** October 31, 2026 · **Implementation boundary:** maintainer/source-reviewed · **Source:** proprietary/private.

## Practical customer value

**Ask Locke helps people start from their real-world task, not a legal document title.** A visitor can describe a transaction and receive a recommendation from the actual available product catalog. After opening a document, optional form assistance can explain specific questions and propose field entries based on details the customer elects to share.

Guidance deepens through the document workflow, independent of the assistant: the Customized tier asks structured questions and offers clause selections, Advanced explores potential issues and contingencies, and Complete Package coordinates role-specific terms and supporting documents.

## Two distinct assistance modes

| Mode | Purpose | Technical control |
|---|---|---|
| Document picker | Suggest an existing product for a described task | Recommendations must match available catalog identifiers |
| Form help | Explain fields and optionally suggest answers from customer-provided facts | Suggestions must match actual form field IDs and permitted value types/options |

The application constrains request size, assistant messaging, budgets and request rates. Unsupported or malformed model output is not admitted as an authoritative recommendation or field update.

## Deterministic document drafting

Ask Locke does **not** generate a free-form executable contract, choose arbitrary legal clauses, or replace jurisdiction and product-readiness checks. Maintained legal-document structures and content, validated customer answers, rule-based conditions, and applicable jurisdiction logic control final document assembly. This separates probabilistic conversational help from the deterministic output path.

## AI privacy boundary

When the feature is invoked, customer-entered messages and bounded context pass through OpenRouter to the selected model provider. The documented production route requests **zero-data-retention provider handling**, and Locke Direct does not store chat transcripts on its servers. Completed questionnaire values are not automatically supplied wholesale; jurisdiction state can be shared when required to answer a supported question. Anything a customer voluntarily types into chat is part of that AI request.

**Zero-data-retention routing is a provider handling request, not a promise that messages never leave the device or that provider infrastructure is never involved.** See the [live Privacy Policy](https://www.lockedirect.com/privacy).

## Limits

Ask Locke is **document selection and field guidance, not legal advice**. It may return no usable answer, misunderstand a request, or be unavailable. The application retains the deterministic, maintained-document path when assistant help fails.

[Customer workflows](ASK-LOCKE-AND-GUIDED-WORKFLOWS.md) · [Privacy-first controls](PRIVACY-FIRST.md).
