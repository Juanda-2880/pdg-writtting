# Thesis Status

Single source of truth for what stage each section is at. The **Coordinador** (see `../skills/agent-roles/Coordinador.md`) keeps this updated — check here before starting work instead of opening every chapter file.

Status values: `not started` · `drafted` · `under review` · `approved`.

> **Segunda versión, 2026-09-12.** Esta tabla refleja la segunda pasada completa sobre el documento: se aplicaron los 18 comentarios `\todo{}` del tutor (commit `fb9ee6b`), se cerraron 17 entradas de `ADR.md`, se redactó el Marco teórico y se ajustó cada capítulo a la extensión máxima del formato. Extensiones medidas sobre el PDF compilado (`make build`, 31 páginas), no estimadas.

| Sección | Archivo | Estado | Extensión | Notas |
| :--- | :--- | :--- | :--- | :--- |
| Resumen | `main.tex` (front matter) | not started | máx. 1 pág. | Se escribe al final, con 4-6 palabras clave y sin citas. |
| Abstract | `main.tex` (front matter) | not started | máx. 1 párr. | Se escribe al final, junto con el Resumen. |
| Lista de acrónimos | `main.tex` (front matter) | drafted | — | 15 siglas realmente usadas. SAAMFI salió de aquí: es nombre propio, no sigla (autores, 2026-09-12), y pasó al Glosario. |
| Glosario de términos | `main.tex` (front matter) | drafted | — | Contiene SAAMFI. Ampliable con más términos de dominio si el Revisor lo ve necesario. |
| Motivación y antecedentes | `chapters/01-motivacion-antecedentes.tex` | under review | **3 / 3 pág.** | Cumple. Incorpora el antecedente institucional de acceso al hardware y el antecedente técnico de despliegue manual con llama.cpp. Justificación cubre los cinco ángulos pedidos. |
| Descripción del problema | `chapters/02-descripcion-problema.tex` | under review | **1 / 1 pág.** | Cumple. Cubre el riesgo de monopolización incluyendo cargas de entrenamiento. Un `[verify: ADR-010]` esperando el árbol de problemas. |
| Objetivos | `chapters/04-objetivos.tex` | under review | **1 / 1 pág.** | Cumple. General reformulado a "Construir la plataforma". Los cuatro específicos con un solo verbo, sin fechas ni marcadores. |
| Marco teórico | `chapters/05-marco-teorico.tex` | under review | **4 / 4 pág.** | **Redactado 2026-09-12.** Siete secciones; cada una cierra relacionándose con su objetivo específico, como exige el formato. 30 claves citadas, todas 2015 o posterior. |
| Estado del arte | `chapters/06-estado-del-arte.tex` | not started | máx. 4 pág. | **Único capítulo del cuerpo sin redactar.** El material ya está investigado y espera en el dossier del scratchpad de la sesión: plataformas MLOps en nube, clústeres GPU de campus y LiteLLM como antecedente descartado, cada uno con su razón de no servir al caso IAsLab. |
| Metodología | `chapters/07-metodologia.tex` | under review | 6 pág. (sin límite) | Sin DSR. Enfoque iterativo tipo Scrum con sprints de dos semanas. Cronograma completo de ago-2026 a may-2027. Presupuesto y Esquema de trabajo eliminados por indicación del tutor. |
| Contribución y resultados | `chapters/08-contribucion-resultados.tex` | under review | **3 / 4 pág.** | Cumple. Trazabilidad objetivo → resultado → entregable alineada con los objetivos reescritos. |
| Anexos | `chapters/99-anexos.tex` | not started | — | Bloqueado por ADR-010: falta decidir si los árboles van en TikZ o como imagen. |
| Bibliografía | `references.bib` | drafted | — | 41 entradas. **Ninguna fuente anterior a 2015**: se retiraron `hevner-designscienceis-2004`, `peffers-dsrm-2007` y `brooke-sus-1996`; `yoo-slurm-2003` y `vavilapalli-yarn-2013` siguen en el archivo pero ya no se citan. |

## Verificaciones que pasa el documento hoy

Medido, no supuesto. Reproducible con los `grep` de `../skills/writting-tools/puntuation.md` §5.

- `make build` compila limpio: **cero** `Citation ... undefined`, **cero** `Reference ... undefined`, ningún `??` en el PDF.
- **Cero em dash (`—`)** en prosa renderizada, en los ocho capítulos y en `main.tex`. Es la regla 8 de `../CLAUDE.md` y el tutor la pidió tres veces.
- **Cero construcciones antitéticas** `no es X, es Y` y variantes.
- **Cero `\todo{}`**: los 18 comentarios del tutor están aplicados y borrados.
- **Cero menciones** a *Fair-Share*, *backlog heredado*, "lenguaje extenso" y *Design Science Research*.
- **Cero fuentes anteriores a 2015** citadas, conforme a `../skills/reference-writting/recency.md`.
- Cada capítulo dentro de su extensión máxima institucional.

## Dudas abiertas

Viven en [`../project-context/ADR.md`](../project-context/ADR.md), no aquí. **Queda una sola: ADR-010** (qué anexos se incluyen y si los árboles de problemas y objetivos se dibujan en TikZ o se insertan como imagen). Todo lo demás se respondió y se aplicó.

## Decisiones estructurales vigentes

- **2026-09-06 — El documento sigue la estructura de ANTEPROYECTO** de `../project-context/formato-anteproyecto.md`, no la de tesis final de `../skills/thesis-writing/structure.md`. Por eso no hay capítulos de Resultados, Discusión ni Conclusiones.
- **2026-09-12 — El capítulo "Hipótesis y restricciones" queda eliminado.** Decisión de los autores. El tutor no la objetó cuando se le preguntó de dónde salía el capítulo («si los piden pues los piden, yo no tengo problema»), así que la eliminación se sostiene como desviación deliberada del formato, no como olvido. El numerado de archivos salta de 02 a 04 a propósito; el número de capítulo en el PDF lo genera `\chapter`, no el nombre del archivo.
- **2026-09-12 — El proyecto CONSTRUYE la plataforma, no extiende un sistema previo.** Corrección del tutor el 09-09 y confirmación de los autores en ADR-027: no existe ninguna interfaz previa del IAsLab con la que integrarse; lo único preexistente es SAAMFI, y solo como proveedor de identidad. Aplicado en `documentation.md`, en el objetivo general y en los capítulos 01, 02, 07 y 08. **Ningún agente futuro debe reintroducir el verbo "extender".**
- **2026-09-12 — Título del proyecto: IAsLab ORCHID**, plataforma de orquestación y gobernanza de cargas de IA/ML en la infraestructura de la Universidad Icesi (ADR-001).
- **2026-09-12 — Se elimina el principio de "Fair-Share".** El modelo es **reserva de cupos con prioridad por rol**: estudiantes y profesores reservan, y los profesores tienen prioridad para reclamar recursos y para controlar el reparto de la capacidad de la sala. Aplicado en todo el documento y en `project-context/`.
- **2026-09-12 — Se retira *Design Science Research*.** El tutor lo pidió (ADR-016). La metodología describe el proceso real: enfoque iterativo tipo Scrum, sprints de dos semanas.
- **2026-09-12 — El alcance cubre cargas de entrenamiento en gobernanza y telemetría.** El entrenamiento en sí sigue fuera (lo cubre el proyecto hermano), pero las cuotas y la observabilidad no pueden ser ciegas a esas cargas. El mecanismo de distinción es **por punto de envío**, no por heurística: lo que entra por el control plane de entrenamiento es entrenamiento (FR-02.6, FR-03.5, ADR-020 cerrada).
- **2026-09-12 — La cuantización queda fuera como capacidad construida.** La plataforma despliega modelos ya cuantizados o se apoya en la que aplique el motor al cargar (ADR-021). Las citas de cuantización sostienen por qué esos modelos caben en 24 GB, no qué construye el proyecto.
- **2026-09-12 — LiteLLM no se adopta como AI Gateway** (ADR-024). Pasa a estado del arte. **Hallazgo del Investigador que conviene tener presente:** no existe literatura ni producto maduro que imponga cuotas sobre cargas LLM y no-LLM de forma unificada, así que esa capa probablemente hay que construirla.
- **2026-09-12 — Modelo de roles: los que provea SAAMFI, más un rol administrador de plataforma** (ADR-022). Se retira la enumeración de cinco roles académicos.
- **2026-09-12 — Regla de vigencia de fuentes:** ninguna cita externa puede tener más de 11 años. Regla en [`../skills/reference-writting/recency.md`](../skills/reference-writting/recency.md).
- **2026-09-12 — Reglas de redacción de objetivos propias del proyecto**, adoptadas tras la revisión del tutor (ADR-028): [`../skills/objectives-writting/objectives-project-rules.md`](../skills/objectives-writting/objectives-project-rules.md).
- **Los nombres de los autores van en orden ALFABÉTICO en el PDF compilado, no por rol.** Ya aplicado: De La Pava, Melo, Pacheco.

## Lo que sigue

1. **Redactar el Estado del arte** (cap. 06), el único capítulo del cuerpo que falta. La investigación ya está hecha.
2. **Resolver ADR-010** y construir los anexos.
3. **Resumen y Abstract**, que por indicación del formato se escriben al final.
4. Una pasada del **Revisor** sobre el documento completo antes de entregarlo.

## How to update this file

- Change a row's status the moment work on it actually changes state — don't batch updates.
- `drafted` → the Redactor has written prose and it compiles (`make build`).
- `under review` → the Revisor is actively checking it (`../skills/agent-roles/Revisor.md`).
- `approved` → the Revisor signed off; only the Coordinador reopens an approved section.
- Use Notes for what a future session needs at a glance (a blocking gap, a pending decision), not a changelog; git history already has that.
