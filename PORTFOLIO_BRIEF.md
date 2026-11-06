# FlexEd Academy — portfolio brief

## Thirty-second description

FlexEd Academy is a deployed AI lesson-planning platform for high-school
teachers. It retrieves from real standards documents, generates a strict
structured plan, audits every cited standard, and exports a district-formatted
Word document. The project is designed around reliable, measured model behavior
rather than prompt-only generation.

## How quality is measured

- The recorded canonical retrieval baseline is 61/61 recall@5 and 61/61
  recall@20; it was not rerun for the November 4 portfolio update.
- A separate 40-case teacher-task benchmark is drafted; reference labels await
  teacher review and hosted evaluation is `not_run`.
- A post-generation grounding audit classifies each cited standard as grounded,
  non-retrieved, borrowed from another scope, or hallucinated.
- Regression tests cover borrowed, invented, cross-course, and out-of-scope
  citations.
- An older 143-case set is retained as a historical drift diagnostic.

Details: [case study](./FlexedAcademy_Case_Study.md),
[November 4 engineering evidence](./ENGINEERING_EVIDENCE.md), and
[historical production evidence](./PRODUCTION_EVIDENCE.md).

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

Use the sign-in page's read-only demo entry point to inspect plans, citations,
and the artifact flow without creating an account or consuming generation
credits. Availability was last documented in the September 6 snapshot; the
recorded walkthrough is the fallback if the live demo is unavailable.

Application source is private and is not included in this repository.

## Two-minute walkthrough

1. Open the live product or recruiter demo.
2. Show a class context and an existing weekly plan.
3. Open a cited standard and point out its source metadata.
4. Explain documented grounding/refusal behavior from the case study; the
   read-only demo cannot run a new generation request.
5. Open the DOCX export flow and explain that the artifact is validated and
   queued rather than treating partial stream text as final.
6. End on the case study's evaluation and architecture sections.

## Honest limitations

- AP Language is the most thoroughly calibrated path.
- The system depends on OpenAI embeddings/generation and Supabase in production.
- Generated instructional activities still require teacher review.
- No pilot or usage numbers are reported yet; evaluation metrics are the
  current evidence base.
