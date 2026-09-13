# Thesis Status

Single source of truth for what stage each section is at. The **Coordinador** (see `../skills/agent-roles/Coordinador.md`) keeps this updated — check here before starting work instead of opening every chapter file.

Status values: `not started` · `drafted` · `under review` · `approved`.

> **Segunda versión, 2026-09-12.** Esta tabla refleja la segunda pasada completa sobre el documento: se aplicaron los 18 comentarios `\todo{}` del tutor (commit `fb9ee6b`), se cerraron 17 entradas de `ADR.md`, se redactó el Marco teórico y se ajustó cada capítulo a la extensión máxima del formato. Extensiones medidas sobre el PDF compilado (`make build`, 31 páginas), no estimadas.

| Sección | Archivo | Estado | Extensión | Notas |
| :--- | :--- | :--- | :--- | :--- |
| Resumen | `main.tex` (front matter) | not started | máx. 1 pág. | Se escribe al final, con 4-6 palabras clave y sin citas. |
| Abstract | `main.tex` (front matter) | not started | máx. 1 párr. | Se escribe al final, junto con el Resumen. |
| Lista de acrónimos | `main.tex` (front matter) | drafted | — | 12 siglas. AWQ y GPTQ salieron el 2026-09-12 al dejar de usarse en el cap. 08. **SSO y SUS siguen listadas sin aparecer en la prosa** (el texto escribe *System Usability Scale* completo): falta decidir si se usan o se retiran. SAAMFI salió de aquí: es nombre propio, no sigla (autores, 2026-09-12), y pasó al Glosario. |
| Glosario de términos | `main.tex` (front matter) | drafted | — | Contiene SAAMFI. Ampliable con más términos de dominio si el Revisor lo ve necesario. |
| Motivación y antecedentes | `chapters/01-motivacion-antecedentes.tex` | under review | **3 / 3 pág.** | Cumple. Incorpora el antecedente institucional de acceso al hardware y el antecedente técnico de despliegue manual con llama.cpp. Justificación cubre los cinco ángulos pedidos. **Contexto reorganizado el 2026-09-13 en embudo (MLOps, cómputo escaso, GPU compartidas, IAsLab y macroproyecto, este proyecto, involucrados), con Sevilla et al. (2022) y Ahmed et al. (2023) añadidos y el propósito del macroproyecto tomado del anteproyecto TRAINI. Antes, en la misma fecha:** sus cuatro citas (Sculley, Kreuzberger, Eken, Gao) verificadas contra el texto completo; Lima et al. (2022) salió por ser una afirmación del estado del campo de 2022 y registradas en `CITAS-VERIFICADAS.md`; **Antecedentes revisados el 2026-09-13 y aprobados por los autores:** sin detalle de bitácora, sin dos puntos, sin la frase de equidad económica (S1). La evidencia de hiperescala (Jeon, Gu, Weng, Liu) se reemplazó por fuentes académicas verificadas (Xu et al., 2025; Weitzel et al., 2025). **Justificación revisada el 2026-09-13:** flujo sin rótulos (pertinencia, acceso y retorno de inversión, efecto ambiental con Xu et al. 2025, relevancia por el escenario académico). Salen el párrafo de cuantización (Frantar, Lin, Dettmers) y el de manejo de datos (Wiest). Sin dos puntos. **El capítulo 01 queda revisado completo.** La frase de cierre ya no resume el aporte como «técnicas de despliegue de LLM» (2026-09-12), porque la plataforma gobierna cualquier carga de IA/ML (`requirements.md` FR-01.4, ADR-024). |
| Descripción del problema | `chapters/02-descripcion-problema.tex` | under review | **1 / 1 pág.** | Cumple. Cubre el riesgo de monopolización incluyendo cargas de entrenamiento. Un `[verify: ADR-010]` esperando el árbol de problemas. La pregunta del proyecto ya no habla de «inferencia distribuida», fuera de alcance según `requirements.md` §4 (2026-09-12). **Revisado por los autores el 2026-09-13:** 2.1 reescrita como árbol de problemas en prosa (problema central, síntomas, causa principal y secundarias, efectos por involucrado), sin nombrar la solución. En 2.2 cambia el enunciado previo a la pregunta, y la pregunta y la oración final se conservan por decisión de los autores. En la pregunta, «prioridad por rol» pasó a «reglas de reparto» (autores, 2026-09-13). Mantiene «observabilidad avanzada», pendiente de la revisión de objetivos. |
| Objetivos | `chapters/04-objetivos.tex` | under review | **1 / 1 pág.** | Cumple. General reformulado a "Construir la plataforma". Los cuatro específicos con un solo verbo, sin fechas ni marcadores. |
| Marco teórico | `chapters/05-marco-teorico.tex` | under review | **4 / 4 pág.** | **Redactado 2026-09-12.** Siete secciones; cada una cierra relacionándose con su objetivo específico, como exige el formato. 30 claves citadas, todas 2015 o posterior. |
| Estado del arte | `chapters/06-estado-del-arte.tex` | not started | máx. 4 pág. | **Único capítulo del cuerpo sin redactar.** **Candidatos ya verificados (2026-09-13), por decisión de los autores de no redactarlo todavía:** Jeon et al. (2019), Gu et al. (2019), Weng et al. (2022) y Liu et al. (2022), con sus pasajes en `CITAS-VERIFICADAS.md`. Descargado y sin verificar: George (2020, preprint). El material ya está investigado y espera en el dossier del scratchpad de la sesión: plataformas MLOps en nube, clústeres GPU de campus y LiteLLM como antecedente descartado, cada uno con su razón de no servir al caso IAsLab. |
| Metodología | `chapters/07-metodologia.tex` | under review | 6 pág. (sin límite) | Sin DSR. Enfoque iterativo tipo Scrum con sprints de dos semanas. Cronograma de ago-2026 a may-2027, **pendiente de replanificar** con el calendario real (PDG1 hasta los primeros días de diciembre, PDG2 de febrero a mayo; ADR-033). Presupuesto y Esquema de trabajo eliminados por indicación del tutor. **Marcadores abiertos (2026-09-13):** tres `% [verify: ADR-030]` sobre hechos que solo constan en actas, tres `% [verify: ADR-033]` en el cronograma y uno `% [verify: ADR-031]` en el *Sprint* 15. El riesgo de ancho de banda ya no llama «medida» a la capacidad de 10 Gbit/s, porque `requirements.md` §4 la registra como dato confirmado por los autores, sin medición. |
| Contribución y resultados | `chapters/08-contribucion-resultados.tex` | under review | **3 / 4 pág.** | Cumple. Trazabilidad objetivo → resultado → entregable alineada con los objetivos reescritos. llama.cpp figura como candidato preferente elegido por medición y ya no como motor comprometido (`requirements.md` FR-01.4, 2026-09-12). Las dos menciones al motor de *benchmarking* dependen de ADR-031. |
| Anexos | `chapters/99-anexos.tex` | not started | — | Bloqueado por ADR-010: falta decidir si los árboles van en TikZ o como imagen. |
| Bibliografía | `references.bib` | drafted | — | 42 entradas (Eken et al. 2026 añadida el 2026-09-13). Cada una mapeada a su PDF en `../fuentes/INDEX.md`; hoy hay 5 PDF locales. **Ninguna fuente anterior a 2015**: se retiraron `hevner-designscienceis-2004`, `peffers-dsrm-2007` y `brooke-sus-1996`; `yoo-slurm-2003` y `vavilapalli-yarn-2013` siguen en el archivo pero ya no se citan. |

## Verificaciones que pasa el documento hoy

Medido, no supuesto. Reproducible con los `grep` de `../skills/writting-tools/puntuation.md` §5.

- `make build` compila limpio: **cero** `Citation ... undefined`, **cero** `Reference ... undefined`, ningún `??` en el PDF.
- **Cero em dash (`—`)** en prosa renderizada, en los ocho capítulos y en `main.tex`. Es la regla 8 de `../CLAUDE.md` y el tutor la pidió tres veces.
- **Cero construcciones antitéticas** `no es X, es Y` y variantes.
- **Cero `\todo{}`**: los 18 comentarios del tutor están aplicados y borrados.
- **Cero menciones** a *Fair-Share*, *backlog heredado*, "lenguaje extenso" y *Design Science Research*.
- **Cero fuentes anteriores a 2015** citadas, conforme a `../skills/reference-writting/recency.md`.
- Cada capítulo dentro de su extensión máxima institucional.
- **Fidelidad de citas** (`../skills/reference-writting/source-fidelity.md`): verificadas contra el texto completo solo las citas de la sección *Contexto* del cap. 01 (2026-09-13). El resto del documento está **sin verificar**; `CITAS-VERIFICADAS.md` ya registra dos usos sin respaldo en el cap. 05.
- **Ortografía RAE** (`../skills/writting-tools/ortografia-rae.md` §4): cero prefijos con guion sobre base univerbal (*macroproyecto*, *precuantizados*), cero calcos registrados (*de grano fino*, *granular*, *servido*, *huella*, *arnés*) y extranjerismos crudos en cursiva. Verificado 2026-09-12.

## Dudas abiertas

Viven en [`../project-context/ADR.md`](../project-context/ADR.md), no aquí. **Quedan seis** (al 2026-09-13):

- **ADR-010**: qué anexos se incluyen y si los árboles de problemas y objetivos se dibujan en TikZ o se insertan como imagen.
- **ADR-029**: si la prioridad de reserva por curso académico (`requirements.md` FR-02.2) sigue siendo requisito después de que el tutor dejara fuera las cuotas por curso y horario el 2026-09-09. No toca la tesis hoy.
- **ADR-030**: si los hechos de reunión que el cap. 07 todavía afirma sin respaldo (Jira y Bitbucket; rango de 90 % a 95 % y fuente de poder; advertencia del tutor y compromiso GitOps) se escriben en `project-context/` o se retiran. Tres marcadores `% [verify: ADR-030: ...]` en `chapters/07-metodologia.tex`. El 2026-09-13 los autores promovieron los *sprints* 1 y 2, el calendario de PDG1 y PDG2 y el uso compartido con las clases.
- **ADR-031**: si el motor de *benchmarking* lo construye el proyecto o se reutiliza el harness del laboratorio. Un marcador en la fila *Sprint* 15 de `tab:cronograma`.
- **ADR-032**: dónde cae la línea de corte de la escalera de alcance [`../project-context/alcance-moscow.md`](../project-context/alcance-moscow.md). La proponen los autores y la decide el tutor. Puede cambiar los cuatro objetivos específicos.
- **ADR-033**: cómo se reparten las fases entre PDG1 (hasta los primeros días de diciembre de 2026) y PDG2 (febrero a mayo de 2027). Tres marcadores en `chapters/07-metodologia.tex`; depende de ADR-032.

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
- **2026-09-12 — Ortografía RAE y anglicismos en cursiva en lugar de calcos:** prefijos soldados a la base univerbal, extranjerismos crudos en cursiva según el DLE, y anglicismo en cursiva cuando la única traducción es un calco literal (*fine-grained* y no *de grano fino*). Los términos técnicos ya asentados en español se conservan. Regla y listas en [`../skills/writting-tools/ortografia-rae.md`](../skills/writting-tools/ortografia-rae.md).
- **2026-09-13 — No se aplican las extensiones máximas del formato de la facultad.** Decisión de los autores («no quiero que nos limitemos por páginas»), después de comparar con el anteproyecto terminado del proyecto de grado anterior (TRAINI, mismo tutor), que no las respeta. La columna *Extensión* de la tabla queda como dato informativo, no como límite.
- **Los nombres de los autores van en orden ALFABÉTICO en el PDF compilado, no por rol.** Ya aplicado: De La Pava, Melo, Pacheco.

## Lo que sigue

1. **Redactar el Estado del arte** (cap. 06), el único capítulo del cuerpo que falta. La investigación ya está hecha.
2. **Resolver ADR-010** y construir los anexos.
3. **Fijar la línea de corte del alcance con el tutor (ADR-032)** usando `../project-context/alcance-moscow.md`. Cierra con ella ADR-029 y ADR-031, y desbloquea la replanificación del cronograma (ADR-033) y la posible reescritura de objetivos.
4. **Terminar la promoción de hechos de las actas** del 2026-09-04 y del 2026-09-09 (cierra ADR-030). La del 2026-08-26 quedó revisada el 2026-09-13.
5. **Resumen y Abstract**, que por indicación del formato se escriben al final.
6. Una pasada del **Revisor** sobre el documento completo antes de entregarlo.

## How to update this file

- Change a row's status the moment work on it actually changes state — don't batch updates.
- `drafted` → the Redactor has written prose and it compiles (`make build`).
- `under review` → the Revisor is actively checking it (`../skills/agent-roles/Revisor.md`).
- `approved` → the Revisor signed off; only the Coordinador reopens an approved section.
- Use Notes for what a future session needs at a glance (a blocking gap, a pending decision), not a changelog; git history already has that.
