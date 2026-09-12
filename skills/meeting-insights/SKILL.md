---
name: meeting-insights
description: Use when a meeting transcript is pasted into the chat and needs to be turned into a durable record — meetings with the thesis tutor, the lab administrators, or the author team (acta, minutes, "extract the insights from this transcript", "what did we decide in this meeting"). Produces one traceable Markdown file per meeting in `project-context/meetings/`, cross-checked against the open questions in `project-context/ADR.md` and the project facts in `project-context/`.
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
[`project-context/ADR.md`](../../project-context/ADR.md). You are looking for answers to
*specific* open questions, and you will only recognize them if you know what they are.
Skipping this step is the most common way this skill produces a pretty file that closes
nothing.

### 4. Extract

Walk the transcript once, in order, filling the template below. Apply the rules in
[`extraction-guide.md`](./extraction-guide.md): every line carries a literal quote, and
decided / suggested / discussed are three different buckets.

### 5. Write the file and index it

- Write `project-context/meetings/AAAA-MM-DD-<slug>.md` (slug: two or three words, lowercase, hyphenated —
  `tutor-objetivos`, `admin-hardware`).
- Add one row to [`meetings/INDEX.md`](../../project-context/meetings/INDEX.md).
- Report to the user, in the chat: how many decisions were recorded, which ADR entries the
  meeting appears to answer, and any contradiction found with `project-context/`. Those are
  the parts that need a human next.

## Output template

Write the insight file in **the language of the meeting**, which for this project is
Spanish. The template below is therefore given in Spanish on purpose: its headings and
labels are the **literal output** the skill must emit, not documentation to be translated.
Keep them verbatim so every record in `project-context/meetings/` is greppable by the same section names.

Omit a section entirely if it has no content. An empty heading reads as "nothing was said
about this", which is a claim you cannot make.

```markdown
# Reunión AAAA-MM-DD — <tema>

- **Participantes:** <nombre o rol> (tutor), … · marcar `[no identificado]` si la transcripción no lo aclara
- **Duración / tramo cubierto:** <si consta>
- **Fuente:** transcripción pegada en el chat, no versionada (ver `project-context/meetings/README.md`)

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

Section names stay in Spanish because they are the literal output headings.

| Section | What goes in | What does NOT |
| :--- | :--- | :--- |
| `Decisiones tomadas` | Someone decided and nobody objected | "We could…", "we'd have to look at it" |
| `Compromisos` | A named person took something on | A task nobody picked up |
| `Respuestas a dudas abiertas (ADR)` | Answers a specific open entry | A tangentially related remark |
| `Contradicciones con project-context/` | Clashes with something written there | Clashes with something you assumed |
| `Hechos nuevos del proyecto` | A project fact stated with confidence | A fact the speaker hedged |
| `Preguntas que quedaron abiertas` | Explicitly left unanswered | Something *you* found unclear |
| `Discutido sin conclusión` | Discussed, never closed | Noise, greetings, unrelated topics |

## Common mistakes

- **Summarizing instead of quoting.** An insight with no literal quote is indistinguishable from an invention. If you cannot find the sentence, the line does not go in.
- **Promoting a suggestion to a decision.** "I'd move that to the appendix" is not "it was moved to the appendix". This is the most expensive failure: it turns the tutor's opinion into a commitment of the document.
- **Guessing who spoke.** Diarization fails constantly; `[hablante incierto]` is a valid answer, inventing a name is not.
- **Not reading `ADR.md` before extracting.** You produce a tidy record that closes nothing, because you did not know which questions were open.
- **Applying the answer to the document in the same pass.** Not this skill's job (see above).
- **Switching languages.** Quotes are transcribed as they were spoken and are never translated.

## Supporting files

- [`extraction-guide.md`](./extraction-guide.md) — the extraction rules: mandatory evidence, the four buckets, uncertain attribution, and the two cross-checks against `ADR.md` and `project-context/`.
- [`README.md`](./README.md) — what the module is and how it wires into the rest of the harness.

When sharing or installing this skill, keep the whole `meeting-insights/` folder together.
`SKILL.md` depends on `extraction-guide.md` by relative path, and writes into `project-context/meetings/`.
