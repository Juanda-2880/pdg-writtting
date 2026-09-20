# Meeting index

One row per meeting. Read this before opening a full record: it says what exists and what
each meeting closed, without loading whole files into context.

Maintained by the [`meeting-insights/`](../../skills/meeting-insights/README.md) skill, which adds a
row here in the same step that writes a record. Titles are in Spanish because they name
Spanish documents.

| Date | Meeting | File | Decisions | ADR answered | Contradictions |
| :--- | :--- | :--- | :---: | :--- | :---: |
| 2026-08-26 | Arquitectura propuesta, recursos del laboratorio y alcance de PDG1 (2.ª reunión) | [`2026-08-26-tutor-arquitectura.md`](./2026-08-26-tutor-arquitectura.md) | 10 | ADR-013 (aplicada, b9c2943), ADR-014, ADR-015 (aplicadas, 1b671b1) · ADR-008, ADR-016 partial (aplicadas, 1b671b1) | 3 · all resolved 2026-09-12 · +1 review note → **ADR-030** |
| 2026-09-04 | Elicitación con Alejandro: uso real de la sala, motor de inferencia y benchmarks | [`2026-09-04-alejandro-elicitacion.md`](./2026-09-04-alejandro-elicitacion.md) | 3 | none · **ADR-013 contradicted** (closed by the authors against this testimony, b9c2943) · ADR-004, ADR-017 closed 2026-09-12 | 4 · all resolved 2026-09-12 · +2 review notes → **ADR-030, ADR-031** |
| 2026-09-09 | Delimitación del alcance y revisión en vivo del anteproyecto (3rd with the tutor) | [`2026-09-09-tutor-alcance-y-revision.md`](./2026-09-09-tutor-alcance-y-revision.md) | 11 | **ADR-015, ADR-016 resolved** (aplicadas, 1b671b1) · **ADR-018 resolved** "se queda", closed the other way (chapter deleted by the authors, 173a68f) · ADR-011 partial (closed, 1b671b1) · ADR-008, ADR-014 (closed, 1b671b1), ADR-017 (closed, 173a68f) advanced | 4 · all resolved 2026-09-12 · +4 review notes: 2 resolved with pointer; ADR-029 cerrada 2026-09-20 (prioridad por curso pasa a requerimiento Sin compromiso), **ADR-030** open |

## Columns

- **Decisions** — how many entries the record's `Decisiones tomadas` section has.
- **ADR answered** — the `project-context/ADR.md` identifiers the meeting answers, marked
  `(pend.)` while the answer has not been applied to the document. Applying it deletes the
  entry from `ADR.md`, but **the reference stays here**: it is what tells you where the
  answer came from once the entry no longer exists. Once applied, `(pend.)` becomes
  `(aplicada, <commit>)`, or `closed` when the entry was closed by a human decision that
  differs from what the meeting said.
- **Contradictions** — how many clashes with `project-context/` the meeting surfaced. A
  non-zero number is pending work for the Investigador, not a footnote. After the count:
  whether they are resolved, and any *review notes* added later to the record's
  `Contradicciones` section (clashes found on review, with the ADR opened for each).
