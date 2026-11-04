# FlexEd Academy

**FlexEd Academy helps teachers turn a weekly teaching request into a standards-grounded lesson plan and a district-style Word document.**

![FlexEd Academy walkthrough](./FlexedAcademy_Walkthrough.gif)

[Explore the demo](https://flexedacademy.com) · [Read the case study](./FlexedAcademy_Case_Study.md) · [Inspect engineering evidence](./ENGINEERING_EVIDENCE.md)

I built and operate FlexEd as a solo project. Its central problem is making an
AI-generated teaching artifact inspectable: the teacher needs to see which
standards informed it, check the proposed activities, and recover when generation
or document export fails. The product connects that entire workflow, from source
ingestion to a saved plan and downloadable document.

## What I built

- A retrieval pipeline combining semantic search, keyword search, course and grade filters, query expansion, and bounded lexical reranking, followed by a citation-grounding audit.
- A Python/FastAPI application with structured OpenAI outputs, tool-driven planning and revision, streamed progress, tenant-scoped Postgres storage, and recoverable document jobs.
- Evaluation and operating controls: retrieval regression cases, deterministic contract tests, token-cost estimates, request identities, and outcome/latency measurements.

## Results

| Evidence | What it establishes |
| --- | --- |
| Recorded retrieval | **61/61** at recall@5 and recall@20 on the historical corpus regression set; not rerun for this update. |
| Teacher-task evaluation | **40 draft cases**, awaiting teacher review. Hosted evaluation has not run; no generation-quality score is claimed. |
| Production snapshot | **September 6, 2026:** a working demo path at that date, without a current uptime or adoption claim. |
| Offline evaluator | **22 tests passed** on November 4. These check reporting behavior, not hosted model performance. |

The new benchmark keeps retrieval recall and MRR separate from human-reviewed
correctness, faithfulness, and citation support. AP Language remains the most
calibrated course. A valid citation does not establish that every activity is
instructionally sound, and teachers should review generated plans before use.

## How it works

Teacher request → scoped hybrid retrieval → structured generation → schema
and citation checks → saved plan → Word export.

On the live sign-in page, choose **Explore demo** to browse a seeded, read-only
account without signing up or buying credits. The demo lets reviewers inspect
plans, citations, and export; generation and edits are disabled. The walkthrough
above remains available if the hosted demo is unavailable.

## Explore further

[Architecture and tradeoffs](./FlexedAcademy_Case_Study.md) · [Evaluation method and current status](./evaluation/README.md) · [Historical production checks](./PRODUCTION_EVIDENCE.md) · [Sample Word output](./FlexedAcademy_Sample_Lesson_Plan.docx) · [One-page brief](./PORTFOLIO_BRIEF.md) · [Full-quality walkthrough](./FlexedAcademy_Walkthrough.mp4)

Source code is private and available on request. This showcase contains product
and engineering evidence; it claims no teacher-adoption counts, learning gains,
or independently validated scoring of instructional quality.
