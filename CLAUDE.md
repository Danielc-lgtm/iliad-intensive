# CLAUDE.md

Master reference for Claude Code sessions working in this repository.

## Overview

- This repo contains teaching materials for the Iliad Intensive fellowship program on AI safety, agent foundations, and related mathematical topics.
- Modules: `agent foundations/`, `decision theory/` (more may be added later).
- Each module has four folders:
  - `sources/` -- read-only reference material (PDFs, docx)
  - `projects/` -- LaTeX source files in Overleaf-compatible format
  - `edits/` -- edit interface (markdown mirror, instructions, choices)
  - `targets/` -- compiled PDF output

Folder names contain spaces (e.g. `agent foundations/`, `decision theory/`). Quote paths in shell commands.

## Content style guidelines

- Concise, technically precise bullet points; no LLM-style prose, no em dashes, no filler.
- Use parenthetical brackets (not em dashes) for inline remarks.
- Accessibility over formalism: avoid jargon like "first-order system," "Peano arithmetic," "Gödel numbering" unless carefully explained; ground formal concepts in computational analogies before symbolic treatment.
- Intuition before derivation: build intuitive understanding before formal notation.
- Stay grounded in sources: all claims traceable to specific source posts/papers, not loose paraphrases.
- Beamer slides use `{\tiny ...}` font size inside `\begin{block}{Title}` environments, matching the existing template in `header.tex`.
- When creating exercise sheets: hints should guide without revealing; progressive hint sequences should increase in specificity, but the last hint should not give away the answer.
- Careful about conceptual distinctions (e.g. $\Box P$ as a statement within $L$ vs $L \vdash P$ as a metalinguistic fact).

## Self-critique after each update (harshest-critic pass)

After completing any content change (slides, lecture notes, exercises), run a harshest,
most nit-picking critic pass, then improve the work along these dimensions:

- **No LLM prose.** The result must be indistinguishable from strong human academic
  writing, or from a rigorous expository LessWrong/Arbital post (match the register to
  the purpose). Calibrate against the best: pull up exemplary expository writing on the
  topic (e.g. Arbital / LessWrong articles; for slides, the best existing slide decks on
  the topic) and check the output for any tell of LLM writing -- hedging, filler
  transitions ("crucially", "notably", "it is worth noting"), inflated topic sentences,
  em-dash padding, vacuous summaries -- then remove them.
- **Self-containedness.** Assume zero prior knowledge of agent foundations. Every term
  and step must be introduced, or recoverable from the slide/note itself.
- **Conceptual rigour and holes.** State the precise goal of the slide/section, then test
  every argument and example against it: is each one sound, clearly phrased, and well
  justified, and does it efficiently and validly serve that goal? Fix or cut anything
  unsound, unclear, unjustified, or off-target.
- **Reverse-engineer the author's goal** for the change and judge the work by whether it
  achieves that goal.

Apply the resulting fixes before committing.

## The three edit interfaces

Each module's `edits/` folder contains three interfaces the author uses to drive changes:

### 1. Markdown mirror (`<project-name>.md`)

A structured markdown view of the LaTeX project (sections, slides, blocks, bullets, image placeholders). The author may add inline edit markers using `<div>description of change</div>` after any line (HTML `<div>` blocks are the edit marker syntax in this repo). When processing:

- Infer the intended LaTeX change from the marker and surrounding context (these are often low-context; reverse-engineer intent).
- Apply the change to the corresponding location in the LaTeX project.
- Compile the project to PDF in `targets/`.
- Regenerate the markdown mirror from the updated LaTeX (remove processed `<div>` markers).

### 2. Instructions file (`instructions.md`)

Bullet-point instructions below the separator line. Often low-context; infer what's meant from project context and sources. When processing:

- Read relevant source materials if needed to understand the instruction.
- Apply changes to LaTeX.
- Compile to PDF.
- Update the markdown mirror.
- Delete processed instructions.

### 3. Choices file (`choices.md`)

Claude Code writes here whenever facing a design decision, content ambiguity, or uncertainty about what the author wants. Use numbered IDs (`## Choice #N: ...`). Present your best guess for what to implement, note alternatives. When the author responds with a decision (inline or via instructions.md), implement it and mark resolved.

## Workflow for any edit session

1. `git pull` to get latest changes.
2. Check all modules' `edits/instructions.md` for new instructions.
3. Check all markdown mirror files for `<div>...</div>` edit markers.
4. Check all `edits/choices.md` for answered choices (look for filled-in `**Decision:**` fields).
5. For each change:
   1. Read relevant sources if needed for context.
   2. Apply changes to the LaTeX in `projects/`.
   3. Compile: `cd "projects/<project>" && latexmk -pdf main.tex`.
   4. Copy PDF to `targets/<project-name>.pdf`.
   5. Regenerate the markdown mirror from the updated LaTeX.
   6. Remove processed instructions/markers/resolved choices.
   7. Write any new uncertainties to `choices.md`.
6. `git add -A && git commit -m "[module] descriptive message"`.
7. `git push`.

## Reading sources

- Before making substantive content changes, read relevant files in `sources/`.
- Read PDFs with `pdftotext` or `python` with `PyPDF2`/`pdfplumber`.
- Read docx with `pandoc -t plain` or `python-docx`.
- For agent foundations: key context includes the Agent foundations reading guide (docx), pre-reading instructions (docx), exercise sheet PDF, and existing slides PDF.
- For decision theory: read the decision theory docx and PDF in `sources/`.

## Creating new LaTeX projects (core capability)

Claude Code should be able to create complete LaTeX projects from scratch when asked. This includes writing entire slide decks, exercise sheets, reading guides, or any other document type. The author may request this via `instructions.md`, the markdown mirror, or directly in conversation.

Procedure for creating a new project:

1. Create a new folder under the appropriate module's `projects/` directory (e.g. `decision theory/projects/dt-exercises/`).
2. Write the LaTeX source files:
   - **Beamer presentations:** copy `header.tex` and `logotips/` from `agent foundations/projects/Agency_presentation/`, create `main.tex` following the same `\begin{block}{}{\tiny \begin{itemize}...` structure.
   - **Exercise sheets:** use standard LaTeX article class (not Beamer); follow the style of the existing exercise sheet in `agent foundations/sources/Agency_exercise_V2.pdf` (exercises broken into subparts with progressive lemmas, self-contained notation sections, remarks connecting to broader context).
   - **Other documents** (reading guides, refresher documents, handouts, etc.): use article class with appropriate formatting.
3. Read relevant source materials in `sources/` to inform the content.
4. Compile the project (using the iterative compilation procedure below).
5. Copy the PDF to `targets/`.
6. Generate a corresponding markdown mirror in `edits/`.

The author may also create or edit LaTeX files directly in `projects/` and ask Claude Code to compile, fix errors, and generate/update the mirror.

## LaTeX compilation (self-healing)

- Use `latexmk -pdf` for compilation.
- If texlive is not installed at all, start with:
  ```
  sudo apt-get update && sudo apt-get install -y texlive-latex-base texlive-latex-recommended latexmk apt-file && sudo apt-file update
  ```
- If compilation fails with a missing package/font error:
  1. Parse the log to identify the missing `.sty`, `.cls`, or font file.
  2. Find the right package: `apt-file search <missing-file>` (install `apt-file` first if not present).
  3. Install it: `sudo apt-get install -y <package-name>`.
  4. Retry compilation.
- Repeat the install-and-retry loop until compilation succeeds with zero errors; do not ask the author to install packages manually.
- If the error is a LaTeX syntax/content error (not a missing package), fix the LaTeX and retry.
- Never commit LaTeX that does not compile cleanly.

Known mappings observed in this repo:
- `pgfmath.sty` → `texlive-pictures`
- Beamer base → `texlive-latex-recommended`
- `amssymb`, `amsmath` → `texlive-base` (already in `texlive-latex-base`)

## Git operations

- Always pull before starting work.
- Commit after each logical edit cycle with a descriptive message.
- Always push after committing.
- Commit message format: `[module] brief description`, e.g. `[agent-foundations] Add finite descent slide to Löbian obstacle section`.
