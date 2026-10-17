# Module 05: Figures, tables, and scholarly citations

**Applies to:** Journal manuscripts and grant proposals. Covers figures and tables as scientific arguments, reproducible script generation, table design standards, citation verification, and citation ethics.

## 1. Figures and tables as scientific argument

Scientific displays must be self-contained: an expert reader should be able to understand the experimental design, data distribution, and statistical outcome solely from the display and its caption, without reading the main narrative. Reviewers routinely inspect figures before reading the text.

### Figure caption requirements

- **Informative title line**: State the supported finding or the purpose of the display. Use descriptive titles for schematics, workflows, and proposed experiments rather than implying that they report completed results.
- For empirical displays, define the applicable items below. Schematics and other non-data figures do not require invented sample sizes or statistical tests:
  - The experimental model, intervention, and primary readout.
  - Group definitions and the exact analyzed sample size per group (for example, "$n = 8$ mice per group").
  - The definition of error bars (explicitly state whether bars represent standard deviation, standard error of the mean, or 95% confidence intervals).
  - Analysis-appropriate statistical methods and results, including multiplicity adjustments and degrees of freedom when applicable. Use a linked table for extensive results if the target permits it.
  - The meaning of all symbols, abbreviations, and annotations.
  - The unit of biological replication (for example, individual animals rather than repeated technical assays).

### Grant proposal captions

Grant page limits usually make journal-length captions impractical. Keep proposal captions to a declarative takeaway, concise panel definitions, group sample sizes, and the definition of the error bars. Put test statistics, model specifications, and multiplicity details in the Approach narrative rather than repeating them in caption blocks. Check whether the mechanism requires any content, such as a scale bar or panel-specific dose, to appear in the caption itself.

### Visual layout and data distribution standards

- **Self-contained visual chapters**: Design multi-panel figures as self-contained narrative chapters where sub-panels flow in logical reading order (Panels A to B to C) and converge on the central question.
- **High data efficiency**: Maximize the proportion of ink dedicated to actual data. Eliminate non-data ink: remove heavy background grids, decorative borders, faux three-dimensional bar volumes, and drop shadows.
- **Small multiples for complex comparisons**: When comparing multiple treatment groups, genotypes, or time points, arrange small, identically scaled sub-panels in a grid rather than overcrowding a single plot with dozens of overlapping traces. This enables immediate visual comparison without cognitive fatigue.
- **Show distributions**: Avoid bar charts (dynamite plungers) for small or continuous sample distributions because they hide data spread, bimodal patterns, and outliers. Prefer dot plots with individual data points, box-and-whisker plots with overlaid points, violin plots, or estimation plots showing effect sizes and confidence intervals.
- **Axis integrity**: Do not use axis limits to exaggerate differences. Bar charts representing counts or amounts should start at zero. Other displays may use clearly labeled restricted ranges when appropriate. Use logarithmic axes for fold-change or ratio data when they aid interpretation; label the scale and ticks explicitly.
- **Multi-panel hierarchy**: Group sub-panels logically. Use bold capital letters (A, B, C) in a clean, consistent sans-serif font (for example, Arial or Helvetica). Ensure all panels are cited sequentially in the text.
- **Microscopy and imaging**: Include calibrated scale bars directly on images, state scale bar lengths in the legend, identify staining targets or fluorophores clearly, and ensure that contrast adjustments are linear across the entire image and applied identically to control and treatment groups.

---

## 2. Table design standards

Scientific tables must communicate data clearly without decorative clutter. The following are defaults subject to the target's official template. Use equivalent border, alignment, and footnote settings for DOCX/ODT tables rather than literal LaTeX commands.

- **Scientific booktabs rules**: Follow standard academic typography:
  - Use `\toprule` above the column headings.
  - Use `\midrule` below the column headings.
  - Use `\bottomrule` at the base of the table.
  - Strictly zero vertical rules. Avoid double horizontal lines.
- **Alignment on decimal points**: Align numeric columns on the decimal point using appropriate packages (such as `siunitx` or `dcolumn` in LaTeX). Do not center-align numeric columns.
- **Self-contained table footnotes**: Define every abbreviation and symbol in a dedicated table footnote block.
- **Units in column headers**: Place measurement units in the column or row headers (for example, "Dose (mg/kg)" or "Concentration ($\mu$M)"), not repeated inside individual data cells.

---

## 3. Reproducible visual scripting

Generate data plots through reproducible code where feasible. For microscopy, supplied figures, and manually assembled diagrams, retain source assets and document acquisition, processing, assembly, and export steps instead of requiring a plotting script for every visual. Do not redraw or replace supplied figures during a focused edit unless requested.

- **Languages**: Preserve the project's plotting ecosystem. For new analysis and plotting code, prefer R (`ggplot2`) unless Python has a distinct advantage or the project already uses it.
- **Reproduction entry point**: Provide a script or documented workflow for each generated plot, including inputs, dependencies, parameters, and outputs. Shared functions and project pipelines are acceptable; each figure need not duplicate all code in a standalone script. Use `figures/` for code and display assets and `results/` for supplied findings and plotting inputs when they fit the approved project structure. Generating a display from supplied results does not authorize a new statistical analysis.
- **Non-code assets**: Record the source file, creator or provider, software and version, editable assembly file where available, processing steps, and any use restrictions. Keep original imaging inputs unchanged.
- **Vector formats preferred**: Export plots, charts, and diagrams as vector PDF or SVG for publication. Use raster formats (PNG or TIFF) only for photography, microscopy, or complex heatmaps.
- **Resolution standards**: For raster output, render at minimum 300 DPI for photographs, 600 DPI for combination image-and-line art, and 1200 DPI for pure line art.
- **Accessible, CVD-safe palettes**: Palettes must remain interpretable by individuals with color-vision deficiencies (protanopia, deuteranopia, tritanopia) and when printed in monochrome grayscale:
  - Choose a palette suited to the data, such as Okabe-Ito for categories or viridis/cividis for sequential values. Check the actual display in relevant color-vision simulations and grayscale; a named palette or agency color scheme alone does not establish accessibility.
  - Dual encoding: Combine color with distinct point shapes, line styles (solid, dashed, dotted), or hatch patterns so that color is never the sole differentiator.

---

## 4. Scholarly citation verification and active literature search

Follow the current journal or mechanism's citation style and preserve the existing bibliography system. Use compact numeric citations only when permitted and appropriate; do not assume that grants and manuscripts require different formats.

Never rely on model memory for bibliographic metadata. Hallucinated PMIDs, DOIs, or author lists constitute scientific defects.

### Active literature search and discovery routing

Search when requested or needed to resolve a citation or evidence concern within the active scope. Use a relevant literature skill when available, or consult authoritative databases directly; never generate unverified citations.

- **When to initiate a search**:
  - Resolving missing citation tags (`[AUTHOR QUERY: citation needed]`) in narrative sections.
  - Finding prior experimental precedents, benchmark values, or historical bottlenecks for grant Significance and Innovation sections.
  - Reconciling contradictory experimental observations in the Discussion.
  - Sourcing published peer-reviewed evidence to support author responses during reviewer rebuttals.
  - Verifying whether cited bioRxiv, medRxiv, or arXiv preprints have since appeared in peer-reviewed journals.

- **Routing matrix to specialized literature skills**:
  - *Biomedical literature, abstracts, and MeSH terms*: Delegate to the `pubmed-database` skill.
  - *Open-access life-sciences full texts and PMCIDs*: Delegate to the `literature-search-europepmc` skill.
  - *Cross-disciplinary citations, author metrics, and broad scholarly works*: Delegate to the `literature-search-openalex` skill.
  - *Recent life-sciences preprints*: Delegate to the `literature-search-biorxiv` skill.
  - *Computational biology, machine learning, and physical science preprints*: Delegate to the `literature-search-arxiv` skill.
  - *Human clinical trial protocols, endpoints, and registered outcomes*: Delegate to the `clinical-trials-database` skill.

- **Intake and verification protocol**:
  1. Formulate scoped queries using precise biological entities, assay names, or MeSH terms.
  2. Present candidate papers to the author with author names, title, journal, year, and a concise 1-sentence summary of the evidentiary support provided.
  3. In review-only tasks, report candidates without modifying the bibliography or manuscript. Save the relevant abstracts as a literature search record in `references/literature-search/`, following Module 08, so the review is reproducible at abstract level. When citation additions are explicitly requested, add verified references within that scope. Obtain approval before changing scientific claims beyond the requested scope.

### Authoritative database verification

Verify added or audited citations against authoritative records appropriate to their source type. Audit the complete library when required for full production or explicitly requested; a focused edit does not require verification of every untouched reference:
- Biomedical and life sciences: NCBI PubMed API or Europe PMC.
- Cross-disciplinary: Crossref API, OpenAlex, or publisher records.
- Datasets and repositories: DataCite or repository-specific DOIs.
- Clinical trials: ClinicalTrials.gov NCT identifiers.
- Official guidelines and software: Publisher, governmental, or release archive URLs.

### Verify evidentiary support separately

A valid DOI, PMID, or bibliographic record establishes identity, not support for a claim. For each added or audited citation:

1. Locate the passage, result, table, or figure supporting the specific claim.
2. Check the population or model, design, intervention or exposure, outcome, and limitations relevant to that claim. Do not transfer a finding to a different context without qualification.
3. Record the evidence level: abstract only, full text, registry record, official documentation, or another specified source. Abstract-only checks cannot establish details absent from the abstract.
4. Record the source location and access date in the audit response or, when persistent records are part of the task, in the search or review record.
5. Distinguish metadata verified, claim support assessed, and publication status checked. If access or tools prevent a check, mark it Not checked or Blocked and state what remains unresolved.

### Reference library organization

Preserve the existing reference system and structure. For new projects, the following organization is a default, not a requirement to migrate a citation manager or create directories for a focused edit:

- `references/papers/`: Store downloaded full-text PDFs, preprints, and whitepapers. Use a consistent naming convention such as `FirstAuthorYear.pdf` or `FirstAuthor_Keyword_Year.pdf`.
- `references/notes/`: Store the user's notes and clippings, plus literature summaries or extraction tables that map findings to manuscript sections or claims.
- `references/references.bib`: Store verified, clean BibTeX entries. Keep this file reserved for entries that are cited or actively vetted for citation.
- Official style files (`.bst`, `.csl`): Store journal or agency bibliography styles directly inside `references/`.

Save relevant abstracts and any retrieved full texts following Module 08. Retain an abstract when it is relevant for any reason, including background or methods, and discard irrelevant results. In review-only tasks, leave the author's bibliography unchanged unless editing is requested.

### Clean BibTeX database standards

Preserve the existing reference manager or bibliography system. For BibTeX projects, use `references/references.bib` only when it fits the existing structure. Keep fields separate rather than compressing metadata into the journal title.

The following is a non-citable field template, not a publication record. Replace placeholders with verified metadata and omit identifiers that do not exist for the source type. Never add the template itself to a working bibliography:

```bibtex
@article{PLACEHOLDER_NOT_A_CITATION,
  author  = {VERIFIED_AUTHOR_LIST},
  title   = {VERIFIED_TITLE},
  journal = {VERIFIED_JOURNAL},
  year    = {VERIFIED_YEAR},
  volume  = {VERIFIED_VOLUME},
  number  = {VERIFIED_ISSUE},
  pages   = {VERIFIED_PAGES_OR_ARTICLE_NUMBER},
  doi     = {VERIFIED_DOI_IF_AVAILABLE},
  pmid    = {VERIFIED_PMID_IF_AVAILABLE}
}
```

Use the official `.bst` or CSL style provided by the target agency or journal. Do not generate custom replacement styles without user authorization.

---

## 5. Citation ethics and preprint policy

- **Primary source attribution**: Cite original discoverers and method developers for specific claims, assays, and algorithms. Avoid citing review articles as the sole attribution for an empirical observation.
- **Cite software and data**: Cite data repositories, public datasets, analysis software, and open-source packages alongside traditional journal articles.
- **Publication status checks**: For added or audited references, check relevant publisher notices, PubMed notices, or Retraction Watch records for retractions, corrections, withdrawals, and expressions of concern. Before submission-ready release, complete the applicable reference audit or report unresolved checks. Record sources and access dates; an incomplete search does not establish the absence of notices.
- **Preprint citation rules**:
  - Check whether a cited bioRxiv, medRxiv, or arXiv preprint has since been published in a peer-reviewed journal. Before replacing it, confirm that the published version still supports the cited claim; results and conclusions may differ. Prefer the published version when it provides the required support, subject to the target's policy and the authorized edit scope.
  - If the preprint remains unpublished, verify that it has not been withdrawn or flagged.
  - Label preprints explicitly as such in the text or reference list when required by the journal or funding agency.
- **Eliminate citation abuse**: Strictly avoid citation stuffing, gratuitous self-citation, and coercive citation patterns.
