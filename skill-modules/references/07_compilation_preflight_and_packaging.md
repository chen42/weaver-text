# Module 07: Compilation, preflight QA, and packaging

**Applies to:** Final preparation, verification, layout audits, and deliverable packaging for scientific manuscripts and grant proposals. Supported production formats are LaTeX, DOCX, and LibreOffice ODT. Markdown is acceptable for first drafts and is converted before packaging.

## 1. Scope and document states

Compile or export only when it is part of the requested task. A focused text edit does not require a build, a new workspace, or a submission package. Preserve the existing source format and toolchain; do not convert documents merely to fit an example command. Markdown is an acceptable first-draft format; convert it to the required submission format before preflight and packaging, and do not submit Markdown unless the target explicitly accepts it.

Distinguish these states in the delivery summary:

- **Draft**: Working text that may contain visible author queries, missing inputs, or unchecked requirements. Preserve unresolved queries and identify them in the handoff.
- **Reviewed**: The requested checks have been performed and findings reported. State the scope, open findings, and any Not checked or Blocked items. This label does not certify submission readiness.
- **Submission-ready**: The required components have been prepared, relevant mandatory requirements verified, and blocking findings resolved. No unresolved author queries remain in submission files. Do not use this label when a required check is incomplete.

Record verification evidence in the existing requirements record when one is maintained. Missing tools or unavailable inputs must be reported, not treated as successful checks.

## 2. Reproducible compilation and export

Use `drafts/` for editable sources, `build/` for temporary output, and `final/` for checked deliverables when these folders fit the approved project structure. Check tool availability and versions before building. Obtain approval before installing software or skills. Preserve original sources and write conversion outputs to a separate location.

### Markdown drafts

Markdown is suitable for first drafts and for text that will later move into a submission format.

- Keep the draft portable. Use standard Markdown for headings, emphasis, lists, tables, and links. Use inline math where needed (for example, `$F(1, 24) = 6.42$`) and avoid raw HTML or tool-specific extensions that do not survive conversion.
- Agree on the target format and converter before drafting, because the converter determines how much structure carries over. Confirm the converter is available, and obtain approval before installing one.
- Represent figures and tables with their source path or generating script and a caption placeholder rather than pasted images alone.
- Convert to LaTeX, DOCX, or ODT before preflight and packaging. Treat conversion as a draft-to-submission step, and inspect the output for lost structure, especially displayed equations, tables, citations, footnotes, and cross-references.
- Apply the same checks to a converted document as to a natively authored file. A successful conversion does not establish layout, reference, or citation integrity.

### LaTeX

Use the project's existing engine and bibliography backend. For a project using `latexmk`, an example build is:

```bash
mkdir -p build final
latexmk -pdf -interaction=nonstopmode -file-line-error -outdir=build drafts/main.tex
```

For an existing LuaLaTeX project:

```bash
latexmk -pdflua -interaction=nonstopmode -file-line-error -outdir=build drafts/main.tex
```

Require a successful exit, inspect the log and rendered pages, and confirm the PDF belongs to the current build before copying it to `final/`. Do not release a stale PDF after a failed build. Verify bibliography and image paths under the actual working directory and output-directory configuration.

### Linux DOCX support

The optional [`docx` skill from `anthropics/skills`](https://github.com/anthropics/skills/tree/main/skills/docx) provides creation, editing, tracked-change handling, validation, and rendering workflows using Node.js, Python, and LibreOffice. Its source includes a Linux LibreOffice helper for sandboxed environments. This is an optional dependency, not an assumption that the skill or its packages are installed.

1. If the `docx` skill is installed, read its `SKILL.md` and relevant linked instructions. Resolve its script paths relative to that skill, not this one. Check current dependencies and license terms before use; claims about preinstalled packages in the external skill do not establish availability locally.
2. If it is not installed, ask before installation. If installation is unavailable or not approved, use LibreOffice ODT as the working format when the user permits conversion. Preserve the original DOCX. If DOCX must remain the source, use LibreOffice only with the user's approval and audit round-trip fidelity; otherwise report the dependency as Blocked.
3. For a new DOCX, use the verified skill's generation workflow. For an existing DOCX, use its editing workflow or an approved LibreOffice workflow; do not regenerate the document through a Markdown round trip or a creation-only library.
4. Preserve styles, numbering, fields, equations, citations, hyperlinks, headers, footers, section breaks, comments, and tracked changes. Do not accept or reject changes without authorization. Text extraction is an inspection aid, not a lossless editable source.
5. Validate the DOCX using the available skill tools and render it with LibreOffice. Inspect the PDF page by page. Rendering in LibreOffice does not establish identical pagination in Microsoft Word; report that limitation when relevant to the submission.
6. Deliver the editable DOCX and checked PDF when requested. An ODT or PDF substitute does not satisfy a mandatory DOCX requirement.

### LibreOffice ODT

Use LibreOffice Writer with ODT as the fallback authoring format when a suitable DOCX workflow is unavailable and the user permits it. Preserve the supplied document and record any conversion. Use paragraph, character, table, and page styles rather than manual spacing to control layout. Verify the availability of any automation interface before relying on it.

For either DOCX or ODT, this Linux example renders to a fresh output directory with an isolated LibreOffice profile. The commands assume the source file and dependencies exist; save them as a script when reproducible export is in scope:

```bash
set -eu
mkdir -p build final
render_dir=$(mktemp -d "$PWD/build/render.XXXXXX")
profile_uri=$(python3 -c 'from pathlib import Path; import sys; print(Path(sys.argv[1]).as_uri())' "$render_dir/profile")

# Use drafts/main.odt instead when ODT is the working source.
libreoffice "-env:UserInstallation=$profile_uri" --headless \
  --convert-to pdf --outdir "$render_dir" drafts/main.docx

test -s "$render_dir/main.pdf"
```

Check both the conversion exit status and the expected output; LibreOffice messages alone do not certify a successful export. An installed LibreOffice binary does not establish rendering availability: sandbox restrictions may block required Unix-domain sockets. If rendering fails, use the installed DOCX skill's verified helper where permitted, or report the block. Do not install or load unreviewed helpers.

Keep the rendered PDF for inspection before copying it to `final/`. Use the original basename or record any intentional renaming. For ODT-to-DOCX export, check the new DOCX separately for layout and structural changes, especially equations, fields, citations, tables, and tracked changes. Retain the editable ODT when it is the working source.

## 3. Build logs and document integrity

Apply checks appropriate to the format:

- **Build failures**: Inspect exit status and logs. Do not release outputs from an unsuccessful build or conversion.
- **Undefined citations and references**: For LaTeX, inspect citation and reference warnings and verify all callouts resolve. For DOCX/ODT, inspect citation fields, cross-references, numbering, and unresolved field errors. Preserve the existing bibliography system rather than requiring BibTeX for every format.
- **Overflow and clipping**: Review all LaTeX overfull-box warnings and inspect affected pages. No fixed warning threshold establishes margin compliance. For DOCX/ODT, inspect tables, equations, floating images, headers, and footers for clipping or overlap.
- **Missing glyphs**: Check compiler or export warnings and rendered mathematical symbols, Greek letters, and other characters.
- **Fonts**: Verify required fonts, substitutions, and PDF embedding against the governing instructions. Inspect embedded fonts with `pdffonts`; do not assume every portal has the same rejection policy.
- **Editable source integrity**: Confirm that DOCX/ODT opens correctly and retains required editable content, comments, and tracked changes. Report checks that could not be performed.

Example PDF font inspection:

```bash
pdffonts build/main.pdf
```

Use the actual rendered PDF path. Record tools, versions, build commands, and relevant warnings when reproducible production is in scope. Keep compiler and rendering logs under `build/`, not in the brief project-memory logs. Record completed document edit batches in `log/edits.md` and confirmed author decisions in `log/decisions.md` as described in Module 01.

## 4. Submission preflight

Check the rendered deliverable against the current official instructions and `guidelines/requirements.md` when maintained.

### Layout and components

- Count pages, words, and characters as applicable according to the target's definition, including which components and references count toward each limit. Check display-item caps where required. Report the counts and any overage. Do not cut text to reduce the count; when the document is more than two pages over, propose specific cuts and pruning options and wait for approval before packaging. Overages within the two-page allowance may proceed, with the overage stated in the delivery summary.
- Distinguish separately uploaded attachments from sections in a single file. Apply page breaks only where required by the actual document structure.
- Verify page size, margins, fonts, line spacing, headers, footers, and file-format requirements without assuming generic agency values.
- Inspect every rendered page for clipping, overflow, overlapping captions, blank pages, incorrect numbering, and misplaced figures. If visual inspection is unavailable, mark it Not checked or Blocked.

### Figures and tables

- Check legibility at the final display size and verify panel labels and callouts.
- Check vector output and raster resolution against the target's requirements. Retain provenance for supplied or manually assembled assets as described in Module 05.
- Confirm captions, units, group definitions, sample sizes, and uncertainty measures where applicable.

### Narrative and reference checks

- Preserve unresolved author queries in drafts; exclude them from submission-ready files only after resolution, not by silently deleting the uncertainty.
- Audit acronym definitions only within the requested scope and governing requirements. Do not expand or rename established acronyms during a focused edit by default.
- Check editable prose for rhetorical em dashes and en dashes and for unwanted typographic quotation marks. Preserve numeric ranges, minus signs, hyphens in compound and eponymous names, and en-dash ligatures used as notation. Exclude verbatim quotations, reference titles, code, identifiers, official templates, and other protected source content from automatic replacement.
- Verify bibliographic metadata, claim support, and publication status separately as described in Module 05. State the evidence level and any incomplete checks.
- Refresh permitted cross-references and fields, then verify their values and locations in the final render. Do not assume all fields update correctly during headless conversion.

## 5. Deliverable packaging

Package only requested or required deliverables. Adapt names and structure to the target rather than creating every example file:

```text
final/
├── manuscript_main.pdf
├── manuscript_main.docx             # When DOCX is required or requested
├── manuscript_main.odt              # When ODT is the approved working source
├── supplementary_information.pdf
├── submission_source_bundle.zip     # When source submission is required
└── checklists/                      # Required completed reporting checklists
```

- For LaTeX source submissions, include the required `.tex`, `.bib`, `.bst`, class/style files, figures, and `.bbl` files when the target requires them. Preserve relative paths. Do not omit a required `.bbl` merely because it is generated.
- Rebuild source bundles from a clean extraction in a separate directory without depending on the original workspace. Record any permitted external dependencies. If the receiving system cannot be reproduced locally, report the unverified portion.
- For DOCX/ODT submissions, include the required editable file, checked PDF if requested, and any required supplements or checklists. Do not replace a required source format with a PDF alone.
- When Markdown was the draft source, keep the draft in the project source directory and include it in the package only if the target accepts Markdown or the user requests it.
- Exclude scratch notes, review logs, temporary profiles, build caches, stale outputs, and unrelated files unless explicitly required.
- Record the document state, source version, verification scope, unresolved items, and final filenames in the delivery summary or release record. Include brief logs only if requested; do not copy the entire `log/` directory into a submission package by default.
- Tag or otherwise change Git state only when authorized. Use a user-approved tag name rather than assuming `v1.0-submission`.
