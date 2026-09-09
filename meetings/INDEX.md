# Meeting index

One row per meeting. Read this before opening a full record: it says what exists and what
each meeting closed, without loading whole files into context.

Maintained by the [`meeting-insights/`](../meeting-insights/README.md) skill, which adds a
row here in the same step that writes a record. Titles are in Spanish because they name
Spanish documents.

| Date | Meeting | File | Decisions | ADR answered | Contradictions |
| :--- | :--- | :--- | :---: | :--- | :---: |
| 2026-08-26 | Arquitectura propuesta, recursos del laboratorio y alcance de PDG1 (2.ª reunión) | [`2026-08-26-tutor-arquitectura.md`](./2026-08-26-tutor-arquitectura.md) | 10 | ADR-013, ADR-014, ADR-015 (pend.) · ADR-008, ADR-016 partial (pend.) | 3 |
| 2026-09-04 | Elicitación con Alejandro: uso real de la sala, motor de inferencia y benchmarks | [`2026-09-04-alejandro-elicitacion.md`](./2026-09-04-alejandro-elicitacion.md) | 3 | none · **ADR-013 contradicted** | 4 |

## Columns

- **Decisions** — how many entries the record's `Decisiones tomadas` section has.
- **ADR answered** — the `project-context/ADR.md` identifiers the meeting answers, marked
  `(pend.)` while the answer has not been applied to the document. Applying it deletes the
  entry from `ADR.md`, but **the reference stays here**: it is what tells you where the
  answer came from once the entry no longer exists.
- **Contradictions** — how many clashes with `project-context/` the meeting surfaced. A
  non-zero number is pending work for the Investigador, not a footnote.
