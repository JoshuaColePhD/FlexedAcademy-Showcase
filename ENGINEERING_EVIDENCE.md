# Engineering evidence — November 4, 2026

This update records source inspection and local evaluation-contract checks. It
does not refresh the [September 6 production snapshot](PRODUCTION_EVIDENCE.md),
run a hosted model, query a production database, or claim adoption.

The November 4 portfolio documentation, draft task specifications, and offline
evaluator were developed with Codex assistance. Reference labels and output
ratings still require human review; this statement does not attribute earlier
application development.

## Implemented capabilities

Inspected application baseline: `ccc0e51503d016ed1c07bf9bf9d979a630c36c04`.
Offline evaluation addition: `3728b24d360cf9819d40657f4b5f26c5e69c9f2f`.
Application source remains private and is not included here. The paths below
name inspected files for provenance. They are not a copy of the application.

| Capability | Implementation evidence | Boundary |
|---|---|---|
| Hybrid retrieval | `backend/retrieval.py`: pgvector and Postgres full-text search with reciprocal rank fusion, exact-code lookup, course/grade/state scopes | Retrieval relevance still depends on corpus quality and calibration. |
| Reranking | Bounded lexical overlap bonus after candidate retrieval, with an existing A/B harness | A lexical reranker, not a cross-encoder; no new improvement measurement claimed. |
| Structured generation and tools | `backend/llm.py`: strict schemas for plans/revisions; streamed tool calls for artifacts | The separate MCP connector remains experimental. |
| Validation and persistence | Schema validation, citation classification, tenant-scoped storage and queued document jobs | Source-grounding does not establish pedagogical correctness. |
| Cost and latency | Usage ledger with cached-token cost estimates; content-free outcomes and p50/p95 summaries | Instrumentation exists; no new operating-cost or latency result is published. |
| Reliability | Request/run identities, recoverable streaming jobs, document retries, deterministic contract tests | Local tests are not a hosted availability measurement. |

## New evaluation work

The source repository now contains 40 original synthetic teacher tasks focused on
AP Language: 32 answer requests, four clarification requests, and four requests
that should decline an unsupported claim. The fixed split contains 28 development
and 12 holdout cases. Expected source identifiers and answer criteria are all
marked **pending teacher review**. The new set does not replace or modify the
existing 61-case corpus regression baseline.

The offline evaluator accepts separately collected observations, checks dataset
identity and model consistency, and keeps missing/error cases visible. Retrieval
metrics are recall@5, recall@20, and MRR@20. Generation metrics require human
ratings for correctness and faithfulness, plus a separate citation-support audit.
Unapproved labels cannot produce quality scores. See the [method and generated
status artifact](evaluation/README.md).

## Verification boundary

The evaluator's focused pytest suite covers metric definitions, fixed dataset
splits, unreviewed labels, duplicate/unknown cases, mismatched model and dataset
identity, invalid ratings, and incomplete runs. It uses synthetic observations;
those values are never presented as application results. Ruff and a no-observation
CLI run check the implementation without application dependencies or credentials.

Local check result: **22 focused pytest tests passed** on Python 3.12.13; Ruff
lint and format checks passed. The no-observation CLI produced the linked
40-case `not_run` artifact. The completeness-gate test confirms an unrun report
cannot pass as a completed benchmark. No full application release gate or hosted
test was run because this change adds only documentation and an isolated evaluator.

The historical 61/61 result remains historical. A future measured report must
identify its reviewed dataset, corpus, prompt, model, code revision, sample sizes,
failure counts, and collection date. Successful local checks do not substitute
for those measurements.

## Release practice

The application uses local release checks and manual deployment of an explicitly
tested revision. GitHub Actions and Render auto-deploy remain disabled under the
owner's release policy. This portfolio update changes neither production
behavior nor deployment configuration.
