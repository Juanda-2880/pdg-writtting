# Índice de reuniones

Una fila por reunión. Léelo antes de abrir un insight completo: dice qué hay y qué cerró
cada reunión, sin cargar los archivos enteros al contexto.

Lo mantiene la skill [`meeting-insights/`](../meeting-insights/README.md): al escribir un
insight nuevo añade su fila aquí, en el mismo paso.

| Fecha | Reunión | Archivo | Decisiones | ADR respondidas | Contradicciones |
| :--- | :--- | :--- | :---: | :--- | :---: |
| 2026-08-26 | Arquitectura propuesta, recursos del laboratorio y alcance de PDG1 (2.ª reunión) | [`2026-08-26-tutor-arquitectura.md`](./2026-08-26-tutor-arquitectura.md) | 10 | ADR-013, ADR-014, ADR-015 (pend.) · ADR-008, ADR-016 parciales (pend.) | 3 |
| 2026-09-04 | Elicitación con Alejandro: uso real de la sala, motor de inferencia y benchmarks | [`2026-09-04-alejandro-elicitacion.md`](./2026-09-04-alejandro-elicitacion.md) | 3 | ninguna · **ADR-013 contradicha** | 4 |

## Columnas

- **Decisiones** — cuántas entradas tiene la sección "Decisiones tomadas" del insight.
- **ADR respondidas** — los identificadores de `project-context/ADR.md` que la reunión
  responde, marcados `(pend.)` mientras la respuesta no se haya aplicado al documento. Al
  aplicarla se borra la entrada de `ADR.md`, pero **la referencia se conserva aquí**: es lo
  que deja saber de dónde salió la respuesta cuando la entrada ya no existe.
- **Contradicciones** — cuántos choques con `project-context/` detectó la reunión. Una cifra
  distinta de cero es trabajo pendiente para el Investigador, no una anécdota.
