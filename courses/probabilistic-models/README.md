# Probabilistic Models

Covers probabilistic graphical models (directed only): fundamentals of probability, Bayesian networks (representation, exact and approximate inference, MCMC), learning Bayesian networks (ML and Bayesian parameter learning, structure learning), dynamic Bayesian networks, hidden Markov models, and the Kalman filter. Based on the JKU lecture by G. Widmer, WS 2026/27.

**Status:** draft — chapters 1–3 written (Introduction, Fundamentals of Probability, Bayesian Networks: Representation & Semantics)
**Missing:** chapters 4–8 are outlines only (BN inference, learning, DBNs, HMMs, Kalman filter); figure placeholders for the ALARM network (ch. 3) and score following (ch. 7); no exam collection yet

## Files

| File | Description |
|------|-------------|
| `summary.pdf` | Working summary (chapters 1–3 written, 4–8 outlined) |
| `summary.tex` | LaTeX source |
| `figures/` | Images for figure placeholders (most figures are drawn inline with TikZ/pgfplots) |
| `slides/` | Lecture slide PDFs (not tracked by git) |

## Notes for editing

- Chapters follow the lecture units: VO 1 → ch. 1, VO 1–2 → ch. 2, VO 3 → ch. 3, VO 4–5 → ch. 4, VO 6–8 → ch. 5, VO 9 → ch. 6, VO 10–11 → ch. 7, Kalman video → ch. 8.
- Unwritten sections contain `\planned{...}` notes; replace them once the corresponding slides are available.
- `\figureplaceholder{height}{concept}{brief + search hint}{caption}{label}` marks figures that should come from an external image; drop the image into `figures/` and replace the placeholder with `\includegraphics`.
- Notation follows the lecture (Koller & Friedman style): `\Xall` for all variables, bold `\bX`, `\bE` for sets, superscript values `x^0, x^1` with `x^0 = false`, `\Pa`, `\NonDesc`, `\indep`.
- All worked numbers in chapters 2–3 (student network queries, local independencies, parameter counts) were re-computed by script.

## How to help

Contributions are welcome even when there is no specific task listed. Good places to help:
- Update the notes if lecture material changes.
- Fix errors, typos, broken formulas, or unclear explanations.
- Add examples, derivations, figures, or exam questions where they make a topic easier to study.
- Recompile and commit the PDF after changing a `.tex` file, if you can.

Open an issue if you are unsure; open a pull request directly for small fixes.
