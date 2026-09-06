# Thesis Status

Single source of truth for what stage each section is at. The **Coordinador** (see `../agent-roles/Coordinador.md`) keeps this updated — check here before starting work instead of opening every chapter file to figure out what's done.

Status values: `not started` · `drafted` · `under review` · `approved`.

| Section | File | Status | Notes |
| :--- | :--- | :--- | :--- |
| Resumen / Abstract | `main.tex` (front matter) | not started | Write last, per `thesis-writing/SKILL.md` Mode 1/2 — needs the rest of the thesis done first. |
| Introducción | `chapters/01-introduccion.tex` | not started | |
| Marco teórico | `chapters/02-marco-teorico.tex` | not started | |
| Metodología | `chapters/03-metodologia.tex` | not started | |
| Resultados | `chapters/04-resultados.tex` | not started | |
| Discusión | `chapters/05-discusion.tex` | not started | |
| Conclusiones | `chapters/06-conclusiones.tex` | not started | |
| Anexos | `chapters/99-anexos.tex` | not started | |
| Bibliografía | `references.bib` | not started | Populated as the Investigador supplies real sources — see `../agent-roles/Investigador.md`. |

## How to update this file

- Change a row's status the moment work on it actually changes state — don't batch updates.
- `drafted` → the Redactor has written prose and it compiles (`make build`).
- `under review` → the Revisor is actively checking it (`../agent-roles/Revisor.md`).
- `approved` → the Revisor signed off; only the Coordinador reopens an approved section.
- Use Notes for anything a future session needs to know at a glance (a blocking gap, a pending decision) — not a full changelog; git history already has that.
