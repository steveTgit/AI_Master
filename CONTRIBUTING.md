# Contributing

Thanks for wanting to help improve these notes. Every fix matters — even a single corrected formula helps the next person who reads it.

---

## Fix a typo in the browser (no git required)

1. Find the file you want to fix (e.g. `courses/reinforcement-learning/summary.tex`).
2. Click the **pencil icon** (Edit this file) in the top-right of the file view on GitHub.
3. Make your change.
4. Scroll down, write a short description (e.g. "Fix typo in Bellman equation"), and click **Propose changes**.
5. Click **Create pull request**.

That's it. No fork, no clone, no terminal needed.

---

## Larger changes (fork + branch + PR)

For adding sections, restructuring content, or contributing a new course:

```bash
# 1. Fork the repo on GitHub, then clone your fork
git clone https://github.com/<your-username>/AI_Master.git
cd AI_Master

# 2. Create a feature branch
git checkout -b fix/rl-td-lambda-derivation

# 3. Make your changes
# ... edit files, compile PDFs ...

# 4. Commit and push
git add courses/reinforcement-learning/summary.tex courses/reinforcement-learning/summary.pdf
git commit -m "Fix TD(λ) derivation in RL summary"
git push origin fix/rl-td-lambda-derivation

# 5. Open a pull request on GitHub
```

---

## Adding a new course

1. Copy the appropriate template:
   ```bash
   cp templates/summary_template.tex courses/<course-slug>/summary.tex
   cp templates/exams_template.tex courses/<course-slug>/exams.tex
   ```

2. Name the course folder using **lowercase kebab-case**: `ml-supervised-techniques`, `computer-vision`, etc.

3. Set `\coursetitle` near the top of each `.tex` file. Set `\basedon` in
   `summary.tex` when the summary template provides it.

4. Add a `README.md` inside the course folder using the template below.

5. Compile and commit both `.tex` and `.pdf`:
   ```bash
   cd courses/<course-slug>
   latexmk -pdf summary.tex
   latexmk -pdf exams.tex
   git add summary.tex summary.pdf exams.tex exams.pdf figures/
   ```

### Course README template

```markdown
# <Course Title>

Short description of what the course covers.

**Status:** draft / usable / reviewed
**Missing:** [list what is not yet written]

## How to help
Contributions are welcome even when there is no specific task listed. Good places to help:
- Update the notes if lecture material changes.
- Fix errors, typos, broken formulas, or unclear explanations.
- Add examples, derivations, figures, or exam questions where they make a topic easier to study.
- Recompile and commit the PDF after changing a `.tex` file, if you can.

Open an issue if you are unsure; open a pull request directly for small fixes.
```

---

## Folder structure for a course

```
courses/<course-slug>/
├── README.md
├── summary.tex            ← compiled from summary_template.tex
├── summary.pdf            ← commit this too
├── exams.tex              ← compiled from exams_template.tex (when past exams exist)
├── exams.pdf              ← commit this too
├── exams_solutions.tex    ← optional: same questions with inline worked solutions
├── exams_solutions.pdf    ← commit this too if you add the .tex
├── figures/               ← images used in either .tex file
└── slides/                ← lecture PDFs and other local material (NOT tracked)
```

`.gitignore` whitelists course folders: only `README.md`, `summary`, `exams`,
`exams_solutions`, and `figures/` are tracked. Anything else you drop in a
course folder — slides, raw exam scans, notebooks, scratch files — stays local
automatically, so you can keep source material next to the document without
committing it. To publish a genuinely new document type, add an explicit `!`
rule to the courses block in `.gitignore`.

---

## Naming conventions

- **Course folders:** lowercase kebab-case (`reinforcement-learning`, not `Reinforcement Learning`).
- **Figure files:** descriptive lowercase names (`bellman-backup.png`, not `img1.png`).
- **Branch names:** `fix/<short-description>` for fixes, `add/<course-slug>` for new courses.

---

## PDFs

Please compile and commit updated PDFs when you change `.tex` files. Others may not have LaTeX installed. If you cannot compile (e.g. missing packages), submit the PR anyway and note it — the maintainer can compile.

---

## Style

See [docs/style-guide.md](docs/style-guide.md) for LaTeX formatting rules (box types, accent colors, section structure, etc.).
