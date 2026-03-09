# AI Master — Lecture Summaries

Structured LaTeX summaries for every lecture in the AI Master programme,
built from slides, notes, and the lectures themselves.
The goal is a single, comprehensive document per course that makes exam
preparation efficient and systematic.

---

## Repository structure

```
AI_Master/
├── template.tex                          # Shared LaTeX template (copy, never edit in-place)
│
├── AI in Life Sciences/
├── Deep Reinforcement Leaning/
├── DL Architectures & Generative Techniques/
├── Genome Analysis & Transcriptomics/
├── ML Unsupervised Techniques/
├── Robopsychology/
└── Structural Bioinformatics/
```

Each course folder will contain:

| File | Purpose |
|------|---------|
| `summary.tex` | Main summary document (copied from `template.tex`) |
| `summary.pdf` | Compiled output — tracked for easy sharing |
| `img/` | Figures extracted from slides or drawn in TikZ |
| `slides/` | Original slide PDFs (gitignored if large) |

---

## Workflow for a new lecture

1. **Copy the template** into the course folder and rename it:
   ```bash
   cp template.tex "ML Supervised Techniques/summary.tex"
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

---

## Template overview

`template.tex` is a self-contained `book`-class document designed around
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

Full macro list is in `template.tex` under the *Mathematical Macros* section.

---

## Compiling

**Recommended:** `latexmk` handles multiple passes automatically.

```bash
# Inside the course folder:
latexmk -pdf summary.tex       # compile
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
