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

Respuesta: El titulo del proyecto es IasLab ORCHID - Plataforma de orquestación y gobernanza de cargas de IA/ML en la infrastructura de la universidad ICESI.

### ADR-004 — ¿Qué criterio cuantitativo define un nivel "satisfactorio" de aceptación operacional?

- **Estado:** abierta
- **Abierta por:** Redactor · 2026-09-06
- **A quién corresponde:** tutor
- **Dónde se usa:**
  - `thesis/chapters/04-objetivos.tex` — ítem con `\label{obj:evaluacion}` · marcador literal: `\emph{[verify: ADR-004 — criterio cuantitativo de aceptación operacional, no especificado en project-context/]}`
  - `thesis/chapters/07-metodologia.tex` — sección de estrategia metodológica, donde se describe la evaluación empírica
- **Contexto:** el objetivo 4 promete "niveles satisfactorios de aceptación operacional" sin definirlos.
- **Qué se necesita para cerrarla:** un umbral por cada dimensión evaluada — usabilidad (por ejemplo, puntaje SUS mínimo) y desempeño bajo carga (por ejemplo, latencia p95 y número de usuarios concurrentes soportados).
- **Al resolver:** sustituir el marcador en el objetivo 4 y explicitar los mismos umbrales en la metodología, para que ambos capítulos digan lo mismo.

Respuesta: El sistema debe poder soportar 20 usuarios simultaneos utilizando la plataforma

### ADR-008 — ¿Cuáles son las fechas de inicio y fin del proyecto y la duración de cada fase?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** autores / tutor
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — secciones "Fases de desarrollo del proyecto" (duraciones) y "Cronograma" (marcadores literales: `% [verify: ADR-008 — duración de cada fase, depende del cronograma]` y `% [verify: ADR-008 — CRONOGRAMA: diagrama de Gantt pendiente; requiere fechas de inicio/fin del PDG]`)
- **Contexto:** el formato exige un diagrama de Gantt con actividades derivadas de los objetivos específicos, y exige además asignar una duración a cada fase de la metodología. El objetivo general se declaró alcanzable en unos ocho meses, pero no hay fechas calendario en `project-context/`. La reunión del 2026-09-09 aportó dos hitos puntuales — entrega al profesor Navarro el **lunes 2026-09-14**, y marco teórico + estado del arte el fin de semana previo (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`) — pero siguen faltando la fecha de inicio, la fecha de entrega final del PDG y el reparto de semanas por fase.
- **Qué se necesita para cerrarla:** fecha de inicio, fecha de entrega final, y el reparto de semanas por fase.
- **Al resolver:** añadir la duración a la tabla de fases y construir el cronograma; las fases ya están mapeadas a los objetivos específicos, así que las actividades se derivan de ahí.

Respuesta: El inicio del proyecto fue el 10 de agosto 2026 y se termina en Mayo del 2027



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
- **Contexto:** SAAMFI aparece diez veces en el documento y es central para la gobernanza de cuotas por rol, pero `project-context/` solo lo describe por su función ("institutional security mechanism for identity management"), nunca deletrea la sigla. El formato institucional exige que toda sigla se defina; inventar una expansión plausible sería exactamente lo que prohíbe la regla 6. La reunión del 2026-09-09 aclaró la **función** sin resolver la **sigla**: SAAMFI es únicamente un proveedor de identidad (Identity Provider, comparable a Auth0/Keycloak) — «solamente va a funcionar como un Identity Provider y ya está», confirmado por el tutor con «Exactamente» (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`, [18:30]-[18:39]). Tres reuniones seguidas sin obtener las palabras exactas de la sigla.
- **Qué se necesita para cerrarla:** las palabras exactas que componen la sigla.
- **Al resolver:** completar la entrada de la lista de acrónimos y borrar el marcador.

Respuesta: La solucion a este ADR ya se encuentra en meetings y se puede usar esa repuesta

### ADR-012 — ¿Qué departamento corresponde al programa de Ingeniería Telemática?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-06
- **A quién corresponde:** autores (consultando el programa)
- **Dónde se usa:**
  - `thesis/main.tex` — portada · marcador literal: `% [verify: ADR-012 — departamento que corresponde al programa de Ingeniería Telemática]`
- **Contexto:** la portada dice "Departamento de Computación y Sistemas Inteligentes", que se escribió cuando se creía que el título era en Ingeniería de Sistemas. Confirmado que el programa es Ingeniería Telemática (ver la tabla de autores en `project-context/README.md`), ese departamento puede ya no ser el correcto. No se cambia por cuenta propia porque el nombre del departamento no consta en `project-context/`.
- **Qué se necesita para cerrarla:** el nombre exacto del departamento al que adscribe el programa de Ingeniería Telemática, y si difiere del de Ingeniería de Sistemas (De La Pava se gradúa de ambos).
- **Al resolver:** ajustar la línea del departamento en la portada y borrar el marcador.

responder: El departamento de ambas carreras es la falcutad barberi de Ingenieria, Dise;o y Ciencias aplicadas

### ADR-014 — ¿Cómo ha sido históricamente el acceso a los equipos y GPU del IAsLab?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** administrador del laboratorio / tutor
- **Dónde se usa:**
  - `thesis/chapters/01-motivacion-antecedentes.tex` — sección "Antecedentes del problema", antes del párrafo que empieza `El sistema web de la primera fase` · marcador literal: `\todo{INCORPORAR ANTECEDENTE INSTITUCIONAL DE ACCESO A LOS EQUIPOS:`
- **Contexto:** el tutor pide añadir el antecedente **institucional** que hoy falta: que el acceso a los equipos se concedía manualmente y solo a personal de confianza o investigadores principales; que la causa fue la ausencia de mecanismos automáticos de gobernanza, cuotas y aislamiento, siendo la restricción manual la única medida preventiva contra procesos descontrolados; y que eso produjo un cuello de botella administrativo, tiempos de espera, exclusión práctica de pregrado, semilleros y electivas, y subutilización del hardware. **Ninguno de estos hechos aparece en `project-context/`**: `documentation.md` describe el problema técnico de la primera fase, no la política de acceso. Redactarlos tomándolos del propio comentario del tutor sería inventar el hecho a partir de la pregunta, que es lo que prohíbe la regla 6 de `CLAUDE.md`.
- **Qué se necesita para cerrarla:** confirmación del laboratorio de ese relato, con el detalle que se pueda sostener: quién otorgaba el acceso, bajo qué criterio, y si existe alguna evidencia citable (actas, políticas internas, tiempos de espera registrados) o si debe presentarse como comunicación personal. La reunión del 2026-09-09 no la respondió, pero nombró la vía para cerrarla: la profesora **Ángela Villota** conoce la historia del IAsLab y los autores ya se comprometieron a entrevistarla (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`, compromiso sin fecha).
- **Al resolver:** añadir el hecho confirmado a `project-context/documentation.md`, redactar con él uno o dos párrafos en "Antecedentes del problema" y borrar el `\todo{}`.

Responder: Puedes utilizar el contexto de los meetings para responder esta seccion

### ADR-015 — El objetivo de gobernanza, ¿solo diseña el esquema de cuotas o también lo implementa?

- **Estado:** respondida, pendiente de aplicar — **implementa** (el tutor lo confirmó el 2026-09-09: *"ustedes van a hacer el sistema de cuotas"*, `project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`). No hace falta volver a preguntarla; falta aplicar el cambio y borrar esta entrada.
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/04-objetivos.tex` — ítem con `\label{obj:gobernanza}` · marcador literal: `\todo{Solo se va a diseñar o también desarrollar?}`
  - `thesis/chapters/07-metodologia.tex` — `\cref{tab:fases-desarrollo}`, fase correspondiente a este objetivo
  - `thesis/chapters/08-contribucion-resultados.tex` — sección "Resultados y entregables", entregable asociado
- **Contexto:** el objetivo empieza con *"Diseñar un esquema lógico de cuotas…"*, y el tutor pregunta si el compromiso llega hasta la implementación. Es una decisión de **alcance**, no de redacción: el formato advierte que los objetivos son los compromisos contra los que el evaluador mide el proyecto al final. `documentation.md` tampoco lo zanja. Cambiar el verbo por cuenta propia comprometería a los autores con trabajo que quizá no piensan hacer, o les restaría crédito por trabajo que sí harán.
- **Qué se necesita para cerrarla:** un sí/no a "¿el esquema de cuotas queda implementado y funcionando en el sistema al terminar el PDG?".
- **Al resolver:** ajustar el verbo del objetivo, y en el mismo cambio la fase de `tab:fases-desarrollo` y el entregable del cap. 08, para que los tres digan lo mismo.

Responder: El sistema de cuotas queda implementado y funcionando en el sistema al terminar el PDG, basicamente una aplicacion debe ser capaz de concectarse a este sistema y hacer uso de esto, no queda implementado ninguna aplicacion web o algo parecido pero si la configuracion den la plataforma

### ADR-016 — ¿Se sostiene el marco metodológico DSR + Scrum, o se retira del documento?

- **Estado:** respondida, pendiente de aplicar — **DSR se retira; queda Scrum o "enfoque iterativo"** (el tutor lo confirmó el 2026-09-09: *"¿cuál es su metodología? Scrum, ¿no? […] O enfoque iterativo, también puede llamarse así"*, `project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`). No hace falta volver a preguntarla; falta reescribir `sec:estrategia-metodologica` sin DSR (y revisar si la cita `hevner-designscienceis-2004` sigue teniendo función en el documento) y borrar esta entrada.
- **Abierta por:** Coordinador · 2026-09-09
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — `\section{Estrategia metodológica}`, `\label{sec:estrategia-metodologica}` · marcador literal: `\todo{Tener cuidado con enmarcar el proyecto en metodologías`
- **Contexto:** el tutor advierte que mencionar una metodología implica que hay una labor real detrás de comprenderla y detallarla, y que si no se piensa aplicar es mejor no nombrarla. El capítulo hoy declara *Design Science Research* como paradigma de investigación (citando a Hevner) **y** Scrum como proceso de desarrollo (citando la Scrum Guide). Es comprometerse o borrar, y ambas opciones reescriben la sección entera: si se sostiene, hay que detallar cómo se aplican las guías de DSR y qué artefactos de Scrum se usan de verdad (sprints, backlog, ceremonias); si no, hay que reemplazar la sección por una descripción honesta del proceso real de trabajo.
- **Qué se necesita para cerrarla:** una de dos: (a) "sí, y trabajamos así: <sprints de N semanas, estas ceremonias, este backlog>", o (b) "no, quítalo".
- **Al resolver:** reescribir `sec:estrategia-metodologica` según la opción elegida, revisar que las fases de desarrollo sigan siendo coherentes con ella, y borrar el `\todo{}`.

### ADR-019 — ¿En qué orden cronológico van las fases de desarrollo del proyecto?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/07-metodologia.tex` — `\section{Fases de desarrollo del proyecto}`, `\label{sec:fases-desarrollo}`, y `\cref{tab:fases-desarrollo}` (el orden de las filas) · marcador literal: `\todo{Dicen que habrá una fase de análisis y estabilización del backlog`
- **Contexto:** el `\todo{}` del tutor plantea dos preguntas distintas; esta entrada cubre solo la segunda — "¿primero se trabajará la observabilidad de infraestructura y luego la de orquestación y gobernanza?" — porque es una decisión de secuenciación genuina, sin respuesta en `project-context/`. La primera pregunta del mismo `\todo{}` ("¿habrá una fase de estabilización del backlog heredado?") **ya se resolvió**: no existe tal backlog heredado, este proyecto no es continuación directa de uno anterior — ver la nota en `project-context/documentation.md` y la fila "Metodología" de `thesis/STATUS.md`, que registra el trabajo de redacción pendiente para quitar esa fase de la prosa. La reunión del 2026-09-09 la deja **más abierta, no menos**: «las fases de desarrollo del proyecto están desorganizadas o realmente pueden cambiar un montón» y ahora depende del ejercicio de priorización MoSCoW que el tutor pidió sobre los requerimientos (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`, [55:28]) — no tiene sentido fijar el orden de fases antes de que ese ejercicio recorte el alcance.
- **Qué se necesita para cerrarla:** el orden definitivo de las fases restantes (observabilidad, gobernanza, orquestación, evaluación) — confirmar si es el orden actual o corregirlo.
- **Al resolver:** reordenar `tab:fases-desarrollo` si aplica, y borrar el `\todo{}` (junto con la fase de estabilización del backlog heredado, per la nota de `thesis/STATUS.md`).

Responder: define esto tu como agente en el documento, utiliza intervalos o sprints de 2 semanas para las implementaciones y cambios en el documento

### ADR-020 — ¿Cómo distingue el sistema de cuotas un trabajo de entrenamiento de una sesión de inferencia?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** autores / tutor
- **Dónde se usa:**
  - `project-context/requirements.md` — FR-02.6 (Training Workload Compatibility) y FR-03.5 (Workload-Agnostic Telemetry)
- **Contexto:** los autores confirmaron que el esquema de cuotas por reserva y la telemetría deben cubrir también las cargas de entrenamiento que corren sobre el mismo hardware (control plane del proyecto hermano del macro-proyecto), no solo la inferencia — eso ya quedó escrito como requisito. Lo que falta es el **mecanismo**: ¿el control plane de entrenamiento expone una API o una señal (etiqueta de proceso, namespace de Kubernetes, cgroup) que este sistema pueda leer para reconocer "esto es un job de entrenamiento"? ¿O se detecta indirectamente por patrón de consumo (VRAM sostenida sin tráfico de inferencia)? Sin esa respuesta, FR-02.6 y FR-03.5 son una intención correcta pero no una especificación implementable.
- **Qué se necesita para cerrarla:** cómo identifica el sistema, en la práctica, que un proceso en un nodo es un trabajo de entrenamiento y no una sesión de inferencia — vía integración con el control plane hermano, un contrato de metadatos, o una heurística de telemetría.
- **Al resolver:** añadir el mecanismo elegido como sub-punto de FR-02.6/FR-03.5 en `requirements.md`, y reflejarlo en `technologies.md` si implica un componente nuevo.

Responder: El control pane de entrenamiento se conecta a nuestra infrastructura y lso trabajos lanzados desde ahi se consideran como entrenamiento y los lanzados por nuestro control plane se consideran como despliegue, pero esto es gestionado internamente en el cluster, mira el marco teorico y las diferente

### ADR-021 — ¿La cuantización de modelos queda dentro o fuera del alcance del proyecto?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** tutor
- **Dónde se usa:**
  - `project-context/requirements.md` — FR-01.3 (Quantization Support) y "Model Size Constraints"
  - `project-context/technologies.md` — apartado "Quantization Technologies"
  - `thesis/chapters/01-motivacion-antecedentes.tex` — párrafo de "Justificación" que cita a `frantar-gptq-2023`, `lin-awq-2024` y `dettmers-llmint8-2022` para sostener que modelos grandes caben en los 24 GB de VRAM mediante cuantización
- **Contexto:** en la reunión del 2026-09-09, Melo reporta que Juan Carlos y Alejandro dijeron que **"la parte de cuantización y todo eso no iba a entrar, o sea, la disminución de los modelos no podíamos hacerlo"** [15:36], y el tutor no lo contradice (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`). Eso contradice directamente FR-01.3, que exige soporte de cuantización (AWQ/GPTQ/GGUF/bitsandbytes), y vacía de función a las tres citas del cap. 01: si la cuantización no es una capacidad del sistema, esas citas se vuelven exactamente lo que el tutor llama "citas forzadas". **Hay un matiz sin resolver dentro de la propia reunión**: "no podíamos hacerlo" puede significar *el equipo no lo va a implementar* o *el sistema no la necesita/usa*, y la diferencia importa — quizás el motor de inferencia (vLLM/llama.cpp) ya trae modelos pre-cuantizados de terceros y el proyecto solo los despliega, sin implementar el proceso de cuantizar. Ningún agente puede decidir cuál de las dos lecturas es la correcta.
- **Qué se necesita para cerrarla:** un sí/no explícito a "¿el sistema despliega modelos ya cuantizados por terceros (sin implementar cuantización), o la cuantización queda completamente fuera, incluido el despliegue de modelos pre-cuantizados?".
- **Al resolver:** si queda fuera del todo, retirar FR-01.3 de `requirements.md`, el apartado de `technologies.md`, y las tres citas forzadas del cap. 01 (ajustando el argumento de viabilidad sin ellas). Si solo se excluye *implementar* cuantización pero se permite *desplegar* modelos pre-cuantizados, 
reformular FR-01.3 en ese sentido y las citas se mantienen como referencia de por qué esos modelos existen, no de qué hace el proyecto.

Responder: El sistema despliega sobre un montor de inferencia, el cual a medida de pruebas se determinara cual es el mejor y si este soporta cuantizacion, yo como usuario tengo entendido que al yo seleccionar un modelo y desplegarlo en digamos llama.cpp ya se hace la cuantizacion, si es asi si. Si nos toca hacer un proceso adicional, entonces No vvamos a soportar la cuantizacion y los modelos ya tienen que venir asi

### ADR-022 — ¿Cuántos roles de gobernanza tiene el sistema: solo administrador/usuario, o el modelo académico de cuatro roles con prioridad de profesor?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** autores / tutor
- **Dónde se usa:**
  - `thesis/chapters/04-objetivos.tex` — `\label{obj:gobernanza}`, que promete cuotas "acoplado a los atributos de rol de SAAMFI (pregrado, electiva, semilleros y profesores)"
  - `project-context/requirements.md` — FR-02.4 (cuatro roles académicos) y el nuevo FR-02.7 (prioridad de profesor)
- **Contexto:** hay dos versiones distintas del modelo de roles y ninguna se ha retirado formalmente. La reunión del 2026-09-09 fija: **"roles iniciales: administrador y usuario común. Nada de pregrado, electiva o semilleros por ahora"** — la granularidad académica queda explícitamente fuera de alcance por ahora (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`, [22:48]). Pero el mismo día de esta sesión (2026-09-12), los autores confirmaron lo contrario para efectos de esta ADR: **"el sistema de cuotas es por reserva de los estudiantes o profesores, en donde los profesores tienen prioridad"** — lo que ya se escribió como FR-02.7. Estas dos fuentes no dicen lo mismo: una reduce los roles a dos (administrador/usuario), la otra distingue al menos estudiante/profesor con prioridad de rol. No se puede aplicar FR-02.7 con confianza sin saber si esa distinción de rol sigue vigente después del recorte de alcance del 09-09.
- **Qué se necesita para cerrarla:** confirmación de si el recorte de roles del 09-09 sigue vigente, y si FR-02.7 (prioridad de profesor) se sostiene dentro de ese recorte o lo reemplaza.
- **Al resolver:** unificar FR-02.4 y FR-02.7 en `requirements.md` con el modelo de roles definitivo, y ajustar `obj:gobernanza` en el cap. 04 para que no prometa una granularidad de roles que el sistema no vaya a tener.

Responder: VVamos a seguir los roles de SAAMFI en donde estos son los usuarios con diferentes permisos. Y aparte hay un rol adminsitrado quien es el que gestiona la plataforma

### ADR-023 — ¿Cuál es el ancho de banda de red disponible y el requerido para el proyecto?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** tutor / administrador del laboratorio
- **Dónde se usa:**
  - `project-context/requirements.md` — no hay hoy ninguna cifra de red; esta ADR es la fuente para añadirla si se decide incluirla
- **Contexto:** la reunión del 2026-08-26 reporta que Alejandro pidió switches de **"al menos 25 gigas por segundo"**; la del 2026-09-04 dice que la red interna actual **"no es lo suficientemente rápida"** sin dar cifra; y la del 2026-09-09 el tutor da **10 Gbit/s** como la velocidad actual y menciona que **"para modelos creo que se necesitan como 200 gigabits"** para una buena tasa de tokens (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`, [16:02]). Tres cifras (10, 25, 200 Gbit/s) para dos preguntas distintas (capacidad actual vs. requerida) y ninguna con fuente escrita.
- **Qué se necesita para cerrarla:** la velocidad real medida de la red interna del laboratorio, y si el proyecto realmente necesita una cifra objetivo de ancho de banda (dado que la inferencia distribuida por red ya quedó fuera de alcance el 09-04/09-09).
- **Al resolver:** añadir la cifra confirmada a `project-context/requirements.md` (sección de restricciones de red), citando la fuente (medición directa, no otro testimonio).

Responder: El ancho de banda actualmente en la sala 103 M de la facultad es de 10 Gbit/s, y el proyecto no requiere más que eso, ya que no se va a hacer inferencia distribuida

### ADR-024 — ¿El AI Gateway se construye a la medida, o se usa LiteLLM ya desplegado en el laboratorio?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** tutor / administrador del laboratorio
- **Dónde se usa:**
  - `project-context/technologies.md` — "LiteLLM Proxy", descrito como si ya fuera la solución elegida
  - `project-context/requirements.md` — FR-01.4 (Inference Engine Abstraction), que asume LiteLLM Proxy como el gateway
- **Contexto:** el tutor dijo el 2026-08-26 **"no tengamos que usar LightLLM [LiteLLM], toca hacer el LightLLM pero puramente enfocado a cualquier AI Gateway"** — es decir, construirlo a la medida. La reunión del 2026-09-04 con Alejandro dice lo contrario: **"por ahí también estaba como el proxy que estamos usando también, que se llama Light LLM"** — ya está en uso en el laboratorio. La reunión del 2026-09-09 deja la pregunta explícitamente abierta en su propia lista de pendientes: **"¿Qué tecnología para el AI Gateway?"**, sin resolverla (`project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`). Es una contradicción entre el tutor y el laboratorio, no un vacío de `project-context/`, y decide si el trabajo de gobernanza es integración sobre algo ya desplegado o desarrollo desde cero.
- **Qué se necesita para cerrarla:** confirmación de si LiteLLM Proxy, ya desplegado, se adopta como el AI Gateway del proyecto, o si se construye una capa propia.
- **Al resolver:** ajustar FR-01.4 y el apartado de LiteLLM en `technologies.md` para que reflejen la decisión, y actualizar el esfuerzo estimado de la fase de orquestación en `07-metodologia.tex` en consecuencia.

Responder: No se va a utilizar LitleLLm ya que tambien tenemos que soportar LM, pero el sistema de cuotas si se encuentra algo chevere en el marco teorico sobre tecnologias entonces se implementa eso, si no tendremos que crearlo a mano

### ADR-026 — ¿Qué otros puntos de vista, además del académico, debe cubrir la justificación del capítulo 1?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/01-motivacion-antecedentes.tex` — sección "Justificación" · marcador literal: `\todo{Revisar desde qué más puntos de vista se requiren especificar dentro del documento, se observa principalmente el impacto académico.}`
- **Contexto:** el tutor observa que la justificación hoy argumenta casi solo el impacto académico (proyectos de investigación, privacidad de datos), sin cubrir explícitamente otros ángulos que el formato de anteproyecto suele esperar — económico/institucional (ya hay algo: retorno de inversión en hardware), social/equidad (acceso disparejo por capacidad de pago), o de la propia operación del laboratorio. No especifica cuáles faltan, así que no se puede adivinar sin inventar contenido.
- **Qué se necesita para cerrarla:** una lista de los puntos de vista adicionales que el tutor espera ver (ej. social, económico, operativo, de política institucional), o su confirmación de que los ya presentes (académico, privacidad, económico) son suficientes.
- **Al resolver:** añadir los párrafos correspondientes a la Justificación y borrar el `\todo{}`.

Responder: economico, operativo, manejo de datos, acceso a la IA para los miembros de la universidad y ayuda en el academico a los investigadores

### ADR-027 — ¿Cuál es "la interfaz del IAsLab" en la que se integra el motor de orquestación de inferencia?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/04-objetivos.tex` — `\label{obj:orquestacion}` · marcador literal: `\todo{Cuál es esa interfaz del IASLab?}`
- **Contexto:** el objetivo dice "Integrar en la interfaz del IAsLab un motor de orquestación de inferencia...", y el tutor pregunta a qué interfaz se refiere exactamente. Es ambiguo si se trata del frontend web del sistema (React/Next.js, según `technologies.md`), de una API existente, o de otra superficie. Sin esa precisión, el objetivo describe una integración con un componente sin nombrar cuál.
- **Qué se necesita para cerrarla:** el nombre o la naturaleza exacta de esa interfaz (¿el frontend web del control plane? ¿una API?).
- **Al resolver:** sustituir "la interfaz del IAsLab" por el nombre preciso del componente, y borrar el `\todo{}`.

Responder: Esto fue una alucionacion, realmente no hay ninguna interfaz, la plataforma de manejo para la infrastructura se creara, lo unico con lo que se integra es con SAAMFI que sirve como IdP, el motor de inferencia sera alguno ya conocido como vLLm o llama.ccp, probablemente este segundo ya que es el que los maestros que han hecho pruebas les ha funcionado mejor (Puedes usar esto en antecedentes, de como actualmente despliegan modelos a mano en la sala y tienen scripts para obtener benchmarks, de sus pruebas han encontrado que llama.cpp les permite desplegar los mejores modelos, de todas formas la infrastructura del sistema deberia ser capaz de utilizar cualquier modelo de inferencia ya que es simplemente construir una imagen docker con este segun lo tengo entendido)

### ADR-028 — ¿Se acepta la reescritura sugerida por el tutor para el objetivo específico de observabilidad?

- **Estado:** abierta
- **Abierta por:** Coordinador · 2026-09-12
- **A quién corresponde:** autores
- **Dónde se usa:**
  - `thesis/chapters/04-objetivos.tex` — primer objetivo específico (observabilidad) · marcador literal: `\todo{Primer objetivo especfiico demasiado detallado, podría ser incluso un objetivo general, evitar usar palabras ambiguas como "interactivas"...}`
- **Contexto:** a diferencia de otros `\todo{}`, este trae una propuesta de reescritura completa y concreta del propio tutor: *"Desarrollar un módulo de observabilidad en el sistema web del IAsLab para la captura y visualización de métricas de hardware y de inferencia, orientado a la supervisión del estado de los nodos de cómputo."* No es una pregunta abierta en el sentido usual — es una redacción lista para adoptar — pero sustituir el objetivo formal del proyecto por la sugerencia de un tercero sin que los autores la revisen y la asuman como propia sería igual de arriesgado que inventarla.
- **Qué se necesita para cerrarla:** un sí/no de los autores a adoptar la reescritura del tutor tal cual, o con ajustes.
- **Al resolver:** reemplazar el objetivo con el texto acordado y borrar el `\todo{}`.

Responder: Si, se acepta la reescritura sugerida por el tutor para el objetivo específico de observabilidad, ya que es una redacción más clara y precisa que la original. Estas reglas son clavve a la hora de redactar objetivos y de hecho actualiza el harnes. Los objetivos deben ser verbos en infitivo, ser claros, precisos y sin ambiguidades, deben ser medibles y alacanzables. No deben confundirse con actividades y no deben contener multiples verbos

