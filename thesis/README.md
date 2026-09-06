# The Thesis Document

This is where the actual thesis text lives — as opposed to `thesis-writing/`, `objectives-writting/`, etc., which are *guidance* modules, not content. Everything under `chapters/` is real, submittable prose (once written).

## Why this is split into one file per chapter

**So an agent never has to load the whole thesis to work on one part of it.** A finished undergraduate thesis runs 60–100+ pages; reading all of it into context to edit one paragraph of Metodología wastes context budget and buries the actually-relevant text in noise. Splitting by chapter means:

- Drafting/editing **one** chapter → read **that one file**, plus whatever it points to (its own header comment names the exact modules to check — you usually don't need more).
- `main.tex` itself stays tiny — a skeleton of `\include{chapters/...}` lines, the title page, and front matter. Never read it to "see the whole thesis"; read `STATUS.md` for that instead.
- `STATUS.md` is the one file that gives a whole-document overview without pulling any prose into context — check it first.

## Where to start

1. **Read `STATUS.md`** — it says what's done, what's in progress, what's untouched. Don't infer status by opening chapter files.
2. **Read only the chapter file(s) your task is actually about.** Each one opens with a comment block stating what it must contain, what it must *not* contain, and which modules to draft from — that's usually enough context on its own.
3. **Cross-chapter work is the exception, not the default.** Only open multiple chapter files when the task genuinely requires it:
   - The Revisor's macro review (`../agent-roles/Revisor.md`) checks flow *between* chapters — that legitimately needs to read the adjacent ones.
   - Discusión (`chapters/05-discusion.tex`) interprets Resultados and ties back to Marco teórico — drafting it well requires re-reading those two, not just its own stub.
   - Otherwise, a chapter's own header comment + `STATUS.md` should be enough; don't preemptively open the rest of the thesis "just in case."

## File layout

| Path | What it is |
| :--- | :--- |
| `main.tex` | Document skeleton: `\documentclass`, `\input{../latex/preamble}`, title page, front matter (Resumen/Abstract — written last), the ordered list of `\include{chapters/...}`, bibliography, appendices. |
| `STATUS.md` | Per-chapter status tracker — read this, not the chapters, to see where the thesis stands. |
| `chapters/NN-nombre.tex` | One file per chapter (see below). Numbered so the reading/compile order is obvious; `99-anexos.tex` is deliberately last regardless of how many numbered chapters exist. |
| `references.bib` | The single shared BibTeX database — every citation key used anywhere in `chapters/` must resolve here (see `../latex/references/citations-and-figures.md`). |
| `imagenes/` | Figures referenced from `chapters/` — descriptive filenames, not `figura1.png` (see `../latex/references/citations-and-figures.md`). |
| `Makefile` / `.latexmkrc` | Copied from `../latex/` — run `make build` from this folder. Output goes to `../compiled-output/latex-build/`, never here. |

## Chapters (undergraduate/TFG structure, per `../thesis-writing/structure.md`)

| # | File | Chapter |
| :--- | :--- | :--- |
| — | `main.tex` front matter | Resumen / Abstract (written **last**) |
| 01 | `chapters/01-introduccion.tex` | Introducción |
| 02 | `chapters/02-marco-teorico.tex` | Marco teórico |
| 03 | `chapters/03-metodologia.tex` | Metodología |
| 04 | `chapters/04-resultados.tex` | Resultados |
| 05 | `chapters/05-discusion.tex` | Discusión |
| 06 | `chapters/06-conclusiones.tex` | Conclusiones |
| — | `references.bib` → `\bibliography{}` | Bibliografía |
| 99 | `chapters/99-anexos.tex` | Anexos |

Each stub file already has a comment block naming exactly what it must/must-not contain and which modules govern it — read that before asking "what goes here."

## Writing workflow

Follow `../agent-roles/README.md`'s Coordinador → Investigador → Redactor → Revisor loop. In practice, for one chapter:

1. Coordinador checks `STATUS.md`, assigns the chapter/subsection.
2. Investigador gathers evidence from `../project-context/` (and literature, for Marco teórico), flags gaps as `[verify: ...]`/`cite_needed` — never invents.
3. Redactor writes into the chapter file, following its header comment, `../thesis-writing/writing-guide.md`, and `../latex/SKILL.md` for the LaTeX mechanics.
4. Revisor runs `make build` from this folder and the checklist in `../thesis-writing/review-checklist.md`.
5. Coordinador updates `STATUS.md`.

## Compiling

```bash
cd thesis
make build   # or: make watch
```
See `../latex/README.md` for the TeX Live prerequisites and `../latex/references/troubleshooting.md` if the build fails.

## Adding/renaming a chapter

Goes through the Coordinador (`../agent-roles/Coordinador.md`) — it's a structural change. When it happens, update **together, in the same change**: the chapter file itself, the `\include` list in `main.tex`, the table above, and `STATUS.md`. Adding a new top-level folder or restructuring this one also triggers the repo-wide rule in `../CLAUDE.md` — update the root `README.md` too.
