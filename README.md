<p align="center"><img src="assets/weaver-text.jpg" alt="weaver-text badge" width="200"></p>

# weaver-text

AI editing help for scientists who write their own manuscripts and grant proposals. The author supplies the ideas, argument, and data and makes the final decisions on wording. The skill edits, reviews, checks citations, and prepares the submission, at the scope each task needs.

Part of a four-skill research suite: `beaver-data` (analysis), `weaver-text` (editing support for author-written text), `honeybee-lit` (general literature reviews), and `wasp-lit` (post-GWAS candidate gene-phenotype literature analysis).

## Why a weaver?

A weaver bird builds its nest strand by strand, and a poorly built nest is inspected and rebuilt. `weaver-text` helps an author tighten each strand of their own text: every claim ties to its evidence, and every review finding comes with a concrete revision the author can accept or reject.

## Reproducibility and standardization

- **Saved sources.** Retrieved guidelines and references are saved locally with provenance, including during reviews (Module 08).
- **Current official rules.** Journal and agency instructions are retrieved and followed. Requirements are never inferred from common practice.
- **Reproducible figures.** Figures and tables are generated from supplied results, with source records, never from invented values.
- **Standard review format.** Every finding, including minor ones, gives a location, rationale, severity, and suggested revision.
- **Reporting-standard checks.** Statistics, causal claims, and study design are checked against the relevant reporting guidelines (Module 02).
- **Decision logs.** Intake actions, edit batches, and author decisions are recorded in `log/intake.md`, `log/edits.md`, and `log/decisions.md`.
- **Verified output.** Rendered documents are inspected before any submission-readiness claim, and blocked checks are reported.

## What it does

| Task | What the author gets |
|---|---|
| Edit | Clearer, tighter versions of the author's own sentences or sections, within the requested scope. |
| Review | Findings with suggested revisions; the author's text stays unchanged until they approve a change. |
| Production | Help assembling the author's material into a submission: figures from supplied results, references, compliance checks, export, and packaging. |

- Line editing for clarity, concision, tense, and tone, keeping the author's voice and meaning.
- Structural feedback on sections and argument flow, offered as suggestions.
- Citation verification, claim-support checks, and publication-status checks.
- Simulated scientific and funding reviews to stress-test a draft before submission, plus help with rebuttals.
- Markdown for early drafts; LaTeX, DOCX, and ODT for production. Existing formats and bibliography systems are kept unless the author approves a change.

## The author stays in charge

- The skill does not invent facts, methods, results, or references. Gaps become `[AUTHOR QUERY: ...]` markers for the author to resolve.
- Edits stay within the requested scope. Larger changes are proposed, not made.
- Review suggestions are applied only with the author's approval.
- Text is never cut solely to meet a length limit; cuts are proposed for the author to choose.
- Software installation and Git changes require permission.

## Package contents

```text
weaver-text/
├── SKILL.md                    # Agent instructions and module routing
├── README.md
├── LICENSE
├── assets/weaver-text.jpg
└── skill-modules/
    ├── references/             # Modules 01 to 08 and the writing-sources register
    └── templates/              # Guidelines README, requirements matrix, results manifest, search record
```

## Project workspace

Create only the folders a task needs, and keep any existing layout ([Module 01](skill-modules/references/01_foundations_guidelines_and_git.md)).

| Purpose | Folders |
|---|---|
| Receive files | `intake/` |
| Establish context | `guidelines/`, `references/`, `results/` |
| Plan and write | `plan/`, `drafts/`, `figures/` |
| Evaluate | `reviews/` |
| Deliver | `final/` |
| Record | `log/` |

Files in `intake/` are sorted without changing contents. `results/` holds supplied findings, not an analysis pipeline; use `beaver-data` for analysis.

## Companion skills

| Skill | Role |
|---|---|
| [`beaver-data`](https://github.com/chen42/beaver-data) | Approved statistical analysis, including quantitative evidence synthesis. |
| [`weaver-text`](https://github.com/chen42/weaver-text) | AI editing, review, and submission help for author-written manuscripts and grant proposals. |
| [`honeybee-lit`](https://github.com/chen42/honeybee-lit) | General literature reviews, from citation checks to narrative, scoping, and systematic reviews. |
| [`wasp-lit`](https://github.com/chen42/wasp-lit) | Post-GWAS literature analysis of candidate gene-phenotype relationships. |

## Installation

Clone the repository, unchanged, into a skills location your agent scans:

```bash
# Pi
git clone https://github.com/chen42/weaver-text.git ~/.pi/agent/skills/weaver-text
# Claude Code (user or project scope)
git clone https://github.com/chen42/weaver-text.git ~/.claude/skills/weaver-text
```

In Pi, run `/reload` after cloning. Export to DOCX, ODT, or PDF depends on locally available tools such as LaTeX, Pandoc, or LibreOffice.

## License

[MIT](LICENSE)
