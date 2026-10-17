---
name: weaver-text
description: Draft, revise, review, and package scientific manuscripts and grant proposals. Use for focused scientific editing, Specific Aims and other grant sections, simulated peer review, responses to reviewers and resubmissions, cover letters, citation checking, submission-guideline compliance, reproducible figures, or publication workflows using LaTeX, DOCX, or LibreOffice ODT, with Markdown accepted for first drafts.
metadata:
  version: "17"
  created: "2026-09-27"
  updated: "2026-10-17"
---

# Weaver text

## Select the task

Use this skill for scientific manuscripts and grant proposals. Choose the smallest scope that meets the request:

- **Edit**: Revise the specified text. Do not expand a local edit into a whole-document audit.
- **Review**: Report findings and suggested revisions without changing source contents.
- **Full production**: Draft, organize, review, export, or package documents through the stages needed for the requested deliverables.

Infer scope and ask only when ambiguous. For scientific drafting and prose revision, read the relevant guidance in Module 03, including for small edits. Load Module 04 when section organization is involved. A local prose edit does not require reporting checklists, literature searches, compilation, or full project scaffolding. A pasted-text edit with no file handling or retrieval needs no workspace.

## Essential rules

- Preserve claims, evidence, names, numbers, dates, citations, and technical meaning except where a change is requested or approved. Never invent missing facts, methods, results, references, or submission requirements. Use visible, actionable `[AUTHOR QUERY: ...]` markers.
- Write clear, direct, neutral scientific prose. Keep paragraphs focused and preserve established acronyms. Use past tense for completed study actions and results, and present tense for established facts and broader interpretations. Avoid promotional language and rhetorical em dashes or en dashes; preserve scientific notation and protected source content.
- Match causal and mechanistic claims to the design and evidence. Present supplied statistics accurately, with analysis-appropriate estimates, uncertainty, and sample sizes. Query missing analyses or values rather than calculating them or prescribing specific scripts or tools. When a reanalysis is needed, recommend that the author perform it.
- Follow current official agency or journal instructions and templates; general conventions are defaults. Do not infer requirements from common practice.
- Editing requests authorize in-scope changes. Ask before substantive changes beyond that scope, wholesale source replacement, format conversion, or project reorganization. Preserve the existing document format and bibliography system unless a change is approved.
- Every review issue, including minor findings, needs a source location, rationale, severity, and concrete suggested revision beneath it. Alternatives are allowed; mark one recommended. Do not apply suggestions without authorization. Describe model-generated reviews as simulated perspectives, not external peer review.
- Drafts may exceed page, word, or character limits during the drafting stage. When a draft exceeds a limit, ask the author what working tolerance to allow for this project and document, and record the confirmed answer in `log/decisions.md` when a workspace exists. Never cut or condense text solely to meet a limit without approval; when a draft is materially over, propose specific cuts and wait for approval. Submission-ready files must meet every limit.
- Save retrieved external sources locally with provenance in every scope, including reviews, following Module 08. Authorized personal retrieval is distinct from redistribution; redistribution restrictions alone do not justify refusing retrieval. Record genuine access or storage limitations. When no document workspace exists, as with pasted text, create only the needed target folder on demand (`guidelines/source/`, `references/papers/`, or `references/literature-search/`) in the current working directory and record provenance in its ledger rather than scaffolding the full workspace.
- Track the agent's own edits to existing files: use tracked changes in DOCX and ODT, and provide a `latexdiff` output for LaTeX or a unified diff for Markdown and other plain-text sources. Keep pre-edit copies and diffs in `build/`, or rely on Git history when the project is a repository. If tracked changes cannot be produced, keep the original, save the edited copy under a new name, provide a comparison the author can open, and report the limitation. For pasted text, mark the changes alongside the revised text. New documents the agent drafts need no tracked changes. Do not accept the agent's tracked changes on the author's behalf.
- Obtain permission before installing software or changing Git state, including initialization, staging, commits, tags, or `.gitignore`. Read-only Git inspection is allowed; check the repository root before modifying it and exclude unrelated files.

## Workspace handling

Preserve existing project structure. Module 01 defines the default layout and detailed handling rules; create only needed folders. This is a writing workspace, not a raw-data or data-analysis pipeline.

When working in a document workspace, inspect files in `intake/` and sort them without changing contents or overwriting files. Placing files there authorizes sorting, not editing. Leave uncertain or blocked files in intake. Keep brief dated records in `log/intake.md`, `log/edits.md`, and `log/decisions.md` for intake actions, completed edit batches, and confirmed author decisions. Detailed critiques belong in `reviews/`; recommendations are not approvals.

## References by task

Load only the references needed for the active task, combining them when necessary. The module numbers identify files, not a mandatory workflow. Resolve links and template paths relative to this skill directory.

| Task or need | Reference |
|---|---|
| Workspace setup, intake placement, submission instructions, or Git handling | [01: Workspace and guidelines](skill-modules/modules/01_foundations_guidelines_and_git.md) |
| Study design, statistical reporting, rigor, or supplied-result provenance | [02: Reporting and rigor](skill-modules/modules/02_reporting_standards_rigor_and_provenance.md) |
| All scientific drafting and prose revision, including small edits | [03: Scientific prose](skill-modules/modules/03_document_modes_and_prose_craft.md) |
| Drafting sections, organizing an argument, or synthesizing literature | [04: Section architecture](skill-modules/modules/04_section_architecture_and_synthesis.md) |
| Literature discovery, citation verification, figures, or tables | [05: Figures and citations](skill-modules/modules/05_figures_tables_and_citations.md) |
| Scientific review, revision options, or reviewer responses | [06: Review and rebuttals](skill-modules/modules/06_simulated_review_and_rebuttals.md) |
| Compilation, format conversion, submission preflight, or packaging | [07: Export and delivery](skill-modules/modules/07_compilation_preflight_and_packaging.md) |
| Retrieving or downloading any external source, including during reviews | [08: Source capture](skill-modules/modules/08_source_capture_and_provenance.md) |

## Handoff

Check the changed text for unsupported facts and artificial phrasing. Return revised text for edits, findings with suggested revisions for reviews, or the requested files for production. Verify only what the task requires and report unresolved questions or blocked checks. Inspect rendered outputs before claiming layout compliance or submission readiness; use the document states in Module 07.
