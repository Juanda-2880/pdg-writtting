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

