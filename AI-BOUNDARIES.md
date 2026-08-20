# AI Boundaries

**Product:** Locke Direct
**Repository type:** Public technical reference
**Source code:** Not included
**Operator:** Locke Development
**Official site:** <https://www.lockedirect.com>
**Last verified:** 2026-08-20

## AI-assisted functionality

Ask Locke is an in-application assistance feature. In its document-picker mode it helps a customer describe what they are trying to do and can recommend an available catalog product. In form-fill mode it can explain a current field and suggest values from facts the customer supplies. The application also uses selected state context when it is needed to ground a jurisdiction-related response.

The feature is bounded rather than open-ended: requests have message and content limits, the assistant is rate limited by request source and customer session, and the client receives a controlled unavailable response when the provider is unavailable or the budget is exhausted.

## Deterministic functionality

Final legal-document assembly is separate from Ask Locke. Product definitions, authored questionnaires, maintained content, jurisdiction data, validation, and the assembly process determine the final document. Ask Locke does not select arbitrary legal clauses by returning free-form text that the renderer treats as authoritative document structure.

Assistant responses are parsed into a constrained envelope. Recommendations must match an available product slug; fill suggestions must match fields supplied by the selected product; facts are sanitized and limited to an allowlist. Model output that does not satisfy the expected envelope is not treated as an authoritative recommendation or fill instruction.

## Provider routing and data boundary

When a customer uses Ask Locke, the relevant prompt, message history, and bounded context are sent through OpenRouter to the selected model provider. The current production route requests zero-data-retention provider handling and does not store the conversation on Locke Direct servers. Facts typed directly into the chat are part of the request. Completed questionnaire values are not automatically included in the prompt; selected state can be included when required to use maintained jurisdiction records.

This is a processing and transmission statement, not a claim that information never leaves the browser. Customers should read the [Privacy Policy](https://www.lockedirect.com/privacy), which governs consumer-facing data handling.

## Failure boundary

Ask Locke may be unavailable, may misunderstand a request, or may return no usable recommendation. The application treats that as an assistance failure and provides a controlled response. It does not turn an arbitrary model response into a final legal document. The maintained catalog, document structures, validation, and entitlement checks remain the authoritative path for document output.

## Limits of this description

The repository documents the current verified role of Ask Locke. It does not publish system prompts, provider credentials, proprietary grounding content, private API inventories, or security-test payloads.
