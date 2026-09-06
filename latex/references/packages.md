# Package Reference

What each package in `../preamble.tex` is for, and why it's there. Don't add a new package to solve a one-off problem without checking here first — and don't add a package "just in case."

| Package | Purpose |
| :--- | :--- |
| `inputenc` (utf8) | Type accented Spanish characters (ñ, á, é, í, ó, ú, ü) directly in the source. |
| `fontenc` (T1) | Correct hyphenation and copy-paste of accented characters; required for monospace fonts to select properly under pdfLaTeX. |
| `lmodern` | Modern, T1-native font shapes (avoids blurry bitmap fonts at odd sizes). |
| `babel` (spanish) | Spanish hyphenation patterns and localized names (`\listtablename`, cross-reference words, date formatting). |
| `xcolor` | Color support (used sparingly — this thesis does not use colored table cells). |
| `array` | Extended column types for `tabular`/`longtable`. |
| `tocloft` | Fine control over Table of Contents spacing. |
| `float` | The `[H]` float placement specifier (forces "exactly here"). |
| `setspace` | Line spacing control (`\doublespacing` on the title page). |
| `pdflscape` | Landscape-oriented pages for wide tables/figures. |
| `booktabs` | Professional table rules (`\toprule`, `\midrule`, `\bottomrule`) — never use `\hline`. |
| `longtable` | Tables that span multiple pages (data appendices, long comparison tables). |
| `xltabular` | Combines `longtable` with `tabularx`'s auto-width columns. |
| `multirow` | Table cells spanning multiple rows. |
| `amsmath` | Standard math environments and operators (`RQ = \dfrac{\text{CTR}}{\text{OTR}}`-style equations). |
| `graphicx` | `\includegraphics`. |
| `caption` | Consistent caption styling (bold label, italic caption text). |
| `tikz` / `pgfplots` | Diagrams and plots drawn directly in LaTeX (architecture diagrams, data flow figures). Only reach for this when a hand-drawn/programmatic diagram is genuinely better than a pre-rendered image (e.g. exported from Python) — don't redraw a plot in TikZ that a data script already produced as a PNG/PDF. |
| `verbatim`, `framed` | Literal text blocks (rare in this thesis; mostly for appendix log excerpts). |
| `csquotes` | `\enquote{...}` for quotations instead of manual `"..."`/`` ``...'' ``. Language-aware, works with babel spanish. See `citations-and-figures.md` for when to use it vs. a direct-quote citation. |
| `fancyhdr` | Page headers/footers (page number in the footer, per the tutor's convention). |
| `sectsty` | Sans-serif section headings. |
| `natbib` (authoryear, round) | APA-style `\citet`/`\citep` commands. Paired with `\bibliographystyle{apalike}`. See `citations-and-figures.md`. |
| `hyperref` | Clickable cross-references and a navigable PDF outline. **Must load before `cleveref`.** |
| `cleveref` (spanish, capitalize) | `\cref{...}`/`\Cref{...}` — auto-prefixed, localized cross-references ("Figura 3", "Capítulo 2") instead of hand-typed `Figura~\ref{...}`. |

## Adding a new package

1. Check this table first — the need may already be covered.
2. If genuinely new, add it to `preamble.tex` in the matching section (encoding/language/tables/floats/math/citations/etc.), not at the bottom.
3. Add a row here explaining why.
4. Per `agent-roles/Redactor.md`, don't introduce new packages or layout changes to an existing draft without the Coordinador's sign-off — an uncoordinated package addition is a common source of build breakage others then have to debug.
