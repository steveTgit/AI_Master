# AI Master — Lecture Summaries

Structured LaTeX summaries for every lecture in the AI Master programme,
built from slides, notes, and the lectures themselves.
Each course produces two documents: a comprehensive summary and a curated
collection of old exam questions.

---

## Repository structure

```
AI_Master/
├── summary_template.tex                          # Shared LaTeX template (copy, never edit in-place)
├── old_exams_template.tex                # Shared old-exams template (copy, never edit in-place)
├── CLAUDE.md                             # Instructions for Claude Code
│
└── <Course Name>/                        # One folder per course (add as needed)
    ├── summary.tex / summary.pdf
    ├── old_exams.tex / old_exams.pdf
    ├── img/
    └── slides/                           # gitignored — put large slide PDFs here
```

Each course folder will contain:

| File | Purpose |
|------|---------|
| `summary.tex` | Main summary document (copied from `summary_template.tex`) |
| `summary.pdf` | Compiled output — tracked for easy sharing |
| `old_exams.tex` | Curated old exam questions (copied from `old_exams_template.tex`) |
| `old_exams.pdf` | Compiled output — tracked for easy sharing |
| `img/` | Figures extracted from slides or drawn in TikZ |
| `slides/` | Original slide PDFs (gitignored if large) |

---

## Workflow for a new course

### 1. Main summary

1. **Copy the template** into the course folder and rename it:
   ```bash
   cp summary_template.tex "ML Supervised Techniques/summary.tex"
   ```

2. **Fill in the metadata** near the top of the file:
   ```latex
   \newcommand{\coursetitle}{ML Supervised Techniques}
   \newcommand{\basedon}{Based on Lecture \emph{ML Supervised Techniques} SS26}
   ```

3. **Write the content** — one `\chapter{}` per major topic, sections and
   subsections following the lecture structure.

4. **Compile** with `pdflatex` (run twice for cross-references) or use
   `latexmk`:
   ```bash
   latexmk -pdf summary.tex
   ```

5. **Commit** the `.tex` source and the compiled `.pdf`.

### 2. Old exam questions

1. **Copy the old-exams template** into the course folder:
   ```bash
   cp old_exams_template.tex "ML Supervised Techniques/old_exams.tex"
   ```

2. **Update the title** near the top of the document body:
   ```latex
   {\fontsize{26}{32}\selectfont\bfseries\color{accent}Old Exam Questions\\[2pt] ML Supervised Techniques\par}
   ```

3. **Organize questions by topic** — one `\section{}` per thematic area,
   questions inside `\questiontitle{…}` / `\closequestion` blocks.

4. **Mark repeated questions** with `\repeatnote` at the start of the box.

5. **Compile and commit** the same way as the main summary.

---

## Template overview

### `summary.tex` (`summary_template.tex`)

`summary_template.tex` is a self-contained `book`-class document designed around
these principles:

- **Readable running text is the default.** Explanations, derivations, and
  logical connections live in prose. Colored boxes are visual landmarks, not
  the primary content carrier.
- **Boxes are used sparingly.** Every colored box type has a specific purpose;
  overuse dilutes their signalling value.
- **A single accent color** (`#1B3A5C`, deep navy) ties all structural
  elements together.

### Box types

| Box | Color | When to use |
|-----|-------|-------------|
| `\begin{defbox}[title={…}]` | Blue | Formal definitions |
| `\begin{thmbox}[title={…}]` | Red | Key theorems, important formulas |
| `\begin{exbox}[title={…}]` | Green | Worked examples |
| `\begin{intbox}` | Amber | Intuition, mental models, "why this works" |
| `\begin{notebox}[title={…}]` | Purple | Exam traps, caveats, things to double-check |

### Math macros (selection)

| Macro | Output |
|-------|--------|
| `\params` | `θ` (bold) — model parameters |
| `\loss` | `ℒ` — loss function |
| `\dataset` | `𝒟` — dataset |
| `\KL{q}{p}` | `D_KL(q ‖ p)` |
| `\E`, `\Prob`, `\Var`, `\Cov` | Standard probability operators |
| `\norm{x}`, `\abs{x}`, `\inner{x}{y}` | Norm, absolute value, inner product |
| `\T`, `\inv`, `\tr`, `\rank`, `\diag` | Linear algebra shorthands |
| `\dd` | Upright differential `d` for integrals |
| `\pd{f}{x}`, `\pdd{f}{x}` | Partial derivatives |
| `\bigO{n}`, `\bigOm{n}`, `\bigTh{n}` | Complexity notation |
| `\Normal`, `\Bernoulli`, `\Dirichlet`, … | Common distributions |

Full macro list is in `summary_template.tex` under the *Mathematical Macros* section.

### `old_exams.tex` (`old_exams_template.tex`)

`old_exams_template.tex` is a self-contained `article`-class document (no
chapters — just sections and questions). It shares the same accent color and
visual language as `summary.tex` but is purpose-built for a question–answer
collection.

**Box types:**

| Box | Color | When to use |
|-----|-------|-------------|
| `\questiontitle{Title}` … `\closequestion` | Blue | Every exam question |
| `\begin{keybox}[title={…}]` | Green | Key insight or model answer hint |
| `\begin{notebox}[title={…}]` | Amber | Organizational notes (e.g. "how this file is organized") |

**Structural macros:**

| Macro | Purpose |
|-------|---------|
| `\questiontitle{Title}` | Opens a numbered question box |
| `\closequestion` | Closes the question box |
| `\repeatnote` | Italic note: "Asked multiple times." — place at top of box |
| `\choice` | `☐` bullet for multiple-choice options |
| `\answerline{3cm}` | Blank fill-in line of the given width |

**Organization:** one `\section{}` per thematic topic area (matching the
main summary's chapter breakdown where possible), questions within each
section in chronological order (newest exam first if known).

**Math macros:** `old_exams.tex` includes the minimal subset needed for
exam-style questions — `\R`, `\E`, `\Prob`, `\KL`, `\dd`. Add from the
full template macro list as needed.

---

## Compiling

**Recommended:** `latexmk` handles multiple passes automatically.

```bash
# Inside the course folder:
latexmk -pdf summary.tex       # compile main summary
latexmk -pdf old_exams.tex     # compile old exam questions
latexmk -pdf -pvc summary.tex  # compile + watch for changes
latexmk -C                     # clean all build artifacts
```

**Manual (two-pass):**
```bash
pdflatex summary.tex
pdflatex summary.tex
```

Required packages (all available in TeX Live / MiKTeX):
`geometry`, `fontenc`, `inputenc`, `lmodern`, `microtype`, `inconsolata`,
`amsmath`, `amssymb`, `amsthm`, `mathtools`, `bm`, `bbm`, `mathrsfs`,
`nicefrac`, `cancel`, `graphicx`, `booktabs`, `array`, `float`, `enumitem`,
`algorithm2e`, `xcolor`, `listings`, `tcolorbox`, `tocloft`, `titlesec`,
`fancyhdr`, `hyperref`, `cleveref`.

---

## Author

Stefan Eder
