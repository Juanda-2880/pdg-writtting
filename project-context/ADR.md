# ADR — Registro de dudas abiertas (Agenda de Decisiones y Resoluciones)

Este archivo es la **lista única de dudas sin resolver del documento**: los vacíos que ningún agente puede llenar por sí mismo porque dependen de una decisión de los autores, del tutor o del laboratorio.

La regla 6 de [`../CLAUDE.md`](../CLAUDE.md) prohíbe inventar hechos, requisitos, datos técnicos o citas. Cuando un agente choca con un vacío así, marca el punto en el texto y **abre una entrada aquí** en vez de rellenarlo con algo verosímil. Este archivo existe para que, cuando la respuesta llegue, el agente que la aplique **no tenga que leer el documento entero para encontrar dónde va**: la entrada ya le dice el archivo, la línea de anclaje y el texto literal que debe reemplazar.

> [!IMPORTANT]
> Este archivo es **efímero por diseño**. Una duda resuelta y aplicada al documento **se borra de aquí**; no se archiva ni se marca como "cerrada". El historial ya lo guarda git. Si el archivo queda vacío salvo por este encabezado, es la señal correcta de que no hay nada pendiente.

---

## Cómo usarlo

### Si eres un agente que **encuentra** una duda

1. **No la resuelvas inventando.** Si el dato no está en `documentation.md`, `requirements.md` o `technologies.md`, o no proviene de una fuente real verificable, es una duda.
2. **Marca el punto exacto en el documento** con un marcador rastreable que nombre la entrada:
   - En prosa LaTeX: `\emph{[verify: ADR-007 — criterio de aceptación operacional]}`
   - En comentario LaTeX: `% [verify: ADR-007 — criterio de aceptación operacional]`
   - Si lo que falta es una fuente y no un dato: `\citep{cite_needed}` **y además** una entrada aquí que diga qué afirmación quedó sin respaldo.
3. **Abre la entrada** al final de la sección "Dudas abiertas", usando el siguiente número de la secuencia (los números **no se reciclan**, aunque la entrada anterior se haya borrado).
4. Rellena **todos** los campos de la plantilla. El campo *Dónde se usa* es el que justifica la existencia de este archivo: sin él, aplicar la respuesta cuesta una lectura completa del documento.

### Si eres un agente que **recibe la respuesta** a una duda

1. Busca la entrada por su identificador: `grep -n "ADR-007" project-context/ADR.md`.
2. Lee **solo** los archivos que la entrada lista en *Dónde se usa*, y ve directo a la línea o etiqueta indicada: `grep -n "ADR-007" thesis/chapters/04-objetivos.tex`.
3. Aplica el cambio descrito en *Al resolver*, y elimina el marcador `[verify: ...]` del texto.
4. **Borra la entrada completa de este archivo**, en el mismo cambio.
5. Recompila (`cd thesis && make build`) y actualiza [`../thesis/STATUS.md`](../thesis/STATUS.md) si el estado de alguna sección cambió.

### Si eres el autor (humano) respondiendo dudas

Responde por número de entrada. Basta con algo como *"ADR-007: el criterio es un puntaje SUS ≥ 68 y latencia p95 por debajo de 2 s bajo 24 usuarios concurrentes"*; el agente sabe por la entrada dónde aplicarlo.

Responder **en una reunión** también vale, con una condición: que la respuesta quede registrada en un insight de [`meetings/`](./meetings/README.md) con su cita literal, generado por la skill [`meeting-insights/`](../skills/meeting-insights/README.md). Ese insight **no borra la entrada de aquí**: la marca como *pendiente de aplicar*. La entrada se borra cuando la respuesta ya está escrita en el documento, siguiendo los pasos de la sección anterior.

### Qué **no** va aquí

- Tareas de redacción pendientes (eso es `thesis/STATUS.md`).
- Decisiones estructurales ya tomadas (eso va en la sección de decisiones de `thesis/STATUS.md`).
- Secciones aún no escritas (el marcador `% [verify: not yet written]` de un capítulo vacío no es una duda).
- Preguntas que un agente puede responder leyendo `project-context/` — eso es pereza, no un vacío.

---

## Plantilla de entrada

```markdown
### ADR-NNN — <la duda, formulada como pregunta>

- **Estado:** abierta
- **Abierta por:** <rol> · <AAAA-MM-DD>
- **A quién corresponde:** <autores | tutor | administrador del laboratorio>
- **Dónde se usa:**
  - `<ruta/al/archivo>` — <ancla: etiqueta, sección o línea> · marcador literal: `<texto exacto a reemplazar>`
- **Contexto:** <por qué hace falta este dato y qué se rompe si se inventa>
- **Qué se necesita para cerrarla:** <la forma exacta de la respuesta: un número, un nombre, un sí/no>
- **Al resolver:** <qué escribir y dónde, en una frase>
```

---

## Dudas abiertas

### ADR-010 — ¿Qué anexos deben incluirse y quién elabora los árboles de problemas y objetivos?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/99-anexos.tex` — archivo completo
  - `thesis/chapters/02-descripcion-problema.tex` — final del capítulo · marcador literal: `% [verify: ADR-010: enlazar al árbol de problemas cuando exista en 99-anexos.tex]`
- **Contexto:** el formato exige como anexos el análisis de participación, el árbol de problemas y el árbol de objetivos. El capítulo 2 ya tiene identificadas causas y efectos jerarquizados, de modo que el árbol puede derivarse de ese texto; falta decidir si se dibuja en TikZ dentro del documento o se inserta como imagen en `thesis/imagenes/`.
- **Qué se necesita para cerrarla:** la decisión de formato (TikZ o imagen) y la confirmación de que los tres anexos son obligatorios en esta entrega.
- **Al resolver:** crear los anexos con sus `\label{}`, y sustituir el marcador del capítulo 2 por un `\cref{}` real al árbol de problemas.

### ADR-030 — ¿Se escriben en `project-context/` los hechos de reunión que la tesis ya afirma, o se retiran del texto?

- **Estado:** abierta
- **Abierta por:** Revisor · 2026-09-12
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — `\label{sec:estrategia-metodologica}`, segundo párrafo (Jira y Bitbucket) · marcador literal: `% [verify: ADR-030: Jira y Bitbucket salen del acta 2026-08-26 (Compromisos), no de project-context]`
  - `thesis/chapters/07-metodologia.tex` — `\item[Saturación de VRAM y congelamiento de nodos GPU]` (rango de 90 % a 95 % y fuente de poder) · marcador literal: `% [verify: ADR-030: rango 90-95 % y fuente de poder salen del acta 2026-09-04; FR-03.4 solo dice 90%+]`
  - `thesis/chapters/07-metodologia.tex` — `\item[Cambios de requisitos que obliguen a rehacer la infraestructura]` (advertencia del tutor y compromiso con GitOps) · marcador literal: `% [verify: ADR-030: advertencia del tutor y compromiso GitOps salen del acta 2026-09-09]`
  - `project-context/meetings/2026-08-26-tutor-arquitectura.md`, `2026-09-04-alejandro-elicitacion.md` y `2026-09-09-tutor-alcance-y-revision.md` — sección "Contradicciones", anotación «Hechos de esta reunión usados en la tesis sin respaldo en `project-context/`»
- **Avance (2026-09-13):** en la revisión del acta del 2026-08-26 los autores promovieron el contenido de los *sprints* 1 y 2 junto con la exigencia del curso (`project-context/README.md`, «Course requirement for PDG I»), el calendario de PDG I y PDG II (`project-context/README.md`, «Academic calendar», que corrige el corte a los primeros días de diciembre) y la restricción de uso compartido con las clases (`requirements.md` §4). Esos marcadores ya se borraron del cap. 07. El nuevo calendario abrió ADR-033.
- **Contexto:** la regla 9 de `CLAUDE.md` exige que un hecho dicho en una reunión entre a `project-context/` por mano humana antes de citarse en la tesis. Quedan tres pasajes del cap. 07 que afirman hechos que solo constan en las actas: el uso de Jira y Bitbucket [2026-08-26, 52:07, sección *Compromisos*]; el rango de 90 % a 95 % de uso de GPU y la fuente de poder como causa del congelamiento [2026-09-04, 22:18]; y la advertencia del tutor sobre necesidades futuras junto con el compromiso GitOps [2026-09-09, 32:51 y 39:50]. Ninguno parece falso; lo que falta es la fuente de hecho. Borrar los pasajes por cuenta propia también sería decidir por los autores.
- **Qué se necesita para cerrarla:** por cada uno de los tres pasajes, «promover» (el autor escribe el hecho en `documentation.md`, `requirements.md`, `technologies.md` o `project-context/README.md`) o «retirar». Los dos últimos se deciden al revisar las actas del 2026-09-04 y del 2026-09-09.
- **Al resolver:** para lo promovido, borrar su marcador `% [verify: ADR-030: ...]`; para lo retirado, reescribir la frase sin el hecho y borrar el marcador. El cap. 07 no tiene extensión máxima, así que el cambio no afecta los límites de página.

### ADR-031 — ¿El motor de *benchmarking* automatizado lo construye el proyecto, o se reutiliza el harness que ya tiene el laboratorio?

- **Estado:** abierta
- **Abierta por:** Revisor · 2026-09-12
- **A quién corresponde:** autores / tutor
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — `tab:cronograma`, fila *Sprint* 10 (cronograma rehecho por los autores el 2026-09-13) · texto literal: `Ejecución del motor de \emph{benchmarking} automatizado bajo carga de usuarios concurrentes` · marcador literal: `% [verify: ADR-031: diseño propio o reutilización del harness del laboratorio]`
  - `thesis/chapters/07-metodologia.tex` — `\label{sec:estrategia-metodologica}` («los resultados que genera el motor de \emph{benchmarking} automatizado») y fila «Evaluación empírica» de `tab:fases-desarrollo`
  - `thesis/chapters/08-contribucion-resultados.tex` — segundo párrafo de «Aportes relacionados con el desarrollo de capacidades del investigador» y fila `obj:evaluacion` de `tab:objetivos-entregables`
  - `project-context/requirements.md` — FR-04.1 a FR-04.3
  - `project-context/technologies.md` — §E.1 "Custom Python Benchmark Harness"
  - `project-context/documentation.md` — «Institutional antecedents» · texto literal: `the laboratory evaluated inference engines with its own benchmarking harness`
- **Contexto:** `documentation.md` registra que el laboratorio ya tiene un harness propio (un *script* de Python guiado por YAML que mide *tokens* por segundo y tiempo de respuesta). `requirements.md` FR-04.1 describe esa misma herramienta como requisito del proyecto, y el cap. 07 programa su «Diseño y ejecución» en el *Sprint* 15. En la reunión del 2026-09-04, Alejandro ofreció acceso al repositorio del harness y dejó para el tutor si entra en el alcance [17:58, 20:32]; ninguna acta ni decisión escrita lo resolvió después. Si se reutiliza, «Diseño» sobrestima el trabajo; si se construye, la tesis debería decir por qué no basta el existente.
- **Qué se necesita para cerrarla:** una de tres: (a) se reutiliza el harness del laboratorio y el proyecto solo lo adapta y ejecuta; (b) el proyecto construye uno propio; (c) el *benchmarking* automatizado queda fuera y la evaluación usa otra herramienta de carga.
- **Al resolver:** ajustar FR-04 y §E.1 al origen decidido, cambiar el verbo de la fila *Sprint* 15 si aplica, revisar las dos menciones del cap. 08 y borrar el marcador.


### ADR-032 — ¿Hasta qué fila de la escalera de alcance llega este PDG?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-13
- **A quién corresponde:** autores proponen · tutor decide
- **Dónde se usa:**
  - `project-context/requirements.md` — sección 2, las cuatro tablas por objetivo · y sección 4, viñeta ADR-032
  - `thesis/chapters/04-objetivos.tex` — los cuatro `\label{obj:...}`: cada objetivo debe comprometer solo filas por encima de la línea
  - `thesis/chapters/07-metodologia.tex` — `tab:fases-desarrollo` y `tab:cronograma` (ver ADR-033)
  - `thesis/chapters/08-contribucion-resultados.tex` — `tab:objetivos-entregables`
  - `project-context/requirements.md` — FR de las filas que queden fuera
- **Contexto:** el tutor pidió el 2026-09-09 ordenar los requerimientos con MoSCoW y que el equipo proponga hasta dónde llega, reservándose la decisión («ustedes me proponen hasta qué punto quieren llegar y yo les digo si hasta ahí o no», [55:28]). La escalera de 38 capacidades que vivía en `alcance-moscow.md` se refundió el 2026-09-20 en `requirements.md`, donde cada requerimiento va bajo el objetivo que lo compromete y con su prioridad. **Avance (2026-09-13):** los autores sacaron del documento el soporte a entrenamiento, y el 2026-09-20 pasó a `requirements.md` §3.1 como requerimiento sin compromiso. Siguen abiertas la prioridad de profesores (hoy ADR-034) y el *System Usability Scale*. Mientras no haya corte acordado, los objetivos del cap. 04 prometen capacidades que el tutor no ha confirmado.
- **Qué se necesita para cerrarla:** los requerimientos de `requirements.md` §2 que el tutor confirma como compromiso del PDG y los que pasan a §3 o a trabajo futuro.
- **Al resolver:** reescribir los objetivos afectados (y su espejo en `documentation.md`), marcar fuera de alcance los FR de las filas excluidas, cerrar ADR-029 y ADR-031 con la misma decisión y abrir el trabajo de ADR-033.

### ADR-033 — ¿Cómo se reparten las fases entre PDG1 y PDG2 con el calendario real?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-13
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — `\label{sec:cronograma}`, segundo párrafo · marcador literal: `% [verify: ADR-033: el sprint 4 termina el 13-dic, después del cierre de PDG1 (primeros días de diciembre), y el sprint 5 (11-31 ene) cae antes del inicio de PDG2 (febrero, project-context/README.md)]`
  - `thesis/chapters/07-metodologia.tex` — `tab:fases-desarrollo`, columna Duración
- **Contexto:** los autores fijaron el 2026-09-13 que PDG1 termina en los primeros días de diciembre de 2026 y PDG2 va de febrero a mayo de 2027 (`project-context/README.md`, «Academic calendar»). El cronograma actual se armó suponiendo PDG1 hasta finales de diciembre y PDG2 desde enero: los *sprints* 8 y 9 terminan el 13 de diciembre y los *sprints* 10 y 11 empiezan el 11 de enero, fuera de ambos cursos. Además, las fases salen de los objetivos actuales, que pueden cambiar con ADR-032. Replanificar antes de fijar el alcance obligaría a hacerlo dos veces.
- **Avance (2026-09-13):** JDLP rehízo el cronograma con *sprints* de tres semanas desde el 21 de septiembre, etapa previa del 10 de agosto al 20 de septiembre y orden clúster → telemetría → cuotas → plataforma → evaluación (`documentation.md`, «Execution-order decisions»). Con ese plan el *sprint* 4 (23 nov – 13 dic) termina después del cierre de PDG1 y el *sprint* 5 (11–31 ene) cae antes de PDG2, y el segundo párrafo del cronograma dice «PDG2, entre enero y mayo de 2027». Los tres marcadores anteriores se reemplazaron por uno solo.
- **Qué se necesita para cerrarla:** ADR-032 cerrada, y la decisión de si entre diciembre y febrero se trabaja o no (hoy ese periodo no pertenece a ningún curso).
- **Al resolver:** reconstruir `tab:fases-desarrollo` y `tab:cronograma` desde los requerimientos de `requirements.md` §2, ajustar el segundo párrafo de `\label{sec:cronograma}` y borrar el marcador.

### ADR-034 — ¿Es compromiso del PDG el nivel de prioridad profesor sobre estudiante, si el modelo de roles vigente solo tiene administrador y usuario?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-20
- **A quién corresponde:** autores / tutor
- **Dónde se usa:**
  - `project-context/requirements.md` — seccion 2 «Roles de usuario», nota final · marcador literal: `*[verify: ADR-034]*`
  - `project-context/requirements.md` — RF-2.3.2, columna de criterio de aceptación · marcador literal: `*[verify: ADR-034]*`
  - `thesis/chapters/04-objetivos.tex` — `\label{obj:gobernanza}` · texto literal: `con prioridad de los profesores sobre la asignación de la capacidad de la sala`
  - `thesis/chapters/07-metodologia.tex` — `tab:fases-desarrollo`, fila «Gobernanza de cuotas», y `tab:cronograma`, *Sprint* 6 · texto literal: `prioridad de los profesores sobre la capacidad de la sala`
  - `thesis/chapters/08-contribucion-resultados.tex` — primer párrafo de «Aportes relacionados con el objeto del proyecto» y fila `obj:gobernanza` de `tab:objetivos-entregables`
  - `project-context/requirements.md` — R2-22, columna de requerimiento · marcador literal: `*[verify: ADR-034]*`
- **Contexto:** los autores fijaron el 2026-09-20 que el modelo de roles es el que dejó el tutor el 2026-09-09, «administrador y usuario, de momento». Con dos roles no existe un nivel profesor/estudiante, de modo que RF-2.3.2 solo puede implementarse como un atributo de prioridad configurable. Pero el objetivo específico 2 del anteproyecto sí promete «prioridad de los profesores sobre la asignación de la capacidad de la sala», y los capítulos 07 y 08 lo repiten. O el objetivo se reescribe en términos de prioridad por rol, o se agrega el nivel profesor/estudiante al modelo de roles. Es la tensión que ADR-032 no resolvió.
- **Qué se necesita para cerrarla:** una de dos: (a) el PDG compromete el nivel profesor/estudiante y el modelo de roles pasa a tres; (b) el PDG compromete solo prioridad configurable entre los roles que provea SAAMFI, y el objetivo 2 se reescribe sin nombrar a los profesores.
- **Al resolver:** aplicar la opción elegida en R2-22 de `requirements.md`, borrar el marcador, y reescribir `obj:gobernanza` y sus ecos en los capítulos 07 y 08 si aplica.
