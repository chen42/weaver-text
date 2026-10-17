# Evals

`evals.json` lists behavior checks for the skill's main promises: scope discipline, review without editing, no invented values, length-limit handling, tracked changes, source saving, and citation verification.

To run an eval, create a scratch project, copy the listed fixture files from `evals/files/` into the paths the prompt names (for example, `evals/files/results.md` to `drafts/results.md`, and `evals/files/intake/` to `intake/`), run the prompt with the skill loaded, and grade the output against each expectation. The format follows the skill-creator `evals.json` convention.
