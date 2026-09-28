# FlexEd Academy — portfolio brief

## Thirty-second description

FlexEd Academy is a deployed AI lesson-planning platform for high-school
teachers. It retrieves from real standards documents, generates a strict
structured plan, audits every cited standard, and exports a district-formatted
Word document. The project is designed around reliable, measured model behavior
rather than prompt-only generation.

## How quality is measured

- Retrieval is gated by a canonical recall evaluation set: currently 61/61
  recall@5 and 61/61 recall@20.
- A post-generation grounding audit classifies each cited standard as grounded,
  non-retrieved, borrowed from another scope, or hallucinated.
- Regression tests cover borrowed, invented, cross-course, and out-of-scope
  citations.
- An older 143-case set is retained as a historical drift diagnostic.

Details: [case study](./FlexedAcademy_Case_Study.md) and
[production evidence](./PRODUCTION_EVIDENCE.md).

## The applied-AI problem

Standards contain low-frequency identifiers, repeated numbering schemes, and
course-specific meanings. A model can produce a fluent but incorrect citation.
FlexEd treats retrieval, validation, refusal, and artifact integrity as part of
the product contract.

## Evidence to show a recruiter

- [Live application](https://flexedacademy.com) (use “Explore demo” on the sign-in page)
- [Applied-AI case study](./FlexedAcademy_Case_Study.md)
- [Production evidence snapshot](./PRODUCTION_EVIDENCE.md)
- [Product walkthrough](./FlexedAcademy_Walkthrough.mp4)
- [Sample generated lesson plan](./FlexedAcademy_Sample_Lesson_Plan.docx)

The deployed sign-in page currently exposes a read-only recruiter demo. Use its
demo entry point so the reviewer can inspect plans, citations, warnings, and the
artifact flow without creating an account or consuming generation credits.

Source code is private; available on request.

## Two-minute walkthrough

1. Open the live product or recruiter demo.
2. Show a class context and an existing weekly plan.
3. Open a cited standard and point out its source metadata.
4. Show the grounding warning/refusal behavior for an unsupported request.
5. Open the DOCX export flow and explain that the artifact is validated and
   queued rather than treating partial stream text as final.
6. End on the case study's evaluation and architecture sections.

## Interview story

> The hard problem was not generating teacher-sounding prose. It was preventing
> plausible but wrong standards codes. I solved that by combining scoped
> retrieval, a measured relevance floor, strict structured outputs, and a
> post-generation grounding audit. I then added regression tests for borrowed,
> invented, cross-course, and out-of-scope citations.

## Honest limitations

- AP Language is the most thoroughly calibrated path.
- The system depends on OpenAI embeddings/generation and Supabase in production.
- Generated instructional activities still require teacher review.
- No pilot or usage numbers are reported yet; evaluation metrics are the
  current evidence base.
