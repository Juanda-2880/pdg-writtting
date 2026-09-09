# Meetings — Insights de reuniones

Un archivo por reunión, con lo que se decidió, quién se comprometió a qué, y qué dudas
abiertas quedaron respondidas. Los genera la skill
[`meeting-insights/`](../meeting-insights/README.md) a partir de una transcripción pegada en
el chat.

Esta carpeta guarda **contenido**, no guías: las reglas de extracción viven en el módulo,
igual que [`thesis/`](../thesis/README.md) guarda el documento y `latex/` las reglas para
escribirlo.

---

## Convenio de nombres

```text
meetings/AAAA-MM-DD-<slug>.md      # 2026-09-07-tutor-objetivos.md
```

El slug son dos o tres palabras en minúscula separadas por guiones, que digan de qué fue la
reunión: `tutor-objetivos`, `admin-hardware`, `equipo-cronograma`. Si hay dos reuniones el
mismo día, el slug las distingue.

[`INDEX.md`](./INDEX.md) lleva una fila por reunión. **Léelo antes de abrir un insight
completo**: dice qué reuniones hay, de qué fueron y qué ADR respondió cada una — la misma
relación que `thesis/STATUS.md` tiene con los capítulos.

## Las transcripciones crudas no se versionan

La transcripción se pega en el chat, se procesa y se descarta. Solo persiste el insight
derivado. Tres razones:

1. **Trazabilidad sin volcado.** Cada afirmación del insight lleva su cita literal y su marca
   de tiempo, así que la fuente es verificable sin guardar el texto completo.
2. **Datos de terceros.** Una transcripción registra a personas que no decidieron que sus
   palabras quedaran en un repositorio público. El insight recoge lo que el proyecto
   necesita; el resto no tiene por qué quedar.
3. **Peso y ruido.** Las transcripciones son largas y en su mayoría irrelevantes; versionarlas
   entierra el contenido útil en el historial.

Si hace falta conservar una para reprocesarla, va en `compiled-output/`, que ya está
gitignoreado — nunca aquí.

## Qué es (y qué no es) un insight

**Es evidencia propuesta.** Un dato afirmado en una reunión es un *candidato* a hecho del
proyecto. Se convierte en hecho cuando alguien lo escribe en
[`project-context/`](../project-context/README.md), y solo entonces el Redactor puede citarlo.

Por lo mismo, un insight **nunca** cierra una entrada de
[`project-context/ADR.md`](../project-context/ADR.md) por su cuenta. La marca como
*"pendiente de aplicar"*, con la respuesta literal y la ubicación que la propia entrada
registra; borrarla es un paso aparte, que ocurre cuando la respuesta ya está aplicada al
documento.

## Estructura de un insight

Secciones fijas, en este orden, y las que no tengan contenido se omiten (un encabezado vacío
afirma que "no se habló de esto", y eso no se puede sostener):

| Sección | Qué recoge |
| :--- | :--- |
| Decisiones tomadas | Alguien decidió y nadie objetó |
| Compromisos | Quién se hizo cargo de qué, y para cuándo |
| Respuestas a dudas abiertas (ADR) | Qué entrada de `ADR.md` quedó respondida, y con qué respuesta literal |
| Contradicciones con `project-context/` | Lo dicho contra lo escrito, con el localizador de ambos |
| Hechos nuevos del proyecto | Candidatos a entrar en `project-context/` |
| Preguntas que quedaron abiertas | Candidatas a ADR nueva |
| Discutido sin conclusión | Se habló, nadie cerró nada |

La plantilla exacta está en [`meeting-insights/SKILL.md`](../meeting-insights/SKILL.md).
