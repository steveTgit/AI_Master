# Style Guide

LaTeX formatting rules for contributors. These rules keep all documents visually consistent.

---

## General principles

- **Prose first.** Running text is the default. Colored boxes are landmarks, not the primary content carrier. If you are unsure whether something needs a box, it probably doesn't.
- **One accent color.** All structural elements use `#1B3A5C` (deep navy). Never change this per-document.
- **Boxes sparingly.** Each box type has a specific role. Overusing boxes dilutes their signalling value.

---

## summary.tex — box types

| Box | Color | Use for |
|-----|-------|---------|
| `\begin{defbox}[title={…}]` | Blue | Formal definitions |
| `\begin{thmbox}[title={…}]` | Red | Key theorems, important formulas |
| `\begin{exbox}[title={…}]` | Green | Worked examples |
| `\begin{intbox}` | Amber | Intuition, mental models, "why this works" |
| `\begin{notebox}[title={…}]` | Purple | Exam traps, caveats, things to double-check |

Use `\begin{defbox}` for the first precise statement of a concept. Use `\begin{thmbox}` for results you need to be able to apply on an exam. Use `\begin{intbox}` to explain *why* something works, not just *what* it says.

---

## summary.tex — structure

- One `\chapter{}` per major topic (matching lecture units).
- `\section{}` and `\subsection{}` within chapters.
- No `\chapter{}` in `exams.tex` — it is article class.

---

## exams.tex — question types

| Question type | Format |
|---------------|--------|
| Multiple choice | `\begin{itemize}[leftmargin=1.8em]` with `\choice` items |
| Single number / expression | `\answerline{3cm}` inline at end of question text |
| Calculation / short derivation | `\workingspace{4cm}` on its own line |
| Open / long answer | `\workingspace{7cm}` on its own line |

Adjust `\workingspace` heights to match the expected answer length.

---

## exams.tex — answer key

- Every `exams.tex` ends with `\section*{Answer Key}`.
- Answers are in a manually numbered `enumerate` with `label=\textbf{Q\arabic*.}`.
- **Never** put answers inside `\questiontitle` / `\closequestion` blocks — question boxes stay blank.
- Answers: letter for MCQ, expression for fill-in, key steps for derivations.

---

## Math macros (selection)

These are defined in both templates. Use them consistently.

| Macro | Output |
|-------|--------|
| `\params` | `θ` — model parameters |
| `\loss` | `ℒ` — loss function |
| `\dataset` | `𝒟` — dataset |
| `\KL{q}{p}` | `D_KL(q ‖ p)` |
| `\E`, `\Prob`, `\Var`, `\Cov` | Standard probability operators |
| `\norm{x}`, `\abs{x}`, `\inner{x}{y}` | Norm, absolute value, inner product |
| `\T`, `\inv`, `\tr`, `\rank`, `\diag` | Linear algebra shorthands |
| `\pd{f}{x}` | Partial derivative |
| `\Normal`, `\Bernoulli`, … | Common distributions |

Full list is in `templates/summary_template.tex`.

---

## Figures

- Store all figures in `figures/` inside the course folder.
- Reference as `figures/my-figure.png` (relative path from the `.tex` file).
- Use descriptive filenames: `bellman-backup.png`, not `fig1.png`.
- Prefer PNG for diagrams, JPEG for photos.

---

## Compiling

```bash
# Inside the course folder:
latexmk -pdf summary.tex
latexmk -pdf exams.tex
latexmk -C            # remove build artifacts
```

Commit both the `.tex` source and the compiled `.pdf`.
