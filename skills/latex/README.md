# LaTeX Module

This module provides the LaTeX-specific configuration, build tooling, and skill an AI agent needs to write and compile the IAsLab PDG thesis, without having to rediscover this project's conventions each time.

---

## Purpose

1. Give agents a ready-to-copy preamble, `Makefile`, and `latexmkrc` instead of improvising packages/build steps per session.
2. Fix the citation/bibliography stack (APA 7 via `natbib` + `apalike`) so it's consistent with [`reference-writting/`](../reference-writting/README.md) and [`writting-tools/normas-APA.md`](../writting-tools/normas-APA.md) — see [`SKILL.md`](./SKILL.md) for why this was chosen over the tutor's original `alphaabbr` style.
3. Encode the semantic-markup rules (proper `description`/`itemize`/`enumerate` use, `cleveref` cross-references, `csquotes` quotations, `booktabs`/`longtable` tables) that keep the generated LaTeX correct and maintainable rather than visually-hacked.
4. Route every compiled/generated artifact to [`compiled-output/`](../../compiled-output/README.md), per the repo-wide rule in [`CLAUDE.md`](../../CLAUDE.md).

## Prerequisite: install TeX Live

Nothing in this module compiles without a local TeX Live installation. Before running `make build` (or asking an agent to compile anything), install the packages this preamble actually uses — **not** `texlive-full` (~7 GB); this is a scoped set (~1–2 GB) covering babel Spanish, natbib/apalike, cleveref/csquotes, tikz/pgfplots, and `latexmk`:

**Debian/Ubuntu (apt):**
```bash
sudo apt update && sudo apt install -y \
  texlive-latex-base texlive-latex-recommended texlive-latex-extra \
  texlive-fonts-recommended texlive-lang-spanish texlive-pictures \
  texlive-bibtex-extra latexmk
```

**macOS (MacTeX, via Homebrew):**
```bash
brew install --cask mactex-no-gui   # full distribution; MacTeX has no small preset
# or a lighter route:
brew install --cask basictex && sudo tlmgr update --self && \
  sudo tlmgr install collection-langspanish collection-bibtexextra \
  collection-pictures cleveref csquotes latexmk
```

**Windows:** install [MiKTeX](https://miktex.org/) (installs missing packages on demand the first time you compile) or a full [TeX Live](https://tug.org/texlive/) distribution.

Verify the install with:
```bash
latexmk -v && kpsewhich cleveref.sty natbib.sty csquotes.sty apalike.bst
```
If any of those come back empty, that package/collection is missing — install it and retry rather than removing the feature from the preamble.

## File Overview

| File | Description |
| :--- | :--- |
| [`SKILL.md`](./SKILL.md) | The skill agents load when writing/editing/reviewing `.tex` content — toolchain decisions, semantic-markup rules, workflow. |
| [`preamble.tex`](./preamble.tex) | Ready-to-copy shared preamble: encoding, Spanish/babel, tables/floats, tikz/pgfplots, APA citations, cleveref. |
| [`Makefile`](./Makefile) / [`latexmkrc`](./latexmkrc) | `latexmk`-driven build template, output routed to `compiled-output/latex-build/`. |
| [`references/packages.md`](./references/packages.md) | What every package in the preamble is for. |
| [`references/citations-and-figures.md`](./references/citations-and-figures.md) | APA citation commands, quotations, cross-references, figure/table/equation templates. |
| [`references/troubleshooting.md`](./references/troubleshooting.md) | Diagnosing build failures specific to this stack (babel shorthands, cleveref ordering, float/longtable issues). |
| [`NOTICE.md`](./NOTICE.md) | Third-party attribution (MIT) for the parts of `SKILL.md` adapted from an existing open-source LaTeX skill. |

## Status

This module ships **configuration and rules**, not the thesis document itself — the actual document lives in [`thesis/`](../../thesis/README.md), which uses this module's `preamble.tex` directly via `\input{../skills/latex/preamble}` (so there is one preamble, not a copy that can drift) and its own copies of `Makefile`/`latexmkrc` (boilerplate, safe to copy once).

`preamble.tex` has been end-to-end test-compiled (`make build`, via `latexmk` + `pdflatex` + `bibtex`) with a sample chapter exercising every package: `description` lists, `\citet`/`\citep` (natbib+apalike), `\enquote{...}`, an equation, a `tikzpicture` figure, and a `booktabs` table — all cross-referenced with `\cref`. That test surfaced and fixed three real conflicts, now baked into `preamble.tex` and documented in [`references/troubleshooting.md`](./references/troubleshooting.md):
- `babel[spanish]`'s `<`/`>` guillemet shorthands crashing TikZ arrow tips (`\draw[->]`) — fixed with a properly-scoped `\shorthandoff{<>}`.
- `cleveref`'s Spanish default naming tables "Cuadro" instead of "Tabla" — overridden to match `writting-tools/normas-APA.md`.
- `csquotes`'s Spanish default rendering `\enquote{...}` as guillemets («») instead of the double quotation marks APA requires — fixed with a custom quote style.

## Provenance

The package choices and structure here were informed by a reference LaTeX thesis project the project tutor shared (`ai-project-dt-main`) — used only as a style/convention reference (document class, package list, Makefile pattern), not copied into or referenced from this repository. Some of `SKILL.md`'s semantic-markup guidance is adapted from the MIT-licensed [dbosk/claude-skills](https://github.com/dbosk/claude-skills) `latex-writing` skill — see [`NOTICE.md`](./NOTICE.md) for the full attribution and what was deliberately left out.
