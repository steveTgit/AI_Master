# CLAUDE.md — AI Master Notes Repository

Instructions for Claude when working in this repo.

---

## Project overview

LaTeX exam-prep repository for the AI Master programme. Each course folder
contains two documents:

| File | Class | Template |
|------|-------|----------|
| `summary.tex` | `book` | `template.tex` |
| `old_exams.tex` | `article` | `old_exams_template.tex` |

---

## summary.tex conventions

- **Structure:** `\chapter` per major topic, `\section` / `\subsection` within.
- **Accent color:** `#1B3A5C` (deep navy) — never change this.
- **Philosophy:** running prose is the default; boxes are landmarks, not
  the primary content carrier. When in doubt, write prose.

### Box types (summary.tex)

| Box | Color | Use for |
|-----|-------|---------|
| `\begin{defbox}[title={…}]` | Blue (#1A5276) | Formal definitions |
| `\begin{thmbox}[title={…}]` | Red (#922B21) | Key theorems, important formulas |
| `\begin{exbox}[title={…}]` | Green (#1E8449) | Worked examples |
| `\begin{intbox}` | Amber (#9A6A00) | Intuition, mental models |
| `\begin{notebox}[title={…}]` | Purple (#5B2C6F) | Exam traps, caveats |

Do NOT add boxes without a clear reason. Every unnecessary box dilutes
the signalling value of all boxes.

---

## old_exams.tex conventions

- **Structure:** `\section` per thematic topic (no chapters — article class).
  Sections should map to the chapter breakdown of the corresponding `summary.tex`.
- **Questions are NOT numbered manually** — `\questiontitle` auto-increments
  a counter.
- **Exact duplicates are removed.** When the same question appeared on
  multiple exams, keep one instance and add `\repeatnote` at the top.
- **Mathematical content is kept verbatim.** Only normalize wording where
  scans were messy; never change answer choices or numbers.

### Box types (old_exams.tex)

| Macro / Box | Color | Use for |
|-------------|-------|---------|
| `\questiontitle{Title}` … `\closequestion` | Blue (#1A5276) | Every exam question |
| `\begin{keybox}[title={…}]` | Green (#1E8449) | Key insight or answer hint |
| `\begin{notebox}[title={…}]` | Amber (#9A6A00) | Organizational notes only |

### Structural macros

| Macro | Effect |
|-------|--------|
| `\questiontitle{Short title}` | Opens a numbered blue question box |
| `\closequestion` | Closes the question box |
| `\repeatnote` | Prints italic "Asked multiple times." |
| `\choice` | `☐` bullet item for multiple-choice |
| `\answerline{3cm}` | Fill-in underline of specified width |

### Math macros included in old_exams.tex

`\R`, `\E`, `\Prob`, `\KL{q}{p}`, `\dd` — add from `template.tex` as needed.

---

## Shared design rules (both files)

- Same `accent` color: `#1B3A5C`.
- Same `tcbset` global box style: `arc=2.5mm`, `boxrule=0.5pt`, thick left
  accent bar (`borderline west={3.5pt}{0pt}{…}`), `sharp corners=west`,
  `parbox=false`, `breakable`.
- Same typography: `lmodern`, `microtype`, `inconsolata`, `\parindent=0pt`,
  `\parskip≈0.6em`.
- Same title page structure: thick accent rule → large bold title → thin
  accent rule → author → date.

---

## Compiling

```bash
latexmk -pdf summary.tex
latexmk -pdf old_exams.tex
latexmk -C          # clean build artifacts
```

Always commit both `.tex` and `.pdf`.

---

## What NOT to do

- Do not edit `template.tex` or `old_exams_template.tex` in-place — copy first.
- Do not add `\answers` or solution content to `old_exams.tex` — it is
  intentionally a practice set without solutions.
- Do not change accent colors or box color definitions per-document.
- Do not add a chapter level to `old_exams.tex` — it is article class.
