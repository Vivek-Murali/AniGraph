# AniGraph — shared data contract design

This describes a contract to implement in M03, not an already validated production schema.

## Canonical record families

| Record | Identity and required meaning | Optional fields / caveats |
|---|---|---|
| Anime | `anime_id`, source ID, canonical label, record revision | Alias/language pairs; edition/season scope; release dates may be incomplete |
| Person | `person_id`, source ID, canonical label | Aliases and external identifiers; name alone cannot establish identity |
| Studio | `studio_id`, source ID, canonical label | Aliases, historical name changes and corporate relationships |
| Credit | `credit_id`, anime ID, person ID, role, source-record ID | Character, language, edition, episode scope; null means unknown |
| Studio participation | anime ID, studio ID, participation role, source-record ID | Production is distinct from distribution or licensing |
| Source record | source/system ID, record ID, URL, retrieval timestamp, source revision/hash | Permission/attribution reference and known coverage limits |
| Document/chunk | document/chunk IDs, source-record ID, content hash, language, offsets | Allowed text, transforms and deletion policy |
| Image asset | asset ID, source record, hash, rights reference | M12 only; no implied right to redistribute |

Use UTC ingestion timestamps. Preserve source-provided precision rather than inventing a complete date. Store language tags for labels and credit language. Keep source assertions separate from resolved canonical identity so disputed facts can be corrected without losing their origin.

## Snapshot manifest

Record schema version, dataset/snapshot ID, source checkpoints, exact file list, checksums, row counts by record family, quarantine counts, deduplication policy, transform/code revision and publication status. Consumers only use a committed manifest.

`input records = accepted + quarantined + intentionally skipped` under a defined counting policy. Report duplicates separately and explain whether accepted counts are before or after deduplication.

## Compatibility and validation

- Validate required fields, identity references, allowed role values, string encodings and nullable semantics in both languages.
- Add cross-record referential checks; a JSON document passing a shape schema does not prove its person or anime exists.
- Test ambiguous aliases, co-productions, multiple characters, multiple languages, missing people and conflicting assertions.
- Define whether optional extra fields are accepted. An old strict consumer can reject an additive field.
- Changes in identity, role meaning, units or required fields require a version/migration policy.
- Replay preserves IDs. Source updates and deletion have explicit propagation rules.

## AI result record

Preserve request ID, question, resolved entities, retrieval plan/template ID, snapshot/index revision, model/tokenizer/prompt revisions, evidence IDs, returned answer, citation support review and error/abstention status. Store only the question/content necessary under the chosen privacy and retention policy.
