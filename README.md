# FlexEd Academy — project showcase

FlexEd Academy is an AI lesson planner for high-school teachers that produces
structured, standards-aligned weekly plans and exports them as district-style
Word documents. I (Joshua Cole) built it and run it solo.

The design centers on measurable reliability: retrieval over real standards
documents is evaluated against a canonical recall set (currently 61/61
recall@5), and every cited standard in a generated plan is checked by a
grounding audit before the plan is saved. Details are in the
[case study](./FlexedAcademy_Case_Study.md).

![FlexEd Academy walkthrough](./FlexedAcademy_Walkthrough.gif)

## Try the live demo

1. Go to [https://flexedacademy.com](https://flexedacademy.com).
2. On the sign-in page, click **Explore demo**.
3. You are signed in to a read-only Recruiter Demo account with seeded example
   plans. You can browse plans, citations, and document export; generation,
   edits, uploads, sharing, and billing are disabled for this account.

No sign-up or payment method is needed.

## What's in this package

| File | Description |
|---|---|
| [FlexedAcademy_Case_Study.md](./FlexedAcademy_Case_Study.md) | Applied-AI case study: how quality is measured, architecture, grounding and failure behavior, tradeoffs |
| [PORTFOLIO_BRIEF.md](./PORTFOLIO_BRIEF.md) | One-page summary, evaluation highlights, suggested two-minute walkthrough, limitations |
| [PRODUCTION_EVIDENCE.md](./PRODUCTION_EVIDENCE.md) | Dated production check snapshot (September 6, 2026) and recorded quality baselines |
| [FlexedAcademy_Sample_Lesson_Plan.docx](./FlexedAcademy_Sample_Lesson_Plan.docx) | Sample generated weekly lesson plan (Word export) |
| [FlexedAcademy_Walkthrough.gif](./FlexedAcademy_Walkthrough.gif) | Product walkthrough (GIF, shown above) |
| [FlexedAcademy_Walkthrough.mp4](./FlexedAcademy_Walkthrough.mp4) | Product walkthrough, higher quality (MP4) |
| [FlexedAcademy_Walkthrough.webm](./FlexedAcademy_Walkthrough.webm) | Product walkthrough (WebM) |

## Limitations

AP Language is the most thoroughly calibrated course. Generated plans should
be reviewed by a qualified teacher. No pilot or usage metrics are claimed; the
evidence here is evaluation and production-check results.

## Source code

Source code is private; available on request.

## License

Copyright (c) 2026 Joshua Cole. All rights reserved. This source is viewable for evaluation only. See [LICENSE](./LICENSE).
