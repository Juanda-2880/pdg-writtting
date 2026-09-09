---
name: meeting-insights
description: Use when a meeting transcript is pasted into the chat and needs to be turned into a durable record — meetings with the thesis tutor, the lab administrators, or the author team (acta, minutes, "extract the insights from this transcript", "what did we decide in this meeting"). Produces one traceable Markdown file per meeting in `meetings/`, cross-checked against the open questions in `project-context/ADR.md` and the project facts in `project-context/`.
---

# Turning a Meeting Transcript into Project Evidence

## Overview

Decisions about this thesis get made out loud. The tutor confirms a figure, the lab
administrator settles a hardware question, the team picks a scope — and none of it
reaches `project-context/`, so agents keep re-flagging as "open" things that were
answered weeks ago in a meeting.

This skill closes that loop. It takes a raw transcript, which arrives **pasted into the
chat** and is never committed, and produces one durable Markdown file per meeting whose
every claim is traceable to a literal quote.

The skill's output is **proposed evidence, not verified fact**. It reports what was said
and what that implies; a human decides whether it becomes project truth. See
[`extraction-guide.md`](./extraction-guide.md) for the rules that keep this honest — read
it before extracting, not after.

## What this skill must never do

Writing the insight file is the whole job. In the same run, **do not**:

- edit `project-context/ADR.md` (not even to delete an entry the meeting clearly answered),
- edit anything under `thesis/`,
- edit `project-context/documentation.md`, `requirements.md`, or `technologies.md`.

A transcript is a lossy, often mis-diarized record. Applying it straight to the document
would let one garbled sentence become a cited fact. The insight file **names** what should
change and where; a human approves, and then the normal role workflow
([`agent-roles/`](../agent-roles/README.md)) applies it.

## Procedure

### 1. Receive the transcript

It arrives pasted in the chat. If it is too long to hold comfortably in context, ask the
user to save it to the session scratchpad and read it in slices — **never** skim it and
summarize from the parts you happened to read. A transcript read halfway produces an
insight file that silently omits half the decisions, which is worse than no file.

### 2. Fix the metadata

Establish before extracting: **date** (`AAAA-MM-DD`), **participants and their role**
(tutor / autores / administrador del laboratorio), and the **topic**. If the date isn't in
the transcript, ask — it is the filename and the sort key, and guessing it corrupts the
index. Everything else can be marked uncertain; the date cannot.

### 3. Load what the meeting might answer

Before extracting, read the open entries in
[`project-context/ADR.md`](../project-context/ADR.md). You are looking for answers to
*specific* open questions, and you will only recognize them if you know what they are.
Skipping this step is the most common way this skill produces a pretty file that closes
nothing.

### 4. Extract

Walk the transcript once, in order, filling the template below. Apply the rules in
[`extraction-guide.md`](./extraction-guide.md): every line carries a literal quote, and
decided / suggested / discussed are three different buckets.

### 5. Write the file and index it

- Write `meetings/AAAA-MM-DD-<slug>.md` (slug: two or three words, lowercase, hyphenated —
  `tutor-objetivos`, `admin-hardware`).
- Add one row to [`meetings/INDEX.md`](../meetings/INDEX.md).
- Report to the user, in the chat: how many decisions were recorded, which ADR entries the
  meeting appears to answer, and any contradiction found with `project-context/`. Those are
  the parts that need a human next.

## Output template

Write the insight file in **the language of the meeting** (Spanish for this project).
Omit a section entirely if it has no content — an empty heading reads as "nothing was
said about this", which is a claim you cannot make.

```markdown
# Reunión AAAA-MM-DD — <tema>

- **Participantes:** <nombre o rol> (tutor), … · marcar `[no identificado]` si la transcripción no lo aclara
- **Duración / tramo cubierto:** <si consta>
- **Fuente:** transcripción pegada en el chat, no versionada (ver `meetings/README.md`)

## Decisiones tomadas

- **<la decisión, en una frase>** — «<cita literal>» [MM:SS]
  · afecta: `<ruta/al/archivo>`

## Compromisos

- **<quién>** — <qué> — <para cuándo, o `sin fecha`>  · «<cita literal>» [MM:SS]

## Respuestas a dudas abiertas (ADR)

- **ADR-0NN** — <la respuesta> — «<cita literal>» [MM:SS]
  · **pendiente de aplicar** · la entrada dice que se usa en: `<ruta>`

## Contradicciones con `project-context/`

- **<el dato>** — la reunión dice «<cita>» [MM:SS]; `project-context/<archivo>` dice «<cita>»
  · **sin resolver**: ¿corregir la fuente o la reunión se equivocó?

## Hechos nuevos del proyecto (candidatos a `project-context/`)

- <el hecho> — «<cita literal>» [MM:SS] · destino sugerido: `project-context/<archivo>`

## Preguntas que quedaron abiertas (candidatas a ADR nueva)

- <la pregunta> — surgió en «<cita>» [MM:SS] · a quién corresponde: <autores | tutor | lab>

## Discutido sin conclusión

- <el tema> — se habló, nadie cerró nada. «<cita>» [MM:SS]
```

## Quick reference

| Bucket | Qué entra | Qué NO entra |
| :--- | :--- | :--- |
| Decisiones | Alguien decidió y nadie objetó | "Podríamos…", "habría que ver" |
| Compromisos | Una persona se hizo cargo de algo | Una tarea que nadie tomó |
| Respuestas a ADR | Responde una duda abierta concreta | Un comentario tangencialmente relacionado |
| Contradicciones | Choca con algo escrito en `project-context/` | Choca con algo que tú suponías |
| Hechos nuevos | Dato del proyecto afirmado con seguridad | Dato que el hablante dijo dudando |
| Preguntas abiertas | Quedó explícitamente sin responder | Algo que a ti te quedó sin claro |
| Discutido | Se habló, no se cerró | Ruido, saludos, temas ajenos |

## Common mistakes

- **Resumir en vez de citar.** Un insight sin cita literal es indistinguible de una invención. Si no encuentras la frase, la línea no va.
- **Ascender una sugerencia a decisión.** "Yo lo movería a anexos" no es "se movió a anexos". Es la falla más cara: convierte una opinión del tutor en un compromiso del documento.
- **Adivinar quién habló.** La diarización falla; `[hablante incierto]` es una respuesta válida, inventar un nombre no.
- **No leer `ADR.md` antes de extraer.** Se producen actas que no cierran ninguna duda porque no se sabía cuáles había.
- **Aplicar la respuesta al documento en la misma pasada.** No es el trabajo de esta skill (ver arriba).
- **Cambiar de idioma.** Las citas se transcriben como se dijeron; nunca se traducen.

## Supporting files

- [`extraction-guide.md`](./extraction-guide.md) — las reglas de extracción: evidencia obligatoria, las tres cubetas, atribución incierta, cruce con `ADR.md` y con `project-context/`.
- [`README.md`](./README.md) — qué es el módulo y cómo se enlaza con el resto del harness.

When sharing or installing this skill, keep the whole `meeting-insights/` folder together.
`SKILL.md` depends on `extraction-guide.md` by relative path, and writes into `meetings/`.
