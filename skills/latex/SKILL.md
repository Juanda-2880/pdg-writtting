---
name: latex
description: Use when writing, editing, or reviewing .tex files for the IAsLab PDG thesis — chapters, the preamble, tables, figures, citations, or the build. Covers this project's specific toolchain (report class, Spanish/babel, natbib+apalike APA citations, cleveref, tikz/pgfplots) as well as general LaTeX semantic-markup best practices.
---

# Writing LaTeX for This Thesis

## Overview

This skill governs the mechanics of turning approved thesis content (see `thesis-writing/`) into compilable, well-formed LaTeX. It assumes the content decisions — what a chapter argues, what evidence backs a claim — are already settled by the `agent-roles/` workflow; this skill is about *how to express that in LaTeX correctly*, not what to say.

Origin note: the semantic-markup, cross-reference, and citation practices below are adapted from the MIT-licensed `dbosk/claude-skills` "latex-writing" skill, trimmed to this project's actual toolchain and rewritten for our APA/natbib setup. See `NOTICE.md` for the required attribution.

## This project's toolchain (decided, don't relitigate without the Coordinador)

- **Document class**: `report` (chapters + sections), `letterpaper`, `11pt` — matches the tutor's reference thesis project.
- **Engine**: `pdflatex`, driven by `latexmk` (see `Makefile`/`latexmkrc`) — not a manual `pdflatex` invocation, and not XeLaTeX/LuaLaTeX.
- **Language**: Spanish, via `babel[spanish]`.
- **Citations**: APA 7, via `natbib` (`authoryear,round`) + `\bibliographystyle{apalike}` — chosen to match `reference-writting/` and `writting-tools/normas-APA.md`, which already mandate APA 7. See `references/citations-and-figures.md`.
- **Cross-references**: `cleveref` (loaded after `hyperref`), Spanish names.
- **Build output**: everything generated goes to `compiled-output/` (repo root), per `CLAUDE.md` rule 2 — never into the LaTeX source tree.

The actual thesis document lives in [`../../thesis/`](../../thesis/README.md) (`main.tex` + `chapters/`, per `thesis-writing/structure.md`). It uses this module's `preamble.tex` directly via `\input{../skills/latex/preamble}` — edit the preamble here, not a copy, so the whole thesis stays on one source of truth. `Makefile`/`latexmkrc` are copied into `thesis/` once (boilerplate, low drift risk).

## Core principle: semantic markup

Use the LaTeX construct that matches what the content *is*, not just how it should look.

### Lists: `description` vs `itemize` vs `enumerate`

- **`description`** for term–definition / label–content pairs (e.g. FR-01, FR-02 style requirement listings, glossary-style entries). Never fake this with `itemize` + `\textbf{Label:}`.
- **`itemize`** for uniform items with no inherent order.
- **`enumerate`** when order/sequence matters (steps, PID control loop stages).
- A list with exactly **one** `\item` is not a list — write it as a prose sentence instead.
- Never open a semantic environment (`example`, `remark`, a custom thesis environment) directly with a list or code block — lead with at least one sentence first.

```latex
% BAD
\begin{itemize}
  \item \textbf{FR-01.1:} Model provisioning via repository identifier.
\end{itemize}

% GOOD
\begin{description}
  \item[FR-01.1] Model provisioning via repository identifier.
\end{description}
```

### Cross-references: always `\cref`/`\Cref`

Never hand-type `Figura~\ref{...}`, `Sección~\ref{...}`, `Capítulo~\ref{...}`. See `references/citations-and-figures.md` for the full pattern and label-naming convention.

### Citations: always a `\cite*` command

Never hand-type `(Autor, 2024)`. See `references/citations-and-figures.md` for `\citet`/`\citep`/`\citeyearpar` usage and how it maps to the APA rules in `reference-writting/`.

### Quotations: always `\enquote{...}`

Never manual `"..."` or `` ``...'' ``. Long (≥40-word) quotes go in a `quote`/`quotation` block, not a giant `\enquote{}`. See `references/citations-and-figures.md`.

### Emphasis

- `\emph{...}` for semantic emphasis, `\textbf{...}` for strong emphasis. **Never** ALL CAPS for emphasis in running prose (acronyms/proper nouns like `LSTM`, `IIRA`, `SAAMFI` are fine as-is).

### Floats: figures and tables

Always a proper `figure`/`table` environment with `\caption` + `\label` — an image is not a figure, a `tabular` is not a table. See `references/citations-and-figures.md` for the exact templates (booktabs rules, `longtable` for multi-page tables, self-contained captions).

### Code / verbatim

If a chapter needs to show a code snippet (e.g. a YAML benchmark spec from `project-context/technologies.md`), use `verbatim`/`framed`, or add `listings`/`minted` if syntax highlighting becomes genuinely necessary — don't paste code as plain paragraph text.

## Workflow

1. **Check what evidence/outline this section is drafting from** — this skill doesn't replace `thesis-writing/writing-guide.md`; it's the layer under it.
2. **Write the LaTeX using the semantic constructs above.**
3. **Compile before moving on**: `make build` from the actual project folder (see `Makefile`). Per `agent-roles/Revisor.md`, the Revisor is the one who runs this check as part of sign-off, but the Redactor should still do a sanity compile after any structurally risky edit (new package, new environment, a table/figure that might not fit).
4. **If the build fails**, check `references/troubleshooting.md` before guessing.
5. **New package or preamble change?** Add it to `preamble.tex` in the right section and document it in `references/packages.md` — see the rule at the bottom of that file about not doing this unilaterally.

## Supporting files

- `preamble.tex` — the shared preamble template (encoding, language, packages, citation/cross-reference setup).
- `Makefile` / `latexmkrc` — the build, routed to `compiled-output/`.
- `references/packages.md` — what every package is for.
- `references/citations-and-figures.md` — APA citations, quotations, cross-references, figure/table/equation templates.
- `references/troubleshooting.md` — diagnosing the build failures specific to this stack.
- `NOTICE.md` — third-party attribution (MIT) for the semantic-markup practices this skill builds on.
