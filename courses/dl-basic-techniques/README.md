# Deep Learning: Basic Techniques

Covers the basic techniques of deep learning: the history of neural networks, single-layer networks (linear neuron, perceptron, logistic and softmax regression), why they fail on XOR, multi-layer perceptrons and deep feed-forward networks, backpropagation, the vanishing gradient problem, Jacobian and Hessian, practical training tricks, and Amari–Hopfield networks. Later chapters: generalization and cross-validation, CNNs, learning algorithms, regularization, initialization, normalization. Based on the JKU lecture by G. Klambauer (slides of WS 2025/26).

**Status:** draft — chapters 1, 3 and 4 written (History, Notation, Basic Neural Network Architectures 4.1–4.10 plus the Hopfield excursion)
**Missing:** chapter 2 (Biological Neural Networks) and chapters 5–10 are outlines only; no exam collection yet

## Files

| File | Description |
|------|-------------|
| `summary.pdf` | Working summary (chapters 1, 3–4 written; 2 and 5–10 outlined) |
| `summary.tex` | LaTeX source |

All figures are drawn inline with TikZ/pgfplots, so there is no `figures/` folder yet. Lecture slides and other source material in this folder are not tracked by git.

## Notes for editing

- Chapters follow the course overview from the first lecture (1 History, 2 Biological NNs, 3 Notation, 4 Basic architectures, 5 Generalization, 6 CNNs, 7 Learning methods, 8 Regularization, 9 Initialization, 10 Normalization). Section numbers 4.1–4.10 match the slides; the Hopfield excursion is 4.11.
- Chapter 3 collects the notation as used on the Chapter 4 slides (the lecture's own notation slides were not available); check it against them once they are.
- Unwritten sections contain `\planned{...}` notes; replace them once the corresponding slides are available.
- Notation follows the slides: bold italic vectors (`\bx`, `\bw`, `\bW`), sample index as superscript (`x^n`), layer index in brackets (`\bW\lay{l}`), `w_{ij}` from unit j to unit i. The loss is written `\loss` (calligraphic) to keep it apart from the number of layers `L`, which the slides also call `L`.
- Editorial corrections are made explicit in the text: the sign of the perceptron loss and the `sign(0)` convention, the sign of the logistic-regression Hessian, the shape of the outer product `\bdelta\lay{l}\ba\lay{l-1}\T`, and the ImageNet-record date.
- All worked numbers (least squares, perceptron run, logistic and softmax steps, XOR network, vanishing-gradient factors, Hopfield retrieval) were re-computed by script; the 2–2–1 backpropagation example was checked against central finite differences.

## How to help

Contributions are welcome even when there is no specific task listed. Good places to help:
- Update the notes if lecture material changes.
- Fix errors, typos, broken formulas, or unclear explanations.
- Add examples, derivations, figures, or exam questions where they make a topic easier to study.
- Recompile and commit the PDF after changing a `.tex` file, if you can.

Open an issue if you are unsure; open a pull request directly for small fixes.
