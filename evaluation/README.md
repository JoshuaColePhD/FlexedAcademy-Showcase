# Teacher-task evaluation

**Current status: `not_run`.** There are 40 drafted AP Language teacher tasks;
all reference labels await qualified teacher review. No hosted model or
production database was called for this portfolio update. The generated
[status artifact](teacher_tasks_status.json) deliberately has null quality
metrics. Null means unmeasured, not zero accuracy.

Inspect a [four-case sample of the synthetic task specifications](teacher_tasks_sample.json):
two answer tasks, one clarification task, and one refusal task, all pending
review. The full 40-case set stays in the private source repository. The sample
contains original task wording and source identifiers, not copied standards text
or teacher data; its source-dataset checksum matches the status artifact.

## What the evaluation is intended to establish

| Layer | Measurement | What it cannot establish alone |
|---|---|---|
| Retrieval | Macro recall@5/@20 and MRR@20 against approved expected sources | Whether a generated activity is correct or useful. |
| Correctness | Human score 0–2 against the task's answer criteria | Whether every attributed source claim is supported. |
| Faithfulness | Human score 0–2 for support and attribution of source claims | General learning gains or classroom effectiveness. |
| Citation support | Supported citations divided by audited citations | Overall answer quality; no citations means an undefined rate. |
| Task behavior | Whether the response answers, asks for missing context, or declines an unsupported request appropriately | Performance outside these cases. |

## Dataset and review

The set contains 32 answer tasks across eight AP Language skill areas, four
clarification requests, and four refusal requests. Its 28 development and 12
holdout cases are fixed before measurement. All prompts are synthetic; none
contains student records or a real teacher's conversation.

Source references point to the [College Board course description](https://apcentral.collegeboard.org/media/pdf/ap-english-language-and-composition-course-and-exam-description.pdf).
Source identifiers were checked against the tracked document, but the mapping
from each task to its relevant skills and expected answer criteria still needs
teacher review. This is an evaluation specification, not a completed validation
study. A public benchmark can overlap with future training data; “holdout” here
means withheld from this project's tuning.

## Reproduction workflow

The four-case sample is published above. The full dataset, evaluation script,
tests, and review rubric stay in the private source repository and are not
included here. Review reference
labels first and freeze the dataset checksum. Collect outputs with the actual
model, prompt version, corpus version, and tested code revision. Preserve ranked
retrieval source IDs and failed requests. Have a qualified teacher rate outputs
against the case criteria and retrieved context independently of retrieval rank.

The local command `python3.12 scripts/evaluate_teacher_tasks.py --output
/tmp/teacher_tasks_status.json` validates the dataset and writes a not-run report.
Supplying `--observations` scores an existing observation file; the evaluator
itself has no model or database connection. `--require-complete` fails unless all
cases, references, and generation reviews are complete. Duplicate IDs, unknown
cases, model changes, and dataset checksum mismatches are rejected. Partial-run
metrics retain their coverage and cannot masquerade as a complete benchmark.

For a calculation example only, suppose the expected sources are A and B and the
ranked hits are X, A, Y, B. Recall@5 is 2/2 and reciprocal rank is 1/2, because
the first relevant hit is second. Repeated chunk hits keep their original rank
positions. This arithmetic illustration is not a FlexEd run or quality result.

The [existing 61/61 retrieval baseline](../PRODUCTION_EVIDENCE.md) is a separate,
historical corpus regression result. This new task set neither reproduces nor
replaces it. No new accuracy, cost, latency, adoption, or learning-outcome claim
is made until an actual run supplies the corresponding evidence.
