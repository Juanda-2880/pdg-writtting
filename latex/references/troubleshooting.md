# Troubleshooting the Build

Common failure modes for this specific stack (pdfLaTeX, `babel[spanish]`, `natbib`+`apalike`, `cleveref`, `tikz`/`pgfplots`) and how to diagnose them. Always run `make build` (see `../Makefile`) via `latexmk` rather than a single manual `pdflatex` pass — most of the symptoms below are just "it needs one more rerun," which `latexmk` already handles.

## "Undefined control sequence" or garbled quotation marks

`babel[spanish]` turns `"` into an **active shorthand character** (for the old-style `"a`, `"o` accent shortcuts) and `<<`/`>>` into guillemets (« »). This means:
- A stray literal `"` in prose (instead of `\enquote{...}` from `csquotes`) can render wrong or, in rare cases with other packages fighting over the same shorthand, throw an error.
- Always use `\enquote{...}` for quotes (see `citations-and-figures.md`) — never manual quote marks — and this class of bug disappears.
- If a `"` must appear literally (e.g. inside a URL or file path in `\texttt{}`), that's usually fine as-is since `\texttt` content isn't hyphenated/shorthand-processed the same way, but if something does misbehave inside a verbatim/URL context, wrap it or check `babel`'s `shorthands=off` scoping for that specific span.

## Citations show up as "?" or `[key?]` after a fresh build

Normal on the **first** `pdflatex` pass — the `.aux`/`.bbl` files don't exist yet. `latexmk` (via `make build`) detects this and reruns `bibtex`/`pdflatex` automatically until it converges (usually 3 passes: pdflatex → bibtex → pdflatex → pdflatex). If it's still broken after a `latexmk` run:
- Check the citation key actually exists in the `.bib` file (typo, or the Investigador flagged it as `cite_needed` and it was never resolved — see `agent-roles/Investigador.md`).
- Check `compiled-output/latex-build/*.blg` (the bibtex log) for the real error — bibtex failures are otherwise silent in the PDF.

## `! Argument of \language@active@arg> has an extra }.` when using TikZ (verified)

Hit this compiling a plain `\draw[->] (a) -- (b);` inside a `tikzpicture` with `babel[spanish]` loaded. **Cause**: `babel[spanish]` makes `<` and `>` active shorthand characters for guillemets (« »), which collides with TikZ arrow-tip syntax (`->`, `<-`, `<->`). `../preamble.tex` already fixes this with `\AtBeginDocument{\shorthandoff{<>}}` — note the `\AtBeginDocument`: a bare `\shorthandoff{<>}` placed directly in the preamble does **not** work, because babel only activates the language's shorthands when `\begin{document}` runs, silently re-enabling them after a preamble-level call. If this error resurfaces, check that the shorthand-off call is still present and still wrapped in `\AtBeginDocument`.

## `cleveref` prints the wrong word (e.g. "Cuadro" instead of "Tabla")

- Confirm `\usepackage[spanish,capitalize]{cleveref}` loads **after** `hyperref` in the preamble — reversed order is the most common cause of broken cross-references.
- **Verified**: cleveref's Spanish name set prints `Figura`/`Capítulo`/`Sección`/`Ecuación` correctly out of the box, but its default word for the `table` type is `Cuadro`, not `Tabla` — `../preamble.tex` already overrides this to match `writting-tools/normas-APA.md`:
  ```latex
  \crefname{table}{Tabla}{Tablas}
  \Crefname{table}{Tabla}{Tablas}
  ```
  If another type's printed word doesn't match this thesis's own terminology, override it the same way (see `citations-and-figures.md`).

## `\enquote{...}` renders as « guillemets » instead of "double quotes"

**Verified**: `csquotes`'s automatic style, driven by `babel[spanish]`, defaults to Spanish guillemets — but `writting-tools/normas-APA.md` requires plain double quotation marks for short direct quotes. `../preamble.tex` already defines and selects a custom `apa-spanish` quote style (`\DeclareQuoteStyle` + `\setquotestyle`) to override this. If quotes come out as guillemets again, check that override wasn't accidentally removed from the preamble.

## `! LaTeX Error: Float(s) lost.` or figures drifting far from their reference

- `[H]` (from the `float` package) forces exact placement but can produce large blank gaps or "Float(s) lost" if used inside another float or a two-column/landscape context. Prefer `[h]` (lowercase, LaTeX's own placement hint) for ordinary figures, and reserve `[H]` for cases where exact placement genuinely matters (e.g. a figure that must sit directly under the paragraph introducing it).
- If figures still drift, it's usually because several floats piled up — split the surrounding text so each figure has enough body text after it to "absorb" the page break, or move the figure to right after its first mention.

## `longtable`/`xltabular` breaks awkwardly across a page

- Add `\endhead`/`\endfoot` rows so the header repeats on every page (see any working example table in the tutor's reference chapters for the pattern) — a `longtable` without them just resumes with no header, which is confusing for a reader.

## pgfplots/tikz: `Package pgfplots Error: Sorry, the given file couldn't be found`

- Check the image/data path is relative to the `.tex` file being compiled, not to `latex/` or the repo root — `\includegraphics`/`\input` paths resolve relative to the compiling document's directory (or `\graphicspath`, if set).

## Build is slow because of TikZ/pgfplots

- Large or many TikZ diagrams recompiled on every run add up. If this becomes painful, look into `\usetikzlibrary{external}` to cache compiled TikZ pictures — but only add this once it's an actual problem, not preemptively (see `CLAUDE.md`'s "don't add complexity ahead of need").

## When truly stuck

Run a bare, single `pdflatex -interaction=nonstopmode -halt-on-error -output-directory=compiled-output/latex-build main.tex` (no `latexmk`, no reruns) to see the *first* real error without `latexmk`'s rerun noise, then work from there.
