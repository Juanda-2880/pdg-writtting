# Thesis Status

Single source of truth for what stage each section is at. The **Coordinador** (see `../agent-roles/Coordinador.md`) keeps this updated — check here before starting work instead of opening every chapter file to figure out what's done.

Status values: `not started` · `drafted` · `under review` · `approved`.

| Sección | Archivo | Estado | Notas |
| :--- | :--- | :--- | :--- |
| Resumen | `main.tex` (front matter) | not started | Se escribe al final (formato: máx. 1 página, 4–6 palabras clave, sin citas). |
| Abstract | `main.tex` (front matter) | not started | Se escribe al final, junto con el Resumen. |
| Lista de acrónimos | `main.tex` (front matter) | drafted | 16 siglas realmente usadas en el documento. Pendiente: la expansión oficial de SAAMFI (ADR-011). |
| Glosario de términos | `main.tex` (front matter) | not started | |
| Lista de símbolos | — | n/a | Omitida deliberadamente: el documento no introduce símbolos matemáticos y el formato permite obviarla. |
| Motivación y antecedentes | `chapters/01-motivacion-antecedentes.tex` | under review | Contexto, antecedentes y justificación. Máx. 3 páginas — Revisor mide 4 páginas reales en el PDF compilado; ver `../compiled-output/revision-anteproyecto.md`. **7 comentarios `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ADR-013 (VRAM real) y ADR-014 (antecedente institucional de acceso). |
| Descripción del problema | `chapters/02-descripcion-problema.tex` | under review | Identificación (causa–efecto) y formulación. Máx. 1 página — Revisor mide 2 páginas reales; ver `../compiled-output/revision-anteproyecto.md`. |
| Hipótesis y restricciones | `chapters/03-hipotesis-restricciones.tex` | under review | Máx. 1 página — Revisor mide 2 páginas reales; ver `../compiled-output/revision-anteproyecto.md`. **1 comentario `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ADR-018 (specs de hardware: ¿restricción o anexo?), ligada a ADR-013. |
| Objetivos | `chapters/04-objetivos.tex` | under review | 1 general + 4 específicos, reformulados según `objectives-writting/`. Umbral de "tiempo real" definido (ventana ≤ 5 min). Pendiente: criterio cuantitativo de aceptación operacional del obj. 4 (ADR-004). Máx. 1 página — Revisor mide 2 páginas reales; ver `../compiled-output/revision-anteproyecto.md`. **5 comentarios `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ADR-015 (el objetivo de gobernanza, ¿diseña o implementa?). |
| Marco teórico | `chapters/05-marco-teorico.tex` | not started | Aplazado por decisión del autor; requiere revisión bibliográfica dedicada. Máx. 4 páginas. |
| Estado del arte | `chapters/06-estado-del-arte.tex` | not started | Aplazado por decisión del autor; requiere revisión bibliográfica dedicada. Máx. 4 páginas. |
| Metodología | `chapters/07-metodologia.tex` | under review | Cuerpo redactado (DSR + Scrum, fases mapeadas a objetivos, riesgos). Esquema de trabajo y presupuesto ya redactados. Pendiente solo el cronograma (ADR-008). Sin extensión máxima definida por el formato. **6 comentarios `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ADR-016 (¿se sostiene DSR + Scrum?) y ADR-017 (fase de estabilización y orden de fases). |
| Contribución y resultados | `chapters/08-contribucion-resultados.tex` | under review | Aportes, capacidades del investigador, resultados/entregables por objetivo. Máx. 4 páginas — Revisor mide 3 páginas reales, dentro del límite. **1 comentario `\todo{}` del tutor pendientes** (commit `fb9ee6b`); triaje en `../compiled-output/triage-tutor.md`; dudas nuevas: ninguna nueva; lo que reclama ya está en ADR-008 (cronograma). |
| Anexos | `chapters/99-anexos.tex` | not started | Pendientes: análisis de participación, árbol de problemas, árbol de objetivos. El cap. 02 tiene un `[verify:]` esperando la etiqueta del árbol de problemas. |
| Bibliografía | `references.bib` | drafted | 31 fuentes verificadas por el Investigador (MLOps, schedulers GPU, DRF/Fair-Share, vLLM/cuantización, DSR/SUS). Dossier de evidencia en el scratchpad de la sesión. Vacío conocido: cifras de costo nube pública, sin fuente arbitrada → `cite_needed`. |

## Dudas abiertas

Las dudas que bloquean partes del documento **no se listan aquí**: viven en [`../project-context/ADR.md`](../project-context/ADR.md), una por entrada, con el archivo y el marcador exactos donde se usan. Este archivo registra el *estado de redacción*; ese otro registra *qué falta decidir*. Al cerrar una duda se borra su entrada allí.

## Decisiones estructurales vigentes

- **2026-09-06 — El capítulo 3 excede su límite de 1 página, por decisión del autor.** La causa no es la prosa sino el encabezado de capítulo de la clase `report`, que consume ~8 líneas de la primera página de cada capítulo; comprimirlo (con `titlesec`) haría caber los capítulos 2, 3 y 4 en una página con el contenido completo, pero se alejaría del aspecto del proyecto de referencia del tutor. Se optó por conservar la maquetación y el contenido argumentado, y aceptar que el capítulo 3 ocupe 2 páginas. **No volver a recortar ese capítulo para "arreglar" la extensión.**
- **2026-09-06 — El documento sigue la estructura de ANTEPROYECTO** de `../project-context/formato-anteproyecto.md`, no la estructura de tesis final de `../thesis-writing/structure.md`. Por eso no existen capítulos de Resultados, Discusión ni Conclusiones: aún no corresponden a esta entrega.

## How to update this file

- Change a row's status the moment work on it actually changes state — don't batch updates.
- `drafted` → the Redactor has written prose and it compiles (`make build`).
- `under review` → the Revisor is actively checking it (`../agent-roles/Revisor.md`).
- `approved` → the Revisor signed off; only the Coordinador reopens an approved section.
- Use Notes for anything a future session needs to know at a glance (a blocking gap, a pending decision) — not a full changelog; git history already has that.
