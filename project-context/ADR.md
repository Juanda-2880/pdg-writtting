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

### ADR-001 — ¿Cuál es el título oficial en español del proyecto de grado?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** tutor
- **Dónde se usa:**
  - `thesis/main.tex` — portada, bloque `\begin{titlepage}` · marcador literal: `% [verify: ADR-001 — confirm the exact official Spanish title with the tutor before`
- **Contexto:** el título actual es una traducción de trabajo derivada de `documentation.md`; el formato institucional exige que el título refleje proceso, objeto y ubicación, y debe coincidir con el registrado ante la facultad.
- **Qué se necesita para cerrarla:** la cadena exacta del título aprobado.
- **Al resolver:** reemplazar el texto del `\Huge \textbf{...}` de la portada y borrar el comentario `[verify:]`.

### ADR-004 — ¿Qué criterio cuantitativo define un nivel "satisfactorio" de aceptación operacional?

- **Estado:** abierta
- **Abierta por:** Redactor · 2026-09-06
- **A quién corresponde:** tutor
- **Dónde se usa:**
  - `thesis/chapters/04-objetivos.tex` — ítem con `\label{obj:evaluacion}` · marcador literal: `\emph{[verify: ADR-004 — criterio cuantitativo de aceptación operacional, no especificado en project-context/]}`
  - `thesis/chapters/07-metodologia.tex` — sección de estrategia metodológica, donde se describe la evaluación empírica
- **Contexto:** el objetivo 4 promete "niveles satisfactorios de aceptación operacional" sin definirlos. La hipótesis de `thesis/chapters/03-hipotesis-restricciones.tex` se declara falsable **contra este criterio**: sin él, la hipótesis no es contrastable.
- **Qué se necesita para cerrarla:** un umbral por cada dimensión evaluada — usabilidad (por ejemplo, puntaje SUS mínimo) y desempeño bajo carga (por ejemplo, latencia p95 y número de usuarios concurrentes soportados).
- **Al resolver:** sustituir el marcador en el objetivo 4 y explicitar los mismos umbrales en la metodología, para que ambos capítulos digan lo mismo.

### ADR-008 — ¿Cuáles son las fechas de inicio y fin del proyecto y la duración de cada fase?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** autores / tutor
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — secciones "Fases de desarrollo del proyecto" (duraciones) y "Cronograma" (marcadores literales: `% [verify: ADR-008 — duración de cada fase, depende del cronograma]` y `% [verify: ADR-008 — CRONOGRAMA: diagrama de Gantt pendiente; requiere fechas de inicio/fin del PDG]`)
- **Contexto:** el formato exige un diagrama de Gantt con actividades derivadas de los objetivos específicos, y exige además asignar una duración a cada fase de la metodología. El objetivo general se declaró alcanzable en unos ocho meses, pero no hay fechas calendario en `project-context/`.
- **Qué se necesita para cerrarla:** fecha de inicio, fecha de entrega y, si ya existe, el reparto de semanas por fase.
- **Al resolver:** añadir la duración a la tabla de fases y construir el cronograma; las fases ya están mapeadas a los objetivos específicos, así que las actividades se derivan de ahí.



### ADR-010 — ¿Qué anexos deben incluirse y quién elabora los árboles de problemas y objetivos?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/99-anexos.tex` — archivo completo
  - `thesis/chapters/02-descripcion-problema.tex` — final del capítulo · marcador literal: `% [verify: ADR-010 — enlazar al árbol de problemas cuando exista en 99-anexos.tex]`
- **Contexto:** el formato exige como anexos el análisis de participación, el árbol de problemas y el árbol de objetivos. El capítulo 2 ya tiene identificadas causas y efectos jerarquizados, de modo que el árbol puede derivarse de ese texto; falta decidir si se dibuja en TikZ dentro del documento o se inserta como imagen en `thesis/imagenes/`.
- **Qué se necesita para cerrarla:** la decisión de formato (TikZ o imagen) y la confirmación de que los tres anexos son obligatorios en esta entrega.
- **Al resolver:** crear los anexos con sus `\label{}`, y sustituir el marcador del capítulo 2 por un `\cref{}` real al árbol de problemas.

### ADR-011 — ¿Cuál es la expansión oficial de la sigla SAAMFI?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** tutor / administrador del laboratorio
- **Dónde se usa:**
  - `thesis/main.tex` — front matter, "Lista de acrónimos" · marcador literal: `% [verify: ADR-011 — expansión oficial de la sigla SAAMFI]`
- **Contexto:** SAAMFI aparece diez veces en el documento y es central para la gobernanza de cuotas por rol, pero `project-context/` solo lo describe por su función ("institutional security mechanism for identity management"), nunca deletrea la sigla. El formato institucional exige que toda sigla se defina; inventar una expansión plausible sería exactamente lo que prohíbe la regla 6.
- **Qué se necesita para cerrarla:** las palabras exactas que componen la sigla.
- **Al resolver:** completar la entrada de la lista de acrónimos y borrar el marcador.

### ADR-012 — ¿Qué departamento corresponde al programa de Ingeniería Telemática?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** autores (consultando el programa)
- **Dónde se usa:**
  - `thesis/main.tex` — portada · marcador literal: `% [verify: ADR-012 — departamento que corresponde al programa de Ingeniería Telemática]`
- **Contexto:** la portada dice "Departamento de Computación y Sistemas Inteligentes", que se escribió cuando se creía que el título era en Ingeniería de Sistemas. Confirmado que el programa es Ingeniería Telemática (ver la tabla de autores en `project-context/README.md`), ese departamento puede ya no ser el correcto. No se cambia por cuenta propia porque el nombre del departamento no consta en `project-context/`.
- **Qué se necesita para cerrarla:** el nombre exacto del departamento al que adscribe el programa de Ingeniería Telemática, y si difiere del de Ingeniería de Sistemas (De La Pava se gradúa de ambos).
- **Al resolver:** ajustar la línea del departamento en la portada y borrar el marcador.

### ADR-013 — ¿Cuál es la capacidad real de VRAM de los nodos de cómputo del IAsLab?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** tutor / administrador del laboratorio
- **Dónde se usa:**
  - `thesis/chapters/01-motivacion-antecedentes.tex` — sección "Justificación", final del párrafo sobre servicio de LLM · marcador literal: `\todo{Creo que no son 16GB de VRAM..}`
  - `thesis/chapters/03-hipotesis-restricciones.tex` — sección "Restricciones" · ítem literal: `\item[Capacidad de VRAM limitada por nodo]`
  - `project-context/requirements.md` — "Target Accelerator Hardware" y "Model Size Constraints" (dos menciones a 16 GB)
  - `project-context/technologies.md` — apartado de cuantización · texto literal: `inside the 16 GB VRAM of each RTX 4080`
- **Contexto:** el tutor escribe *"Creo que no son 16GB de VRAM"*, contradiciendo a `requirements.md`, que afirma **NVIDIA GeForce RTX 4080 con 16 GB GDDR6X por nodo**. De esa cifra dependen el argumento de viabilidad del cap. 01 (que los LLM cuantizados caben en el hardware instalado), la restricción del cap. 03 y la justificación de cuantizar a 4/8 bits. Si el dato es falso, **la fuente de verdad está mal y hay que corregir `project-context/` antes que los capítulos**: parchear solo la prosa dejaría a los agentes futuros re-derivando la cifra equivocada.
- **Qué se necesita para cerrarla:** el modelo exacto de GPU y su VRAM por nodo de cómputo, y cuántos nodos hay de cada tipo si el parque es heterogéneo.
- **Al resolver:** corregir primero `requirements.md` y `technologies.md`; después actualizar la restricción del cap. 03 y la frase de viabilidad del cap. 01, y borrar el `\todo{}`.

### ADR-014 — ¿Cómo ha sido históricamente el acceso a los equipos y GPU del IAsLab?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** administrador del laboratorio / tutor
- **Dónde se usa:**
  - `thesis/chapters/01-motivacion-antecedentes.tex` — sección "Antecedentes del problema", antes del párrafo que empieza `El sistema web de la primera fase` · marcador literal: `\todo{INCORPORAR ANTECEDENTE INSTITUCIONAL DE ACCESO A LOS EQUIPOS:`
- **Contexto:** el tutor pide añadir el antecedente **institucional** que hoy falta: que el acceso a los equipos se concedía manualmente y solo a personal de confianza o investigadores principales; que la causa fue la ausencia de mecanismos automáticos de gobernanza, cuotas y aislamiento, siendo la restricción manual la única medida preventiva contra procesos descontrolados; y que eso produjo un cuello de botella administrativo, tiempos de espera, exclusión práctica de pregrado, semilleros y electivas, y subutilización del hardware. **Ninguno de estos hechos aparece en `project-context/`**: `documentation.md` describe el problema técnico de la primera fase, no la política de acceso. Redactarlos tomándolos del propio comentario del tutor sería inventar el hecho a partir de la pregunta, que es lo que prohíbe la regla 6 de `CLAUDE.md`.
- **Qué se necesita para cerrarla:** confirmación del laboratorio de ese relato, con el detalle que se pueda sostener: quién otorgaba el acceso, bajo qué criterio, y si existe alguna evidencia citable (actas, políticas internas, tiempos de espera registrados) o si debe presentarse como comunicación personal.
- **Al resolver:** añadir el hecho confirmado a `project-context/documentation.md`, redactar con él uno o dos párrafos en "Antecedentes del problema" y borrar el `\todo{}`.

### ADR-015 — El objetivo de gobernanza, ¿solo diseña el esquema de cuotas o también lo implementa?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/04-objetivos.tex` — ítem con `\label{obj:gobernanza}` · marcador literal: `\todo{Solo se va a diseñar o también desarrollar?}`
  - `thesis/chapters/07-metodologia.tex` — `\cref{tab:fases-desarrollo}`, fase correspondiente a este objetivo
  - `thesis/chapters/08-contribucion-resultados.tex` — sección "Resultados y entregables", entregable asociado
- **Contexto:** el objetivo empieza con *"Diseñar un esquema lógico de cuotas…"*, y el tutor pregunta si el compromiso llega hasta la implementación. Es una decisión de **alcance**, no de redacción: el formato advierte que los objetivos son los compromisos contra los que el evaluador mide el proyecto al final. `documentation.md` tampoco lo zanja. Cambiar el verbo por cuenta propia comprometería a los autores con trabajo que quizá no piensan hacer, o les restaría crédito por trabajo que sí harán.
- **Qué se necesita para cerrarla:** un sí/no a "¿el esquema de cuotas queda implementado y funcionando en el sistema al terminar el PDG?".
- **Al resolver:** ajustar el verbo del objetivo, y en el mismo cambio la fase de `tab:fases-desarrollo` y el entregable del cap. 08, para que los tres digan lo mismo.

### ADR-016 — ¿Se sostiene el marco metodológico DSR + Scrum, o se retira del documento?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — `\section{Estrategia metodológica}`, `\label{sec:estrategia-metodologica}` · marcador literal: `\todo{Tener cuidado con enmarcar el proyecto en metodologías`
- **Contexto:** el tutor advierte que mencionar una metodología implica que hay una labor real detrás de comprenderla y detallarla, y que si no se piensa aplicar es mejor no nombrarla. El capítulo hoy declara *Design Science Research* como paradigma de investigación (citando a Hevner) **y** Scrum como proceso de desarrollo (citando la Scrum Guide). Es comprometerse o borrar, y ambas opciones reescriben la sección entera: si se sostiene, hay que detallar cómo se aplican las guías de DSR y qué artefactos de Scrum se usan de verdad (sprints, backlog, ceremonias); si no, hay que reemplazar la sección por una descripción honesta del proceso real de trabajo.
- **Qué se necesita para cerrarla:** una de dos: (a) "sí, y trabajamos así: <sprints de N semanas, estas ceremonias, este backlog>", o (b) "no, quítalo".
- **Al resolver:** reescribir `sec:estrategia-metodologica` según la opción elegida, revisar que las fases de desarrollo sigan siendo coherentes con ella, y borrar el `\todo{}`.

### ADR-017 — ¿Existe la fase de estabilización del backlog heredado, y en qué orden van las fases?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — `\section{Fases de desarrollo del proyecto}`, `\label{sec:fases-desarrollo}` · marcador literal: `\todo{Dicen que habrá una fase de análisis y estabilización del backlog`
  - `thesis/chapters/07-metodologia.tex` — `\cref{tab:fases-desarrollo}` (el orden de las filas) y el riesgo `\item[Esfuerzo del backlog heredado mayor al previsto]`
  - `thesis/chapters/03-hipotesis-restricciones.tex` — restricción `\item[Base de código heredada]`
- **Contexto:** el tutor pregunta si esa fase de estabilización va a existir realmente y si el orden cronológico (observabilidad primero, luego orquestación y gobernanza) es el esperado. Además de la duda del tutor, hay una **contradicción dentro de `project-context/`**: `documentation.md` afirma en el planteamiento del problema que el software *requiere* estabilizarse resolviendo historias del backlog, y más adelante lista *"a stabilized codebase inherited from the training phase is available"* entre los **supuestos ya cumplidos**. Ningún agente puede decidir cuál de las dos versiones vale, y de ello dependen una fase entera, un riesgo y una restricción.
- **Qué se necesita para cerrarla:** confirmación de si la estabilización del backlog es trabajo del PDG (y con qué peso), y el orden definitivo de las fases.
- **Al resolver:** corregir la contradicción en `documentation.md`, reordenar `tab:fases-desarrollo` si aplica, ajustar el riesgo y la restricción, y borrar el `\todo{}`.

### ADR-018 — Las especificaciones de hardware, ¿van en "Restricciones" o en los anexos?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** autores / tutor
- **Dónde se usa:**
  - `thesis/chapters/03-hipotesis-restricciones.tex` — final de la sección "Restricciones" · marcador literal: `\todo{Revisar características de los computadores nuevamente`
  - `thesis/chapters/99-anexos.tex` — destino posible
- **Contexto:** el tutor pregunta si este apartado lo exige el formato del PDG y sugiere que quizá pertenece a los anexos. El formato **sí** contempla el capítulo "Hipótesis y restricciones", de modo que la sección no sobra; lo que está en duda es si el **detalle de hardware** (modelo de GPU, VRAM, límites de red) se queda en la restricción o se traslada a un anexo con la restricción reducida a una frase. Depende de **ADR-010** (qué anexos se incluyen) y de **ADR-013**: no tiene sentido mover una tabla cuyas cifras están en disputa.
- **Qué se necesita para cerrarla:** la decisión de dónde vive el detalle, una vez cerradas ADR-010 y ADR-013.
- **Al resolver:** dejar la restricción como enunciado breve y, si se decide mover, crear el anexo con su `\label{}` y enlazarlo con `\cref{}`; borrar el `\todo{}`.
