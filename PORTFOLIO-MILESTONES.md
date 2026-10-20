# AniGraph — copy-ready portfolio milestones

Use these entries with the **Add New Portfolio Item** form. They are proposed roadmap items, not claims of work completed. All payloads start `planned`, `0 / 5`, with no invented rating, steps, dates, contributors or attachment links. If you have already started a milestone, change it to `in-progress` and record only verified deliverables.

## How these map to the existing website

- Select the existing **AniGraph** portfolio collection. Its ID is `32170b2a-cffe-4a0e-b25d-58a580a79bdb`.
- `portfolio` holds the parent story; `portfolio_items` holds the milestone records through `portfolio_id`.
- The form uses nested `progress`; its service converts that to flat `progress_current` and `progress_total` API fields.
- The JSON file contains those **API request fields**, not the nested form model. It is a list of proposed POST bodies, not an import feature already supported by the site.
- The backend computes progress percentage. Do not submit a separate invented overall project percentage.
- The current story page filters a fetched page of milestones in the browser and does not render the parent long-form `content`. Publishing these documents to GitHub does not change that deployed behavior.
- Current audit: AniGraph had no milestone records and no long-form content when inspected on 20 October 2026. These files do not change the live database.
- The screenshot’s icon groups affect where items appear in the unified portfolio view; choose each proposed icon intentionally.
- To preserve ascending milestone order in the current newest-first API, create entries M13 down to M01, or implement an explicit ordering field later. Creation timestamps are not milestone completion dates.

## Suggested update routine

1. Create the planned milestone with its correct collection and icon.
2. Copy the milestone write-up template into a work note or GitHub issue.
3. Attach real evidence as each deliverable passes; update current out of five.
4. Mark complete only after all five deliverables and the acceptance gate are documented.
5. Update the parent project narrative separately when a meaningful release is verified.

## M01 — Problem framing, scope and success criteria

**Project icon:** `file-text` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Define an answerable first version of AniGraph rather than claiming coverage of the whole anime industry.

Planned deliverables:
1. Write the target user, decision and five representative questions.
2. Set MVP boundaries: a curated, source-permitted sample of anime, people, studios and credits.
3. Separate exact graph questions, semantic questions, unsupported questions and future image questions.
4. Define measurable quality, latency and operating-cost targets before tuning.
5. Publish the scope matrix, assumptions and initial architecture decision.

Acceptance: A reviewer can identify what the MVP will answer, what it will refuse and how success will be measured.

Evidence: Problem statement and scope matrix; Five question examples with expected evidence; Acceptance-target decision record.

## M02 — Repository, reproducible environment and development checks

**Project icon:** `code` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Make one small fixture reproducible before adding production services.

Planned deliverables:
1. Choose and record compatible Rust, Python and Neo4j versions; create isolated environments.
2. Establish Rust ingestion and Python AI packages with one documented local command each.
3. Add dependency locks, an environment-variable example without credentials and ignored local data.
4. Add formatting, unit-test and shared-contract checks to CI.
5. Verify a clean checkout can validate the synthetic fixture without external API keys.

Acceptance: A clean checkout passes documented local and CI checks; no source datasets or credentials are required for the fixture path.

Evidence: Environment/setup guide; Lockfiles and example configuration; CI run and fixture output.

## M03 — Source selection, provenance and shared data contract

**Project icon:** `database` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Decide which facts and documents can be used and preserve where every claim came from.

Planned deliverables:
1. Choose an initial source after checking its API terms, reuse conditions and coverage.
2. Record source URLs, retrieval times, revisions, permitted fields, attribution and retention decisions.
3. Define canonical anime/person/studio/credit records with stable IDs, nulls and language-aware aliases.
4. Add synthetic valid, malformed, duplicate, missing-credit and conflicting-name fixtures.
5. Specify committed manifests, checksums, deletion, reconciliation and schema-evolution rules.

Acceptance: Every fixture record validates, every fact has provenance, and a source-coverage matrix identifies missing information.

Evidence: Source register and coverage matrix; Versioned contract and shared fixtures; Schema validation and reconciliation examples.

## M04 — Rust ingestion and replay-safe dataset publication

**Project icon:** `layers` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Turn one allowed source or fixture into a trustworthy, repeatable input snapshot for AI.

Planned deliverables:
1. Implement a bounded Rust collector/parser with explicit request deadlines and source-rate handling.
2. Normalize identifiers, timestamps, language tags and missing values without inventing facts.
3. Quarantine malformed records with stable reason codes and restricted diagnostic context.
4. Deduplicate by source identity/revision, reconcile counts and write a staged canonical snapshot.
5. Publish a complete manifest and test interrupted runs, retry limits and replay.

Acceptance: Running the same input twice produces the same logical dataset, and consumers cannot read a partially published snapshot.

Evidence: Input/output manifests and checksums; Quarantine/reconciliation report; Replay and interrupted-run tests.

## M05 — Entity resolution and anime graph model

**Project icon:** `git-branch` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Model credits and relationships precisely enough to support reliable multi-hop answers.

Planned deliverables:
1. Define Anime, Person, Studio and Credit identities; use a credit entity to preserve role, character, language and evidence.
2. Document relationship direction and the difference between production, licensing and distribution.
3. Resolve aliases and external IDs while preserving ambiguous identities for review.
4. Specify release/version scope, co-productions, missing credits and conflicting-source behavior.
5. Create a hand-checked miniature graph and expected multi-hop query answers.

Acceptance: The miniature graph answers the benchmark credit questions without merging distinct people or treating missing credits as negative evidence.

Evidence: Ontology diagram and identity policy; Alias/conflict examples; Hand-checked graph fixture and expected answers.

## M06 — Neo4j loading and deterministic graph-query baseline

**Project icon:** `database` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Prove the graph is useful without an LLM.

Planned deliverables:
1. Create uniqueness constraints and indexes appropriate to the chosen Neo4j version.
2. Implement idempotent loading keyed by canonical IDs and explicit update/deletion handling.
3. Use an ingestion identity with write permission and a separate application read-only identity.
4. Implement parameterized query templates for cast, staff, studio and bounded collaboration counts.
5. Compare fixture query results and replay behavior with the hand-checked expected outputs.

Acceptance: Exact fixture questions return the expected entities, counts and provenance; repeated loading creates no duplicates.

Evidence: Schema/constraint and query files; Baseline results with source IDs; Load/reload/deletion tests.

## M07 — Python text preparation and semantic-retrieval baseline

**Project icon:** `cpu` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Retrieve relevant text with attributable evidence before generating answers.

Planned deliverables:
1. Use permitted or self-authored text, preserving document IDs, source revisions and offsets.
2. Define chunking, language handling, text normalization and content-hash-based reindexing.
3. Choose an embedding model and pin tokenizer/model/preprocessing versions.
4. Store chunks and vectors in a compatible Neo4j vector index initially, with dimension checks.
5. Evaluate retrieval on labelled queries and verify document deletion removes derived chunks/vectors.

Acceptance: Relevant evidence is retrievable with stable citations, and index versions and deletion behavior are reproducible.

Evidence: Chunk examples and source references; Model/index manifest; Retrieval and deletion results.

## M08 — Hybrid GraphRAG with bounded queries and cited answers

**Project icon:** `cpu` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Combine graph facts and text evidence while preserving a clear boundary between facts and generated explanation.

Planned deliverables:
1. Route exact questions to approved graph templates and semantic questions to retrieval.
2. Combine bounded graph neighborhoods and relevant text under a context budget.
3. Generate answers with entity/source citations and explicit snapshot/coverage scope.
4. Abstain or ask for clarification when evidence is missing, conflicting or ambiguous.
5. Enforce read-only query execution, parameters, timeouts and result limits independently of model instructions.

Acceptance: A traced example shows question, retrieval plan, evidence, bounded query and supported response; unsafe requests cannot write to the graph.

Evidence: Three end-to-end answer traces; Citation and abstention examples; Query-boundary and injection tests.

## M09 — Evaluation, failure analysis and performance evidence

**Project icon:** `test-tube` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Measure whether GraphRAG adds value over simpler baselines.

Planned deliverables:
1. Freeze a proposed pilot set of at least 50 labelled questions, stratified by exact, multi-hop, semantic and unanswerable cases.
2. Separate development and final test questions; prevent paraphrase and entity-family leakage.
3. Compare deterministic graph queries, vector-only RAG and hybrid GraphRAG under matched conditions.
4. Measure answer correctness, retrieval recall, citation support, abstention, latency and cost.
5. Publish failures, denominators, uncertainty and a release decision without tuning on the final test set.

Acceptance: A reproducible report meets the targets chosen in M01 or documents why the system remains an experiment.

Evidence: Versioned benchmark and split policy; Baseline comparison with raw results; Failure analysis and release decision.

## M10 — API and evidence-first demonstration interface

**Project icon:** `globe` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Let a user inspect an answer and the evidence behind it.

Planned deliverables:
1. Expose a typed Python query API with validated inputs, request IDs and structured errors.
2. Build a small demo UI with question examples, citations, graph paths and index freshness.
3. Display missing-evidence and service-unavailable states without implying certainty.
4. Add request deadlines, input/context limits and per-user limits appropriate to the pilot.
5. Run end-to-end cases for successful, ambiguous, unsupported and failed requests.

Acceptance: A new user can ask a supported question, inspect its evidence and understand the system limits.

Evidence: API contract and request examples; Demo screenshots or recording; End-to-end and usability findings.

## M11 — Deployment, monitoring and recovery

**Project icon:** `cloud` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Operate a limited pilot with traceable artifacts and a tested way to recover.

Planned deliverables:
1. Package a documented deployment with pinned artifacts, secret configuration and health checks.
2. Separate ingestion and serving permissions; verify access, deletion and log-minimization behavior.
3. Measure realistic concurrency, latency, memory and infrastructure/model cost.
4. Correlate request traces with source/index/model revisions and monitor stale data and failure rates.
5. Rehearse backup/restore and rollback to a compatible graph, text index, model and application version.

Acceptance: The pilot passes its operating budget and service targets, and a second person can follow the runbook to recover it.

Evidence: Deployment record and resource budget; Load-test and monitoring examples; Restore/rollback drill and runbook.

## M12 — Multimodal image extension and comparative evaluation

**Project icon:** `cpu` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Earn the multimodal claim with one narrow, permissioned image-plus-text use case.

Planned deliverables:
1. Choose one image task and an explicitly permitted or self-authored evaluation corpus.
2. Record asset ownership, IDs, provenance, transforms and allowed display/retention.
3. Implement image embeddings or vision extraction linked to the existing source/entity graph.
4. Measure image-plus-text performance against the text-only baseline on a held-out set.
5. Document hallucination, mismatch, accessibility and deletion cases; retain the extension only if useful.

Acceptance: A reproducible multimodal example and comparison report show supported benefit and remaining failures.

Evidence: Asset/source manifest and one complete trace; Matched text-only vs multimodal results; Known limitations and accessible demo.

## M13 — Final case study, portfolio evidence and handover

**Project icon:** `file-text` · **Status:** planned · **Current / total:** 0 / 5 · **Rating:** leave unrated (0)

**Description to paste:**

Publish an honest, reproducible portfolio story backed by artifacts and measured results.

Planned deliverables:
1. Write the problem, implemented scope, architecture, decisions and trade-offs in the case study.
2. Link specific commits, datasets/manifests, evaluation reports and reproducible demo instructions.
3. Replace proposed targets with actual measured results and identify unimplemented features.
4. Document the operating runbook, known limits, remaining backlog and ownership.
5. Update the portfolio narrative, milestone evidence, GitHub link and status to match verified work.

Acceptance: A reviewer can reproduce one result and distinguish implemented, evaluated, deployed and future capabilities.

Evidence: Final case study and demo; Reproducibility checklist; Portfolio entries linked to evidence.
