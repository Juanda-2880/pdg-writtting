# Thesis Status

Single source of truth for what stage each section is at. The **Coordinador** (see `../skills/agent-roles/Coordinador.md`) keeps this updated — check here before starting work instead of opening every chapter file to figure out what's done.

Status values: `not started` · `drafted` · `under review` · `approved`.

| Sección | Archivo | Estado | Notas |
| :--- | :--- | :--- | :--- |
| Resumen | `main.tex` (front matter) | not started | Se escribe al final (formato: máx. 1 página, 4–6 palabras clave, sin citas). |
| Abstract | `main.tex` (front matter) | not started | Se escribe al final, junto con el Resumen. |
| Lista de acrónimos | `main.tex` (front matter) | drafted | 16 siglas realmente usadas en el documento. Pendiente: la expansión oficial de SAAMFI (ADR-011). |
| Glosario de términos | `main.tex` (front matter) | not started | |
| Motivación y antecedentes | `chapters/01-motivacion-antecedentes.tex` | under review | Contexto, antecedentes y justificación. Máx. 3 páginas — Revisor mide 4 páginas reales en el PDF compilado; ver `../compiled-output/revision-anteproyecto.md`. **7 comentarios `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ADR-013 (VRAM real) y ADR-014 (antecedente institucional de acceso). |
| Descripción del problema | `chapters/02-descripcion-problema.tex` | under review | Identificación (causa–efecto) y formulación. Máx. 1 página — Revisor mide 2 páginas reales; ver `../compiled-output/revision-anteproyecto.md`. |
| Objetivos | `chapters/04-objetivos.tex` | under review | 1 general + 4 específicos, reformulados según `skills/objectives-writting/`. Umbral de "tiempo real" definido (ventana ≤ 5 min). Pendiente: criterio cuantitativo de aceptación operacional del obj. 4 (ADR-004). Máx. 1 página — Revisor mide 2 páginas reales; ver `../compiled-output/revision-anteproyecto.md`. **5 comentarios `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ADR-015 (el objetivo de gobernanza, ¿diseña o implementa?). |
| Marco teórico | `chapters/05-marco-teorico.tex` | not started | Aplazado por decisión del autor; requiere revisión bibliográfica dedicada. Máx. 4 páginas. |
| Estado del arte | `chapters/06-estado-del-arte.tex` | not started | Aplazado por decisión del autor; requiere revisión bibliográfica dedicada. Máx. 4 páginas. |
| Metodología | `chapters/07-metodologia.tex` | under review | Cuerpo redactado (DSR + Scrum, fases mapeadas a objetivos, riesgos). Esquema de trabajo y presupuesto ya redactados. Pendiente solo el cronograma (ADR-008). Sin extensión máxima definida por el formato. **6 comentarios `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ADR-016 (¿se sostiene DSR + Scrum?). **Pendiente de redacción (2026-09-12):** el capítulo sigue describiendo una fase de "análisis y estabilización del backlog heredado" y un "código heredado de la primera etapa del sistema web" — `project-context/documentation.md` ya se corrigió (no hay backlog heredado; este proyecto no es continuación directa del anterior, solo comparte macro-proyecto), falta que el Redactor alinee esta prosa con esa corrección. Los `\cref{}` rotos hacia el capítulo de Hipótesis y restricciones (eliminado) ya se repararon mecánicamente; el contenido de fondo sobre el backlog heredado todavía no. |
| Contribución y resultados | `chapters/08-contribucion-resultados.tex` | under review | Aportes, capacidades del investigador, resultados/entregables por objetivo. Máx. 4 páginas — Revisor mide 3 páginas reales, dentro del límite. **1 comentario `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ninguna nueva; lo que reclama ya está en ADR-008 (cronograma). |
| Anexos | `chapters/99-anexos.tex` | not started | Pendientes: análisis de participación, árbol de problemas, árbol de objetivos. El cap. 02 tiene un `[verify:]` esperando la etiqueta del árbol de problemas. |
| Bibliografía | `references.bib` | drafted | 31 fuentes verificadas por el Investigador (MLOps, schedulers GPU, DRF/Fair-Share, vLLM/cuantización, DSR/SUS). Dossier de evidencia en el scratchpad de la sesión. Vacío conocido: cifras de costo nube pública, sin fuente arbitrada → `cite_needed`. **Pendiente (2026-09-12):** 6 fuentes anteriores a 2015 (`yoo-slurm-2003`, `hevner-designscienceis-2004`, `peffers-dsrm-2007`, `ghodsi-dominantresourcefairness-2011`, `vavilapalli-yarn-2013`, `brooke-sus-1996`) incumplen la nueva regla de vigencia de `skills/reference-writting/recency.md` — ver la nota de proceso más abajo. |

## Dudas abiertas

Las dudas que bloquean partes del documento **no se listan aquí**: viven en [`../project-context/ADR.md`](../project-context/ADR.md), una por entrada, con el archivo y el marcador exactos donde se usan. Este archivo registra el *estado de redacción*; ese otro registra *qué falta decidir*. Al cerrar una duda se borra su entrada allí.

## Decisiones estructurales vigentes

- **2026-09-06 — El documento sigue la estructura de ANTEPROYECTO** de `../project-context/formato-anteproyecto.md`, no la estructura de tesis final de `../skills/thesis-writing/structure.md`. Por eso no existen capítulos de Resultados, Discusión ni Conclusiones: aún no corresponden a esta entrega.
- **2026-09-12 — Se eliminó el capítulo "Hipótesis y restricciones" (antes `chapters/03-hipotesis-restricciones.tex`), por decisión de los autores.** El formato de la facultad sí contempla esa sección (`project-context/formato-anteproyecto.md`), así que esto es una desviación deliberada del formato, no un olvido — queda registrado aquí para que ningún agente futuro la "restaure" por cuenta propia. El numerado de capítulos salta de 02 a 04 a propósito (ver `README.md`); no se renumeraron los archivos restantes porque el número de archivo no determina el número de capítulo en el PDF compilado (eso lo genera `\chapter`), y renombrar habría obligado a reescribir las rutas que citan `../project-context/ADR.md` en sus entradas "Dónde se usa". Como consecuencia, se cerraron ADR-018 (quedó sin objeto) y se recortó el alcance de ADR-004 y ADR-013 (ya no apuntan al capítulo eliminado). `chapters/07-metodologia.tex` tenía siete `\cref{}` hacia el capítulo eliminado; se repararon quitando la referencia cruzada rota, sin tocar el contenido de fondo que discuten (ver la nota de la fila Metodología arriba).
- **2026-09-12 — Se eliminó toda mención a la "Lista de símbolos"** (nota en `main.tex`, fila en esta tabla, frase en `README.md`), por decisión de los autores. Antes se omitía la sección dejando una nota explicando por qué; ahora no queda ni la nota, porque el formato la permite obviar sin explicación (`project-context/formato-anteproyecto.md`, "Lista de símbolos").
- **2026-09-12 — Nueva regla de vigencia de fuentes: ninguna cita externa puede tener más de 11 años (2015 o posterior, contado desde 2026), por decisión de los autores.** Regla completa en [`../skills/reference-writting/recency.md`](../skills/reference-writting/recency.md); aplicada por el Investigador al buscar evidencia (`../skills/agent-roles/Investigador.md`) y verificada por el Revisor al revisar citas (`../skills/agent-roles/Revisor.md`).

## Trabajo pendiente para el próximo ciclo de investigación/revisión

**La próxima vez que un Revisor revise cualquier capítulo, o que se retome una secuencia de redacción en la tesis, se debe volver a correr el proceso investigativo (rol Investigador) sobre las 6 fuentes de `references.bib` anteriores a 2015** listadas en la fila "Bibliografía" arriba y en `../skills/reference-writting/recency.md` — buscar una fuente de 2015 en adelante que respalde la misma afirmación, o escalarlo al Coordinador si no aparece un reemplazo adecuado. No es una duda para `../project-context/ADR.md` (no depende de una decisión humana, es una tarea de investigación), así que vive aquí hasta que se resuelva.

## How to update this file

- Change a row's status the moment work on it actually changes state — don't batch updates.
- `drafted` → the Redactor has written prose and it compiles (`make build`).
- `under review` → the Revisor is actively checking it (`../skills/agent-roles/Revisor.md`).
- `approved` → the Revisor signed off; only the Coordinador reopens an approved section.
- Use Notes for anything a future session needs to know at a glance (a blocking gap, a pending decision) — not a full changelog; git history already has that.
