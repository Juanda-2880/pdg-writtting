# Citations, Cross-References, Figures & Tables in LaTeX

How the citation rules in [`reference-writting/`](../../reference-writting/README.md) map onto the actual LaTeX commands, given the `natbib` + `unsrtnat` + `cleveref` setup in `../preamble.tex`.

> **Style since 2026-11-15: numeric, IEEE-like.** After the tutor's review (`\todo` in `main.tex`, 2026-11-14: numeric `[1]` with the title «Referencias», or alphanumeric `[AWT23]`), the authors chose the numeric style. `natbib` runs with `numbers,square,sort&compress`, `\bibliographystyle{unsrtnat}` orders the list by first citation and prints URLs, and the list is titled «Referencias» and listed in the table of contents. The prose rules of `reference-writting/` (what a citation may attribute, locators for direct quotes) still apply; only the rendering changed from author-year to numbers.

## Citations (natbib, numeric)

| You want | Command | Renders as |
| :--- | :--- | :--- |
| Narrative citation ("Author found...") | `\citet{key}` | Rodríguez et al. [4] |
| Parenthetical citation | `\citep{key}` | [4] |
| With a page/locator (direct quotes) | `\citep[p.~12]{key}` | [4, p. 12] |
| Multiple sources | `\citep{key1,key2,key3}` | [4–6] (compressed and sorted) |
| Secondary source (cited in another work) | `(Autor, citado en \citep{key})` | (Sridharan, citado en [17]) |

Don't use `\citealp`, `\citeyear` or `\citeyearpar`: in numeric mode they print a bare number or nothing useful.

Rules:
- **Never** hand-type a citation like `(Smith, 2020)` — always a `\cite*` command, so the bibliography stays the single source of truth and `unsrtnat` handles numbering and ordering.
- Follow `reference-writting/direct-reference.md` for when a citation must carry a locator (`p.`/`pp.`/`para.`) — direct quotes always do.
- Follow `reference-writting/indirect-reference.md` for paraphrase/synthesis citations — usually `\citep{key}` or `\citet{key}`, no locator needed unless pointing to a specific passage.
- Every `\cite*` key must exist in the shared `.bib` file. If the Investigador hasn't supplied a real source yet, use `\cite{cite_needed}` as a visible, grep-able placeholder — **never** invent a BibTeX key/entry to fill the gap (see `../../../agent-roles/Investigador.md`).

**unsrtnat output language**: `unsrtnat.bst` writes its fixed words in English (`and`, `In`, `pages`, `URL`). If a reviewer flags it, prefer a small custom `.bst` copy over swapping the citation engine; a switch to biblatex is a structural change that goes through the Coordinador, not a silent substitution.

## Direct quotes (csquotes)

- Short quotes inline: `\enquote{texto exacto}` — never manual `` `` `` / `''` or straight `"..."`. `csquotes` renders the correct quotation marks for `babel spanish`.
- Long quotes (≥40 words, per APA 7 / `reference-writting/direct-reference.md`): use a `quote` or `quotation` environment (block-indented), not `\enquote{}` around a huge paragraph.
- Every direct quote's citation must carry a page/paragraph locator (`\citep[p.~34]{key}`).

## Cross-references (cleveref)

- **Always** `\cref{label}` / `\Cref{label}` (sentence-initial). **Never** hand-typed `Figura~\ref{...}`, `Sección~\ref{...}`, etc. — `cleveref` supplies the right Spanish word ("Figura", "Tabla", "Capítulo", "Sección", "Ecuación") and number automatically, and stays correct if the document gets reordered.
- Use descriptive labels, prefixed by type: `fig:arquitectura-iasl`, `tab:requisitos-fr`, `cha:metodologia`, `sec:marco-teorico`, `eq:respiratory-quotient` — not `fig:1` or `label3`.
- Multiple references: `\cref{fig:a,fig:b}` → "Figuras 1 y 2" (cleveref handles the conjunction).

## Figures

```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.8\textwidth]{imagenes/nombre-descriptivo.png}
    \caption{Descripción clara y autocontenida del contenido de la figura.}
    \label{fig:nombre-descriptivo}
\end{figure}
```

- Store image files under an `imagenes/` folder next to the chapter files (matching the tutor's convention), with descriptive filenames — not `figura1.png`.
- The caption must be self-contained: a reader skimming only the List of Figures should understand what it shows.
- If a figure is adapted from a source, say so in the caption and cite it: `\caption{... Adaptado de \citep{key}.}`
- Prefer `[h]`/`[H]` (float package) placement for figures that must stay near their reference in the text; avoid piling up floats at chapter ends unless the layout truly requires it.

## Tables

```latex
\begin{table}[h]
    \centering
    \caption{Descripción clara del contenido de la tabla.}
    \label{tab:nombre-descriptivo}
    \begin{tabular}{lcc}
        \toprule
        Columna & Métrica A & Métrica B \\
        \midrule
        Fila 1 & valor & valor \\
        \bottomrule
    \end{tabular}
\end{table}
```

- Use `booktabs` rules (`\toprule`/`\midrule`/`\bottomrule`) — never `\hline` or vertical rules (`|`), per standard academic table style.
- Use `longtable`/`xltabular` instead of `tabular` for any table that risks spanning a page break (e.g. the full FR/NFR requirements list from `project-context/requirements.md`).
- Every numeric claim drafted from evidence (per `../../../agent-roles/Investigador.md`) that appears in prose should also appear in a table if there are more than 2–3 data points — per `thesis-writing/writing-guide.md`'s rule that every numeric claim gets a table or figure.

## Equations

```latex
\begin{equation}\label{eq:respiratory-quotient}
    RQ = \frac{\text{CTR}}{\text{OTR}}
\end{equation}
```
Reference with `\cref{eq:respiratory-quotient}` → "Ecuación 3".
