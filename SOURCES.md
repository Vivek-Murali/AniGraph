# AniGraph — sources and implementation references

Checked 20 October 2026. The repository describes a proposed design. Tool documentation is not evidence that the project has implemented or benchmarked those tools.

| Reference | Why it is relevant |
|---|---|
| [Neo4j GraphRAG for Python](https://neo4j.com/docs/neo4j-graphrag-python/current/) | Official Python GraphRAG package, retrievers and compatible graph/vector capabilities; verify selected versions at M02 |
| [Hugging Face Transformers](https://huggingface.co/docs/transformers/index) | Python model definitions and inference/training ecosystem |
| [Polars](https://docs.pola.rs/) | Rust-backed dataframe work from Rust or Python; avoid unnecessary custom rewrites |
| [Tokio](https://tokio.rs/tokio/tutorial) | Bounded asynchronous Rust I/O when concurrency is needed |
| [Wikidata licensing](https://www.wikidata.org/wiki/Wikidata:Licensing) | Structured Wikidata data is CC0; this does not extend automatically to linked text or images |
| [AniList API documentation](https://docs.anilist.co/) | Candidate metadata source; inspect current terms, rate limits and allowed use before collection |
| [GitHub Mermaid diagrams](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams) | How Markdown diagrams render in this repository |

## Source-selection record to complete in M03

For each source record: owner, endpoint, exact fields, terms/licence reference and date checked, allowed use, attribution, access controls, retention, rate limits, update/delete policy, expected coverage and known gaps. Do not publish source text/images merely because an API returns their URLs.

Start with synthetic data and self-authored text if source decisions remain unresolved. A small curated source-permitted dataset can establish the engineering path without asserting complete anime-industry coverage. Credits may be sparse or inconsistent across sources; retain uncertainty and provenance.

## Status evidence used for planning

The parent portfolio story and its related portfolio records were inspected read-only, alongside the React frontend and FastAPI backend. The story exists; AniGraph has no stored milestone rows, long-form content, repository link or live-demo link in that inspected snapshot. The local website repositories are the CMS, not implementation evidence for AniGraph. This status is time-specific and should be refreshed as work is completed.
