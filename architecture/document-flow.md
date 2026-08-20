# Document Flow

**Last verified:** 2026-08-20

```mermaid
flowchart TD
  P[Maintained product definition] --> A[Assembly inputs]
  S[Maintained document structures and content] --> A
  Q[Questionnaire answers] --> V[Validated inputs]
  J[Jurisdiction content where applicable] --> V
  A --> V
  V --> R[Shared rendered document representation]
  R --> PDF[PDF renderer]
  R --> DOCX[DOCX renderer]
  R --> PKG[Named multi-document package]
  PDF --> C[Completeness checks]
  DOCX --> C
  PKG --> C
  C --> O[Customer deliverable]
```

The model is intentionally conceptual. The public repository does not publish proprietary templates, clause text, questionnaire schemas, or source code.
