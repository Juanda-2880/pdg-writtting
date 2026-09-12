# Meetings

One record per meeting: what was decided, who committed to what, and which open questions
were answered. The records are produced by the
[`meeting-insights/`](../../skills/meeting-insights/README.md) skill from a transcript pasted into
the chat.

This folder holds **content**, not guidance. The extraction rules live in the module, the
same split [`thesis/`](../../thesis/README.md) has with `skills/latex/`.

> **Language.** The records themselves are written **in Spanish**, because the meetings are
> in Spanish and quotes are never translated. This README, like every other module README
> in the repository, is in English.

---

## Naming convention

```text
meetings/AAAA-MM-DD-<slug>.md      # 2026-08-26-tutor-arquitectura.md
```

The slug is two or three lowercase hyphenated words naming what the meeting was about:
`tutor-arquitectura`, `alejandro-elicitacion`, `equipo-cronograma`. When two meetings fall
on the same day, the slug is what tells them apart.

[`INDEX.md`](./INDEX.md) carries one row per meeting. **Read it before opening a full
record**: it says which meetings exist, what each was about, and which ADR entries each one
answered. Same relationship `thesis/STATUS.md` has with the chapters.

## Raw transcripts are not versioned

The transcript is pasted into the chat, processed, and discarded. Only the derived record
persists. Three reasons:

1. **Traceability without a dump.** Every claim in a record carries its literal quote and
   timestamp, so the source is checkable without storing the full text.
2. **Third-party data.** A transcript records people who never agreed to have their words
   land in a repository. The record keeps what the project needs; the rest has no reason to
   stay.
3. **Weight and noise.** Transcripts are long and mostly irrelevant, and versioning them
   buries the useful content in the history.

If one has to be kept for reprocessing, it goes in `compiled-output/`, which is already
gitignored. Never here.

## What a record is, and what it is not

**It is proposed evidence.** A fact asserted in a meeting is a *candidate* project fact. It
becomes a fact when a human writes it into
[`project-context/`](../README.md), and only then may the Redactor cite it.
This is rule 9 of [`CLAUDE.md`](../../CLAUDE.md).

For the same reason, a record **never** closes an entry in
[`project-context/ADR.md`](../ADR.md) on its own. It marks the entry
*pendiente de aplicar*, with the literal answer and the location the entry itself records.
Deleting the entry is a separate step, and it happens once the answer is actually in the
document.

## Structure of a record

Fixed sections, in this order. Sections with no content are omitted, because an empty
heading asserts "nothing was said about this" and that is not a claim you can support. The
headings are in Spanish since they are the literal output of the skill.

| Section | What it holds |
| :--- | :--- |
| `Decisiones tomadas` | Someone decided and nobody objected |
| `Compromisos` | Who took on what, and by when |
| `Respuestas a dudas abiertas (ADR)` | Which `ADR.md` entry was answered, and with what literal answer |
| `Contradicciones con project-context/` | What was said against what is written, with a locator for both |
| `Hechos nuevos del proyecto` | Candidates to enter `project-context/` |
| `Preguntas que quedaron abiertas` | Candidates for a new ADR entry |
| `Discutido sin conclusión` | Discussed, never closed |

The exact template is in [`meeting-insights/SKILL.md`](../../skills/meeting-insights/SKILL.md).
