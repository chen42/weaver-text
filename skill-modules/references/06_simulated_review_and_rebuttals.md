# Module 06: Simulated review, rebuttals, and decision tracking

**Applies to:** Simulated internal red-team review of drafts, formal responses to real journal peer reviewers, and grant resubmission rebuttals.

## 1. Simulated peer review lenses

Use review lenses relevant to the document and requested scope. State that these are model-generated perspectives, not reviews by external experts or agency officials. Follow Module 08 when retrieving guidelines, templates, or references.

For NIH proposals, organize simulated findings around the simplified review framework rather than the legacy five scored criteria. The simplified framework evaluates three factors: Factor 1, Importance of the Research, covering Significance and Innovation; Factor 2, Rigor and Feasibility, covering Approach; and Factor 3, Expertise and Resources, covering Investigator and Environment, which is rated rather than scored numerically. Report findings under these factor headings where that helps the author anticipate the actual review structure.

Deploy only lenses relevant to the active document:
1. **Compliance and administrative lens**: Audits page limits, word caps, margin boundaries, font size rules, required sections, and agency-specific instructions, using `guidelines/requirements.md` when maintained. Report over-length findings as advisory. Do not treat an overage as a defect that justifies removing text; propose specific cuts and wait for approval.
2. **Methodological and statistical lens**: Audits experimental controls, blinding, randomization, unit of analysis, statistical tests, power rationale, replicate independence, and reporting transparency.
3. **Scientific prose and clarity lens**: Apply the shared prose guidance in Module 03 and its relevant document-specific subsection. Audit sentence and paragraph craft:
   - Check familiar-to-new flow, the subjects the reader follows, subject-verb proximity, and placement of emphasis without compulsory punchlines.
   - Detects nominalizations and passive constructions where direct verbs would improve clarity.
   - Flags sequences of experiments that lack a clear rationale, while preserving chronology where it serves the explanation.
   - Identifies unnecessary or confusing abbreviations when an acronym audit is in scope. Preserve existing acronyms during focused edits unless changes are requested.
4. **Subject-matter domain lenses**: Scrutinizes mechanistic plausibility, prior literature conflicts, and domain-specific assumptions in the 1 to 2 scientific fields central to the work.
5. **Programmatic and editorial fit lens**: Evaluates alignment with funding agency mission, milestone feasibility, translational roadmap, or journal readership scope.

---

## 2. Review triage and interactive decision protocol

### Severity classification

Classify all review findings into three clear tiers:
- **[Critical]**: Flaws that invalidate the scientific conclusion, introduce fatal methodological gaps, or violate hard administrative submission rules.
- **[Major]**: Gaps in rationale, unresolved alternative interpretations, missing controls, or incomplete statistical reporting that materially affect evaluation of the work.
- **[Minor]**: Localized ambiguities, typographical defects, citation omissions, or formatting inconsistencies.

Every actionable finding includes at least one concrete suggested revision, not only a description of the problem. State the proposed wording, the specific deletion or move, or the exact change to a number, label, or citation. A finding may list several revisions as options, each with its own wording, and one is marked as recommended. When a fact is missing, the suggestion is an author query rather than invented content. Suggested revisions appear in the review output and are not written into the author's source until the user approves them.

### Mechanical edits versus substantive alternatives

- **Review-only requests**: Report findings and suggested revisions without changing source contents, including mechanical defects. Give the proposed wording or specific change for each fix. An explicit request to edit authorizes applying the specified changes; review alone does not.
- **Authorized mechanical edits**: Apply in-scope copyedits, formatting fixes, and typographical corrections in batches without seeking permission for each one.
- **Substantive scientific findings**: Use the following decision protocol for changes beyond the authorized scope:
  1. State the concern and its precise location.
  2. Explain its scientific or compliance basis. Distinguish a documented defect from missing information or a concern that cannot yet be evaluated.
  3. Offer feasible options tailored to the issue, and give each option its suggested wording. Options may include clarifying existing methods, narrowing a claim, providing a supported explanation, retrieving missing information, conducting an authorized reanalysis, or planning an additional experiment. Do not force options into fixed categories or invent alternatives merely to meet a count.
  4. For each option, explain whether it needs new data, analysis, author information, or only a text change, and note relevant trade-offs.
  5. Obtain the user's decision before implementing an out-of-scope scientific change. Do not describe planned experiments or analyses as completed.

### Review records

For full production or a requested saved review, keep detailed findings, revision options, and resolution under `reviews/`. A focused review can return findings in the response without a saved report. Workspace intake and brief edit/decision logs follow Module 01.

Use the template below for a detailed record, adapting it to the scope. Every issue needs a suggested revision; author decisions and applied changes are recorded only when they occur:

```markdown
# Review record: [Document name and version]
- Date: YYYY-MM-DD
- Simulated review lens: [e.g., Methodological & Statistical Referee]
- Scope evaluated: [e.g., drafts/section3_results.tex]

## Item 1: [Short Title of Issue]
- Severity: [Critical / Major / Minor]
- Source location: [File, section heading, or figure identifier]
- Critique: [Exact description of vulnerability]
- Scientific basis: [Guideline citation or methodological principle]
- Suggested revisions: [At least one for every issue, including minor ones. Mark this as a suggestion, not an applied edit.]
  - Revision 1 (recommended): [Proposed replacement text or the specific change. Use an author query where a required fact is missing.]
  - Revision 2 (optional): [An alternative resolution, with its own wording]
- Requires new data or analysis: [Yes / No]
- User decision: [Option selected on YYYY-MM-DD]
- Status: [Open / Awaiting author input / Blocked / Implemented / Verified / No change, with rationale]
- Author response: [Detailed scientific rationale]
- Text modification (only after approval):
  > "[Exact revised text written into the source, or the suggested wording when no change was applied]"
```

---

## 3. Real peer-review rebuttal and resubmission protocol

Use the format required by the current journal or funding mechanism. Journal revisions commonly use a point-by-point response. For NIH resubmissions, consult the current mechanism's Introduction instructions and page limit. Do not assume that NSF or other agencies use the same resubmission attachment or response structure.

The response blocks below are intended for journal responses or other processes that request an itemized rebuttal. Adapt their content and organization to the governing instructions rather than imposing them on every grant resubmission.

### Professional tone and stance

- Maintain an objective, respectful, appreciative, and scholarly tone.
- A brief acknowledgment of the editor and reviewers is appropriate. Do not claim that every comment strengthened the manuscript or use repetitive expressions of gratitude.
- Do not express irritation or dismiss a concern as trivial. Scientific disagreement is appropriate when explained with evidence.
- When disagreeing with a reviewer on scientific grounds, provide a courteous defense supported by published citations, theoretical rationale, or additional preliminary data.

### Contradictory or conflicting reviewer comments

Reviewers sometimes make incompatible requests, such as asking to condense and to expand the same section, or proposing opposing interpretations of the same result. Handle these before drafting responses:

1. Identify the conflict during triage rather than addressing each comment in isolation.
2. Check the editor's decision letter for guidance or a stated priority.
3. Adopt a defensible balance and state the rationale for it, citing the specific changes made.
4. Acknowledge both comments and explain the trade-off without dismissing either reviewer.
5. If the editor gave no direction and the conflict is material, ask the editor to clarify rather than choosing silently.

### Point-by-point rebuttal document structure

Structure the response document cleanly:
1. **Header**: Manuscript tracking ID, title, author list, and date of submission.
2. **Introductory summary**:
   - Express gratitude to the editor and reviewers.
   - Summarize the main improvements made during revision (for example, additional experimental controls, clarified statistical models, expanded discussion of limitations).
   - High-level summary table of major changes if the revision is extensive.
3. **Itemized response blocks**: Group by reviewer (Reviewer 1, Reviewer 2, Reviewer 3). Address every comment without omission.

### Standard response block format

For every single reviewer comment, use the following three-part structure:

```markdown
### Point 1.1: [Reviewer critique summary]

**Reviewer Comment:**
> "[Exact, verbatim quote of the reviewer's comment]"

**Author Response:**
[Direct, clear statement agreeing with the point or politely explaining the scientific perspective. Detail the exact actions taken to resolve the critique, such as performing a new experiment, revising a statistical test, or rewriting a section for clarity.]

**Manuscript Revision:**
[Cite the section and, after final rendering, the verified page and line numbers, followed by an excerpt of the modified text. If no change was made, state that and explain why; do not invent a revision or location:]
> "Revised text excerpt inserted into the manuscript showing the precise wording change..."
```
