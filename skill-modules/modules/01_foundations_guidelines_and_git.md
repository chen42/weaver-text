# Module 01: Foundations, guidelines, Git, and workspace

## 1. Inspect before scaffolding

Preserve an existing project structure unless the user approves a reorganization. These folders belong to the manuscript or proposal workspace, not the skill installation. For a new full-production project, propose this layout and create only the folders needed for the task after approval. Intake sorting, source capture, and brief project logs can create their required folders on demand without creating the entire structure.

```text
project_root/
├── intake/                 # User-dropped files awaiting inspection and sorting
├── guidelines/
│   ├── source/             # Original instructions, templates, and checklists
│   ├── README.md           # Source inventory and provenance
│   └── requirements.md     # Traceable compliance matrix, when needed
├── references/
│   ├── papers/             # Articles and full texts
│   │   └── README.md       # Saved full-text inventory and provenance
│   ├── literature-search/  # Literature search records and retained abstracts
│   ├── notes/              # User notes, extracts, and other short records
│   ├── references.bib      # Verified BibTeX records, when applicable
│   └── *.bst / *.csl       # Official bibliography styles
├── results/
│   └── README.md           # Supplied-result inventory and provenance, when needed
├── plan/                   # Outlines and drafting plans
├── drafts/                 # Manuscript/proposal drafts and editable sources
├── figures/                # Figure assets, plotting code, and rendered figures
├── reviews/                # Detailed critiques, suggested revisions, and rebuttals
├── final/
│   └── checklists/         # Required submission checklists, when needed
├── log/
│   ├── intake.md           # Inspections, moves, and unresolved placements
│   ├── edits.md            # Brief records of completed edit batches
│   └── decisions.md        # Brief author decisions and their reasons
├── build/                  # Temporary compilation/rendering files
└── misc/                   # Relevant materials that fit no other category
```

### Workflow order and folder purposes

The logical workflow is receive (`intake/`), establish context (`guidelines/`, `references/`, `results/`), plan and write (`plan/`, `drafts/`, `figures/`), evaluate (`reviews/`), and deliver (`final/`). This is a guide to file placement, not a fixed sequence. Writing is iterative, and a review can lead back to literature, planning, or drafting. Keep folder names unnumbered; alphabetical display order is acceptable.

The layout above describes each folder's purpose. `results/` holds supplied findings, not a raw-data or derived-data hierarchy. Moving a source to `drafts/` does not authorize editing it, and a file in `final/` still needs its verification state recorded. Keep brief project memory in `log/` separate from detailed critiques in `reviews/` and source inventories.

### Intake handling

When working in a document workspace, check `intake/` at the start of the task and when the user adds files. Placing a file there authorizes inspection and sorting within the workspace, not editing its contents or executing it.

1. Inspect each file's type and contents, including files inside intake subfolders. Classify by purpose rather than extension alone. If a format cannot be inspected with available tools, record the limitation instead of guessing.
2. Choose the destination from the layout above according to the file's purpose. Use `misc/` only for identifiable supporting material that fits no other category, not for unresolved placements. Do not treat a filename containing "final" as proof of submission readiness.
3. Preserve file contents exactly and keep original filenames where possible. Do not overwrite an existing file. Use a distinct name for a different version and record the name change. Keep related files and relative links intact; if a move would break dependencies, leave the files in intake and request a placement decision.
4. Log the inspection outcome and each successful move in `log/intake.md`, including the original path, destination, brief reason, and status. Leave uncertain, unsupported, or unreadable files in `intake/` and log them as pending or blocked. Do not silently delete duplicates or mark a failed move as completed.
5. Files received outside intake are not automatically relocated. Preserve existing project structure unless the user approves a move.

### Brief project logs

Append dated, factual entries as actions occur. Create only the log files that have entries. Use one concise line per file intake, completed edit batch, or author decision, with a second line only when needed. Do not copy entire diffs, review reports, literature summaries, or compiler logs into these records.

- `log/intake.md`: Date, original path, destination or pending location, inspection or move result, and brief reason.
- `log/edits.md`: Date, affected file or section, completed change, and brief reason. A proposed revision is not an applied edit.
- `log/decisions.md`: Date, issue, confirmed author choice or deferral, and brief rationale. Link to the detailed review or plan where useful; do not invent approval or record the agent's recommendation as the author's decision.

For focused file edits, record the completed edit batch without scaffolding a full project. Pasted-text edits with no document workspace do not require folders. Brief logs do not replace approvals, detailed evidence records, or Git history.

## 2. Guideline documents and requirement traceability

Place unmodified guideline documents in `guidelines/source/`. These may include calls for applications, notices of funding opportunity, instructions to authors, reporting checklists, official templates, and amendment notices. Capture applies whenever the task consults a target's guidelines, including a review-only task, and is not limited to full production.

Record source provenance in `guidelines/README.md` using `skill-modules/templates/guidelines_README.md`; follow Module 08 for capture and ledger details. For full production or compliance tasks needing a persistent matrix, create `guidelines/requirements.md` from `skill-modules/templates/requirements_matrix.md`. Focused edits and narrow reviews do not require a new matrix. Resolve template paths relative to the skill directory. Trace each recorded requirement to a source and page, section, or URL anchor; flag uncertainty as an author query.

Use this precedence unless the user or official documents specify otherwise:

1. Current amendment or correction.
2. Current call, solicitation, or instructions to authors.
3. Official template for the selected mechanism or article type.
4. General agency or journal policy.
5. This skill's default conventions.

Ask the user to resolve material conflicts that the documents do not resolve.

## 3. Safe Git use

Read-only inspection commands, including `git rev-parse --show-toplevel`, `git status`, `git diff`, and `git log`, are permitted without separate approval. Before any modifying Git operation:

1. Use `git rev-parse --show-toplevel` to detect the enclosing repository root. If no repository exists, report that fact rather than initializing one automatically.
2. Compare the detected root with the intended project. If the project is inside a larger parent repository, report the enclosing root before proposing changes to repository state.
3. Inspect repository status without modifying it.
4. Obtain permission before `git init`, staging, committing, tagging, or changing `.gitignore`.
5. Stage only files within the approved task scope. Do not include unrelated changes.

For an approved full-production workflow, useful milestones include baseline, draft, figures, review response, and release. Treat these as suggestions rather than mandatory commits. Use a user-approved tag name instead of assuming `v1.0-submission`.

Do not demand a globally clean working tree. Verify that task files are saved and that intended changes are represented accurately.

## 4. Standard `.gitignore` policy

Prefer a dedicated `build/` directory for transient artifacts and ignore that directory. A baseline `.gitignore` for scientific LaTeX, Python, and R workflows includes:

```gitignore
# Build output directory
build/

# LaTeX compilation intermediates
*.aux
*.fls
*.fdb_latexmk
*.synctex.gz
*.toc
*.out

# Python cache
__pycache__/
*.pyc

# R environment artifacts
.Rhistory
.RData
.Rproj.user/

# Operating system metadata
.DS_Store
Thumbs.db
```

Do not globally ignore `*.log` or `*.bbl` files at the root level if a journal requires a submitted `.bbl` file or if compiler logs serve as scientific records. Place generated build files inside `build/` instead.

Decide explicitly whether to track generated figures, downloaded reference PDFs in `references/papers/`, and final PDFs. Track them when they are required deliverables or when the project cannot reproduce them reliably elsewhere. Saving licensed or restricted documents locally for the user's own use is expected; do not commit or redistribute them without approval. Do not commit confidential files, protected data, large datasets, credentials, or caches without approval.
