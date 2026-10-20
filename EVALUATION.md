# AniGraph — evaluation and release plan

Status: proposed protocol. No benchmark has been run and no performance/accuracy result is claimed.

## Build the benchmark before tuning

Begin with five hand-checked questions in M01. For M09, propose at least 50 labelled pilot questions distributed across exact facts, multi-hop collaborations, semantic retrieval, ambiguous names, unsupported requests and missing/conflicting evidence. Choose the actual category counts in M01 and report each denominator. This sample is an initial engineering benchmark, not broad statistical assurance.

Separate development and final evaluation sets. Group near-duplicate/paraphrased questions and shared entity families where necessary to prevent leakage. Expected answers must refer to a fixed source snapshot; knowledge gaps should have an expected abstention or clarification. Do not tune prompts on the final test set.

## Baselines

| System | What it tests | Expected strength |
|---|---|---|
| Deterministic graph templates | Graph modelling and exact query correctness | Facts and bounded multi-hop counts |
| Vector-only retrieval / RAG | Text evidence retrieval and synthesis | Semantic text questions |
| Hybrid GraphRAG | Whether graph plus text improves useful answers | Questions needing relationships and textual context |
| Text-only vs image-plus-text | M12's additional value | The narrow selected multimodal task |

Match data coverage, model revisions, precision, context budgets and hardware for comparisons where applicable. Record differences that cannot be matched. An exact question does not need an LLM merely to produce a count.

## Report the following

- Exact-answer correctness for graph fixtures and count questions.
- Entity resolution errors, especially homonyms and aliases across languages.
- Retrieval recall at chosen k, with relevant-evidence labels and denominators.
- Citation correctness and coverage: does the cited source support the answer's claims?
- Correct abstention and clarification rates, plus unnecessary abstentions.
- End-to-end p50/p95 latency, throughput, peak memory and cost per answered request.
- Quality slices by question type, language/edition, rare entities and missing data.
- Adversarial failures: injected source instructions, write requests, huge neighborhoods, unauthorized/private sources and broken citations.

Use human review on a sample of model-judged outputs and record disagreements. Do not present an LLM judge as ground truth. Save prompts, raw outputs, scorer versions and evaluation configuration where permission/retention allows.

## Set thresholds before the final run

| Criterion | Target to set in M01 | Evidence at release |
|---|---|---|
| Hand-checked graph fixture correctness | All expected fixture answers pass | Query assertions and graph snapshot |
| Replay consistency | No unintended duplicate canonical records | Repeat-load report |
| Held-out useful-answer quality | Decide with user/task costs | Frozen-set report and failures |
| Citation support / abstention | Decide by claim and risk | Reviewed examples and aggregate report |
| p95 latency and operating cost | Decide for intended deployment | Representative load/cost report |
| Destructive query / permission boundary | Forbidden actions blocked | Adversarial integration checks |

If a threshold fails, narrow the feature or keep the release experimental. Keep the original threshold in the record. A production claim requires representative user/workload evidence beyond a small pilot set.
