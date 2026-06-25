# Maintainer Notes

Technical notes for whoever maintains this repo.

---

## What gets committed (whitelist)

`.gitignore` uses a **whitelist** for course folders: everything inside
`courses/<slug>/` is ignored by default, and only these paths are tracked:

- `README.md`
- `summary.tex` / `summary.pdf`
- `exams.tex` / `exams.pdf`
- `exams_solutions.tex` / `exams_solutions.pdf`
- `figures/` (images used by the summary)
- `courses/deep-reinforcement-learning/cheatsheet.{tex,pdf}` (course-specific exception)

Everything else stays local and never gets committed: lecture slides
(`slides/`), raw exam scans, exercise notebooks, quiz/real-exam dumps,
cheat-sheet underlays, `.claude/`, and LaTeX build artifacts. This lets you
keep source/study material in the course folder without it entering git.

To publish a **new** document type, add an explicit `!` rule to the courses
block in `.gitignore`.

If a file was committed under an older policy and should now be ignored,
untrack it without deleting the local copy (`git rm --cached` only removes it
from the index):

```bash
git rm --cached courses/<course-slug>/<file>
git commit -m "Stop tracking <file>"
```

---

## Template PDFs

`templates/summary_template.pdf` and `templates/exams_template.pdf` are explicitly allowed in `.gitignore` and should be kept up to date whenever the templates change.

---

## GitHub Actions — LaTeX compilation check

A LaTeX CI workflow is defined in `.github/workflows/latex-check.yml`. It attempts to compile changed `.tex` files on pull requests using a TeX Live container.

LaTeX CI is inherently fragile (package version differences, missing fonts, etc.). The workflow is configured with `continue-on-error: true` so it never blocks a merge. Treat it as informational — a failing check may mean the CI environment is missing a package rather than the `.tex` file being broken.

**TODO:** If the action causes more noise than signal, disable it and rely on contributors compiling locally before submitting PRs.

---

## Adding a course to the README course index

When a new course folder is added:
1. Add a row to the course table in `README.md`.
2. Link to the course folder and any available PDFs.
3. Set status to `draft`, `usable`, or `reviewed`.

---

## Renaming a course folder

Use `git mv` to preserve history:

```bash
git mv courses/old-name courses/new-name
git commit -m "Rename course folder to new-name"
```

After renaming, update the course's `README.md` and the root `README.md` course table.

---

## GitHub repository metadata

Set these in the repository **Settings → General** on GitHub to improve discoverability:

**Description:**
> LaTeX lecture summaries and exam question collections for the AI Master programme.

**Topics (comma-separated):**
`latex`, `study-notes`, `machine-learning`, `artificial-intelligence`, `university`, `exam-preparation`, `lecture-notes`

These cannot be set from inside the repo — they must be configured in the GitHub web UI.
