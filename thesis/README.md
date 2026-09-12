# The Thesis Document

This is where the actual thesis text lives — as opposed to `skills/thesis-writing/`, `skills/objectives-writting/`, etc., which are *guidance* modules, not content. Everything under `chapters/` is real, submittable prose (once written).

## Why this is split into one file per chapter

**So an agent never has to load the whole thesis to work on one part of it.** A finished undergraduate thesis runs 60–100+ pages; reading all of it into context to edit one paragraph of Metodología wastes context budget and buries the actually-relevant text in noise. Splitting by chapter means:

- Drafting/editing **one** chapter → read **that one file**, plus whatever it points to (its own header comment names the exact modules to check — you usually don't need more).
- `main.tex` itself stays tiny — a skeleton of `\include{chapters/...}` lines, the title page, and front matter. Never read it to "see the whole thesis"; read `STATUS.md` for that instead.
- `STATUS.md` is the one file that gives a whole-document overview without pulling any prose into context — check it first.

## Where to start

1. **Read `STATUS.md`** — it says what's done, what's in progress, what's untouched. Don't infer status by opening chapter files.
2. **Read only the chapter file(s) your task is actually about.** Each one opens with a comment block stating what it must contain, what it must *not* contain, and which modules to draft from — that's usually enough context on its own.
3. **Cross-chapter work is the exception, not the default.** Only open multiple chapter files when the task genuinely requires it:
   - The Revisor's macro review (`../skills/agent-roles/Revisor.md`) checks flow *between* chapters — that legitimately needs to read the adjacent ones.
   - Discusión (`chapters/05-discusion.tex`) interprets Resultados and ties back to Marco teórico — drafting it well requires re-reading those two, not just its own stub.
   - Otherwise, a chapter's own header comment + `STATUS.md` should be enough; don't preemptively open the rest of the thesis "just in case."

## File layout

| Path | What it is |
| :--- | :--- |
| `main.tex` | Document skeleton: `\documentclass`, `\input{../skills/latex/preamble}`, title page, front matter (Resumen/Abstract — written last — Lista de acrónimos, Glosario), the ordered list of `\include{chapters/...}`, bibliography, appendices. |
| `STATUS.md` | Per-chapter status tracker — read this, not the chapters, to see where the thesis stands. |
| `chapters/NN-nombre.tex` | One file per chapter/section (see below). Numbered so the reading/compile order is obvious; `99-anexos.tex` is deliberately last regardless of how many numbered chapters exist. |
| `references.bib` | The single shared BibTeX database — every citation key used anywhere in `chapters/` must resolve here (see `../skills/latex/references/citations-and-figures.md`). |
| `imagenes/` | Figures referenced from `chapters/` — descriptive filenames, not `figura1.png` (see `../skills/latex/references/citations-and-figures.md`). |
| `Makefile` / `.latexmkrc` | Copied from `../skills/latex/` — run `make build` from this folder. Output goes to `../compiled-output/latex-build/`, never here. |

## Capítulos (estructura de **anteproyecto**, según `../project-context/formato-anteproyecto.md`)

> [!IMPORTANT]
> El documento sigue la estructura de **anteproyecto** exigida por la facultad, **no** la estructura de tesis final descrita en `../skills/thesis-writing/structure.md`. Por eso no hay capítulos de Resultados, Discusión ni Conclusiones: no corresponden a esta entrega. Esa decisión está registrada en `STATUS.md`.

| # | Archivo | Sección | Extensión máxima |
| :--- | :--- | :--- | :--- |
| — | `main.tex` front matter | Resumen / Abstract (se escriben **al final**) | 1 página / 1 párrafo |
| — | `main.tex` front matter | Lista de acrónimos, Glosario de términos | — |
| 01 | `chapters/01-motivacion-antecedentes.tex` | Motivación y antecedentes (contexto, antecedentes, justificación) | 3 páginas |
| 02 | `chapters/02-descripcion-problema.tex` | Descripción del problema (identificación y formulación) | 1 página |
| 03 | `chapters/03-hipotesis-restricciones.tex` | Hipótesis y restricciones | 1 página |
| 04 | `chapters/04-objetivos.tex` | Objetivos (general + específicos) | 1 página |
| 05 | `chapters/05-marco-teorico.tex` | Marco teórico | 4 páginas |
| 06 | `chapters/06-estado-del-arte.tex` | Estado del arte | 4 páginas |
| 07 | `chapters/07-metodologia.tex` | Metodología (esquema de trabajo, fases, riesgos, cronograma, presupuesto) | — |
| 08 | `chapters/08-contribucion-resultados.tex` | Contribución y resultados del proyecto de grado | 4 páginas |
| — | `references.bib` → `\bibliography{}` | Referencias bibliográficas | — |
| 99 | `chapters/99-anexos.tex` | Anexos (análisis de participación, árbol de problemas, árbol de objetivos) | — |

La **Lista de símbolos** se omite deliberadamente: el documento no introduce símbolos matemáticos y el formato permite obviar esa sección.

Cada archivo ya trae un bloque de comentarios que dice exactamente qué debe y qué no debe contener, y qué módulos lo gobiernan — léelo antes de preguntar "qué va aquí".

## Writing workflow

Follow `../skills/agent-roles/README.md`'s Coordinador → Investigador → Redactor → Revisor loop. In practice, for one chapter:

1. Coordinador checks `STATUS.md`, assigns the chapter/subsection.
2. Investigador gathers evidence from `../project-context/` (and literature, for Marco teórico and Estado del arte), flags gaps as `[verify: ...]`/`cite_needed` — never invents.
3. Redactor writes into the chapter file, following its header comment, `../skills/thesis-writing/writing-guide.md`, and `../skills/latex/SKILL.md` for the LaTeX mechanics.
4. Revisor runs `make build` from this folder and the checklist in `../skills/thesis-writing/review-checklist.md`.
5. Coordinador updates `STATUS.md`.

## Compiling

```bash
cd thesis
make build   # or: make watch
```
See `../skills/latex/README.md` for the TeX Live prerequisites and `../skills/latex/references/troubleshooting.md` if the build fails.

## Adding/renaming a chapter

Goes through the Coordinador (`../skills/agent-roles/Coordinador.md`) — it's a structural change. When it happens, update **together, in the same change**: the chapter file itself, the `\include` list in `main.tex`, the table above, and `STATUS.md`. Adding a new top-level folder or restructuring this one also triggers the repo-wide rule in `../CLAUDE.md` — update the root `README.md` too.
