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
  - `thesis/chapters/02-descripcion-problema.tex` — final del capítulo · marcador literal: `% [verify: ADR-010 — enlazar al árbol de problemas cuando exista en 99-anexos.tex]`
- **Contexto:** el formato exige como anexos el análisis de participación, el árbol de problemas y el árbol de objetivos. El capítulo 2 ya tiene identificadas causas y efectos jerarquizados, de modo que el árbol puede derivarse de ese texto; falta decidir si se dibuja en TikZ dentro del documento o se inserta como imagen en `thesis/imagenes/`.
- **Qué se necesita para cerrarla:** la decisión de formato (TikZ o imagen) y la confirmación de que los tres anexos son obligatorios en esta entrega.
- **Al resolver:** crear los anexos con sus `\label{}`, y sustituir el marcador del capítulo 2 por un `\cref{}` real al árbol de problemas.

