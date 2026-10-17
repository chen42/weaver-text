# Module 08: Source capture and provenance

**Applies to:** Retrieving or downloading external guidelines, templates, references, or other records in any scope, including reviews. This module defines capture methods and provenance for the source-saving rule in `SKILL.md`.

## 1. Decide what to save

Freeze a local copy when either condition holds:

- The source is controlling. It states a requirement, deadline, number, or claim you rely on.
- The source is volatile. It is likely to change or disappear, which includes most agency, funder, and journal pages.

For background context not retrieved as a document, save a note with the URL, access date, and short extract. Keep the sources you rely on, even if they are not ultimately cited. If legitimate access or local storage is unavailable, record the source location and reason; redistribution restrictions alone are not a reason to decline authorized local storage.

Never save search results pages, aggregator pages, or navigation pages. Record the search itself as described in section 2 and save the underlying sources you rely on.

## 2. Literature search records

Reproducibility for a literature search is at the abstract level. Save one record per search, not one file per abstract. Discard abstracts that are irrelevant in every respect. Retain an abstract when it is relevant for any reason, including background, methods, or a comparison you considered.

Place search records in `references/literature-search/`, using the same folder for any literature database. One Markdown file per search is the default, named with the date, database, and short topic, such as `2026-10-06_pubmed_dopamine-reversal.md`. Use `skill-modules/templates/search_record.md`.

Each record states:

- the database and interface, such as PubMed through NCBI E-utilities;
- the exact query as run, including field tags and operators;
- the limits and filters actually applied, such as dates, language, article type, or species;
- the date the search was run;
- the number of results returned and the number retained;
- each retained abstract with its PMID, DOI, or other identifier; citation; retrieval date; the reason it is relevant; and the verbatim abstract;
- a brief synthesis of the retained set.

End each record with a short synthesis: what the retained abstracts collectively support, contradict, or leave unresolved; agreements and conflicts named by identifier; and apparent gaps or a need to refine the search. Keep it to a few sentences and distinguish it from the per-abstract relevance note and from a full review. Do not assert methods, sample sizes, or effect estimates that the abstracts do not report; abstract-level evidence cannot support claims that depend on details absent from the abstract.

Keep `references/references.bib` or the existing reference manager as the canonical record of citation identity. An abstract appearing in two search records is acceptable because each record documents a separate retrieval event. For a systematic review or another large set, keep one search file per search but place the abstract text in a single consolidated store keyed by PMID or DOI, and list those keys in the search file.

## 3. Choose the capture format

- Official PDF: keep the original file unchanged.
- HTML page you cite: save a rendered PDF snapshot and a plain-text extraction. The text is what you quote, and the HTML alone depends on external assets.
- Dynamic or login-gated page: save the rendered PDF or text you can legitimately access, and note that it may not reproduce.
- Registry or dataset record: save the record export (JSON, TSV, or PDF) and the identifiers.
- Reference article: save the full-text PDF when you have access; otherwise record the DOI, PMID, and URL. Abstracts retained from a search follow section 2.

## 4. Name and store

Follow the workspace layout in Module 01. Default locations:

- Controlling documents: `guidelines/source/`
- Literature full texts: `references/papers/`
- Literature search records and retained abstracts: `references/literature-search/`
- User notes and other short records: `references/notes/`
- Supplied findings, statistical outputs, and result tables: `results/`

Existing workspace structure and intake sorting follow Module 01. Source datasets can remain in their original analysis projects or repositories.

For newly retrieved sources, use stable filenames without spaces, for example `NIH_NOT-OD-24-000_2024-05-01.pdf` or `Smith2024.pdf`. For intake files, follow Module 01's filename-preservation rule. Keep one file per source, never overwrite an existing snapshot, and add a new dated file when a source is amended. Leave originals unchanged.

## 5. Record provenance

Every saved source file gets one ledger entry with these fields:

- local path
- original URL
- title
- issuer or publisher
- version, notice, or amendment identifier
- the page's own last-updated string, when present
- access date, with time when useful
- capture format
- sha256 checksum of the saved file
- archive URL and snapshot timestamp, when one exists
- license or redistribution status
- evidence level: abstract only, full text, registry record, or official documentation
- the requirement, claim, figure, or table it supports
- conflicts or uncertainty

Record entries in `guidelines/README.md` for controlling documents and in `results/README.md` for supplied results when an inventory is needed. Literature searches are documented by their search records, and cited works by the existing bibliography. Point the requirements matrix evidence column at the local path and the original URL. Keep these records separate from the brief project logs in `log/`.

Checksum example:

```bash
sha256sum guidelines/source/NIH_NOT-OD-24-000_2024-05-01.pdf
```

## 6. Archive fallback

When a page is likely to change and the local copy may not remain the version of record, also record a Wayback Machine snapshot URL and its timestamp. The local copy is primary and the archive is a secondary reference. For agency pages, capture the notice or amendment identifier and dates even when the page looks static.

## 7. Access and redistribution

Use the access the user already has, such as an institutional subscription or an open-access copy. Do not bypass paywalls, authentication, or rate limits. Saving a copy locally is retrieval for the user's own use. Do not commit it to a public repository, upload it to a third-party service, or share it outside the user's workspace. Do not save protected health information or other restricted data without permission; handle those records as described in Module 02.

## 8. Git boundary

Saved snapshots stay out of commits unless the user approves and the license permits. Exclude large corpora and restricted files from version control, but do not ignore required deliverables. A snapshot never replaces or overwrites the author's source file.

## 9. Verification

- Every external requirement or cited claim resolves to a saved source, a search record, or a recorded reason that no copy exists.
- Retained abstracts trace to a search record that states the database, query, limits, date, and result counts.
- Saved source files have a recorded checksum.
- Amended sources appear as new entries rather than edits to an earlier one.
- License or restriction status is recorded for each saved copy.
