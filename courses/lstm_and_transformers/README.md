# LSTM & Transformers

Covers recurrent networks, BPTT, LSTM, attention, Transformers, linear attention, Mamba, xLSTM, TiRex, attractor networks, and hidden Markov models.

**Status:** draft — chapters 0–6 and 9–10 developed: notation, RNNs, learning algorithms, LSTM, attention, Transformers, linear attention, TiRex, and attractor networks.
**Missing:** chapters 7, 8, and 11 remain an outline; fourteen figure placeholders across chapters 1–6 and 9–10 still need illustrations. No past-exam material has been supplied.

## Files

- `summary.tex`: working summary based on `templates/summary_template.tex`.
- `summary.pdf`: compiled working summary.
- `figures/`: destination for figures added during elaboration.
- `Script_small.pdf`: local source, not tracked; Hochreiter & Adler, *LSTM & Transformers*, Winter Semester 2026.

## Blueprint and authoring plan

The summary preserves source chapter numbering: 0 (Notation), followed by chapters 1–11. Sections and subsections follow the script; the short linear-attention chapter receives two working sections. Source references are kept in TeX comments for editing and use printed page numbers, not PDF viewer page indices. They are not printed at chapter starts. Deeper source headings use paragraph headings to keep the contents readable.

The document is in English, following the repository templates. Write relaxed, informal study notes for students: understanding comes first. Explain an idea in plain words before introducing its equation, use concrete examples, and make the notes usable without opening the original script. Avoid textbook-like formality, unnecessary historical detail, and repeated source-navigation instructions. Replace the visible planning text as each section is developed. Introduce motivation and notation in prose, then add only useful definition, formula, example, intuition, or caveat boxes. Keep all template colors, typography, margins, and heading styles. Save figures under descriptive names in `figures/`.

Recommended elaboration order: notation and RNNs → learning algorithms → LSTM → attention and Transformers → linear attention, Mamba, xLSTM, TiRex → attractor networks and HMMs. Check equations and source coverage before marking a chapter complete.

The existing folder name `lstm_and_transformers` is retained as requested, although new repository slugs normally use kebab-case.

## Compile

```bash
cd courses/lstm_and_transformers
latexmk -pdf summary.tex
```

## How to help

- Develop the planned sections against the supplied lecture script.
- Add clear derivations, examples, and figures.
- Fix errors and recompile the PDF after editing the TeX source.

## Length budget and current progress

Target: no more than about **120 PDF pages**, including front matter and figures. Working allocation: front matter 5; notation 3; RNNs 5; learning algorithms 8; LSTM 17; attention 8; Transformers 23; linear attention 4; Mamba 6; xLSTM 15; TiRex 5; attractor networks 5; HMMs 11. This totals 115 pages, with 5 pages of reserve. These are editorial targets, not limits that justify omitting core concepts.

Chapters 0–6 and 9–10 contain explanations, shape conventions, worked numerical examples, and selected intuition/caveat boxes. BPTT covers output and hidden deltas, shared-weight gradients, biases, initial state, and mini-batches. Alternatives include truncated BPTT, RTRL, and the block hybrid; gradient stability connects to focused backpropagation and LSTM.

Figure briefs are embedded in `summary.tex`: feedback architecture comparison, unrolled BPTT, gradient magnitude over temporal distance, LSTM cell, encoder-decoder bridge, attention alignment, query-key-value retrieval, Transformer encoder-decoder flow, causal/local masks, MHA/GQA/MQA cache sharing, outer-product memory, the TiRex forecast pipeline, attractor basins, and Boltzmann/RBM/DBM connectivity. Replace these panels in place so their space remains included in the page budget.

Editorial corrections are explicit where needed: matrix orientation and same-shape optimizer gradients; the lecture-specific Elman definition; softmax's coupled Jacobian; Gaussian-prior penalty sign and normalization; RTRL per-step versus total complexity; ordered Jacobian products and sufficient norm bounds. The block-hybrid complexity is consistently reported per step and per sequence rather than mixing units. All BPTT weight and bias gradients were checked against central finite differences on a small dense tanh RNN with masked time-step losses.

## Current compiled scope

The developed chapters occupy 64 numbered pages: notation 3, RNNs 4, learning algorithms 8, LSTM 12, attention 6, Transformer 13, linear attention 5, TiRex 6, and attractor networks 7. The complete working PDF is 76 pages including 5 pages of front matter and 7 pages of unfinished outlines. Chapters 7, 8, and 11 retain a combined working allocation of 32 pages, giving a projected total around 101 pages with the current developed material and leaving room for figures and revision below the 120-page target.

Chapter 3 explains cell versus hidden state, the basic and forget-gate LSTM, backpropagation, practical choices, dropout/zoneout, applications, variants, and the exact reset-before GRU used in the equations. Chapter 4 develops scoring/normalization/retrieval, additive and multiplicative attention, local attention, recurrent self-attention, masking, sentence pooling, and key-value retrieval. Four new figure panels reserve space for future diagrams.

Validation: the basic LSTM, forget-gate LSTM, minimal reset-before GRU, and softmax-attention score derivatives agree with central finite differences (maximum absolute errors below 1e-8 in small numerical checks). The worked cell and attention calculations were checked separately. The short NTM, DNC, and pointer-network introductions fill otherwise empty source headings; optional original-paper links are included as footnotes, not prerequisites for reading.

Chapter 5 follows a self-contained path from token embeddings through shape-checked scaled dot-product attention, masking, multiple heads, cross-attention, positions/RoPE, FFNs/SwiGLU, residuals and normalization, training, sampling, and KV caching. It covers original BERT and all ten architecture headings with emphasis on differences rather than product rankings. Chapter 6 derives outer-product retrieval, normalized feature-kernel attention, gated retention, delta updates, diagonal-plus-low-rank transitions, affine prefix scans, and a compact comparison of the related model families.

Additional editorial clarifications: permutation equivariance versus fixed-query invariance; vocabulary versus attention softmax; pre/post/branch-output normalization; total versus active MoE parameters; V3's initial dense layers; SmolLM3's partial NoPE; variant-specific multimodality; gpt-oss's extra normalization logit; full-sequence versus causal kernel aggregation; constant inference state versus training memory; and the cost/closure requirements behind associative scans. Selected model details were checked against original technical reports and model cards, with short optional links at the relevant explanation. No source-navigation banners appear at chapter starts.

Chapter 5–6 validation: 21 numerical checks of worked attention and masking examples, causal full versus cached attention, permutation equivariance, the RoPE relative-position identity, KV bytes, explicit versus recurrent normalized kernel attention, gated prefix weights, delta-rule forms and interpolation, and affine composition. Maximum absolute discrepancy was 1.8e-15. The PDF was compiled with latexmk and the new chapter pages visually reviewed; figure placeholders remain intentional.

Chapters 9–10 add a self-contained forecasting walkthrough and an energy-based memory walkthrough. TiRex covers context versus parameter adaptation, patching and masking, a compact sLSTM recap, computational assumptions, MASE and quantile scores, interval interpretation, realistic evaluation, and variant-specific covariates. Attractor networks cover implicit equilibrium differentiation with an adjoint solve, its convergence conditions, Hopfield storage and asynchronous energy descent, synchronous cycles, Boltzmann conditionals and temperature, likelihood learning with threshold-consistent signs, RBMs, and DBMs. Three new figure panels reserve space for the forecasting pipeline, memory basins, and network connectivity.

Chapter 9–10 validation: 35 numerical checks, including all 16 weight gradients in a small nonlinear equilibrium network, exact Boltzmann and RBM likelihood gradients against central finite differences, Gibbs conditionals by enumeration, 160 single-unit Hopfield updates, and the worked memory/forecast examples. Maximum absolute discrepancy was 3.6e-10. The PDF compiles without warnings; chapter pages were rendered and visually checked, with short boxes kept together and the applications section starting on its own page.

Key corrections in these chapters: zero-shot forecasts still use history and pretraining; fixed temporal state is not total constant memory; attention models are not categorically unable to track dynamics; a MASE value below one compares with an in-sample naive scale; quantile intervals describe marginal predictive uncertainty; driven input units are not clamped; continuous-time stability and Neumann-series convergence are distinct; Hopfield recall need not return the nearest stored pattern; positive-temperature Boltzmann sampling approaches a distribution rather than a guaranteed global-minimum state. The original empty RBM/DBM headings now contain compact explanations and optional primary-source links.
