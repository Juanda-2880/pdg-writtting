# Citations, Cross-References, Figures & Tables in LaTeX

How the APA 7 rules in [`reference-writting/`](../../reference-writting/README.md) and [`writting-tools/normas-APA.md`](../../writting-tools/normas-APA.md) map onto the actual LaTeX commands, given the `natbib` + `apalike` + `cleveref` setup in `../preamble.tex`.

## Citations (natbib, APA-style)

| You want | Command | Renders as |
| :--- | :--- | :--- |
| Narrative citation ("Author (Year) found...") | `\citet{key}` | Rodríguez (2024) |
| Parenthetical citation ("...as shown (Author, Year)") | `\citep{key}` | (Rodríguez, 2024) |
| With a page/locator (direct quotes) | `\citep[p.~12]{key}` | (Rodríguez, 2024, p. 12) |
| Multiple sources | `\citep{key1,key2}` | (Rodríguez, 2024; Muñoz, 2023) |
| Author already named, just the year | `\citeyearpar{key}` | (2024) |

Rules:
- **Never** hand-type a citation like `(Smith, 2020)` — always a `\cite*` command, so the bibliography stays the single source of truth and `apalike` handles formatting/sorting.
- Follow `reference-writting/direct-reference.md` for when a citation must carry a locator (`p.`/`pp.`/`para.`) — direct quotes always do.
- Follow `reference-writting/indirect-reference.md` for paraphrase/synthesis citations — usually `\citep{key}` or `\citet{key}`, no locator needed unless pointing to a specific passage.
- Every `\cite*` key must exist in the shared `.bib` file. If the Investigador hasn't supplied a real source yet, use `\cite{cite_needed}` as a visible, grep-able placeholder — **never** invent a BibTeX key/entry to fill the gap (see `agent-roles/Investigador.md`).

**apalike vs. strict APA 7**: `apalike.bst` gets the shape right (author-year, hanging indent, alphabetical) but has known small deviations from the literal APA-7 rulebook (e.g. `and` vs. `&` between authors, some punctuation details). If a reviewer flags a specific mismatch, prefer a spot patch or a small custom `.bst` tweak over swapping the whole citation engine — a wholesale switch to `apacite`/biblatex-apa is a structural change that goes through the Coordinador, not a silent substitution.

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
- Every numeric claim drafted from evidence (per `agent-roles/Investigador.md`) that appears in prose should also appear in a table if there are more than 2–3 data points — per `thesis-writing/writing-guide.md`'s rule that every numeric claim gets a table or figure.

## Equations

```latex
\begin{equation}\label{eq:respiratory-quotient}
    RQ = \frac{\text{CTR}}{\text{OTR}}
\end{equation}
```
Reference with `\cref{eq:respiratory-quotient}` → "Ecuación 3".
