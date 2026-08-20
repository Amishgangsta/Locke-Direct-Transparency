# AI Boundary

**Last verified:** 2026-08-20

```mermaid
flowchart LR
  B[Customer browser] --> H[Ask Locke request boundary]
  H --> X[Input bounds and context filtering]
  X --> OR[OpenRouter and selected model provider]
  OR --> Y[Structured response parser]
  Y --> AL[Catalog/field allowlists]
  AL --> B

  B --> Q[Questionnaire answers]
  Q --> V[Deterministic validation]
  V --> DA[Deterministic document assembly]
  DA --> OUT[PDF / DOCX / package]

  Y -. does not author final legal structure .-> DA
```

The separated arrows are the principal product boundary: AI guidance can help a customer navigate a product or field, while maintained structures and deterministic assembly control the final document.
