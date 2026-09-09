# Extraction Guide

The rules that keep a meeting insight from becoming a source of invented facts. Read this
**before** extracting, not while reviewing what you already wrote.

The premise: a transcript is a *lossy* record. Automatic transcription mishears technical
vocabulary, speaker diarization mixes people up, and half a meeting is people thinking out
loud. Every rule below exists because one of those failure modes turns into a confident,
wrong sentence in the thesis if you let it.

---

## 1. Every claim carries its evidence

**A line without a literal quote does not go in the file.**

```markdown
✅ - **La VRAM por nodo son 24 GB, no 16** — «esos equipos tienen 24, los de 16 son los viejos» [00:14:32]
❌ - El tutor aclaró el tema de la VRAM.
```

The quote is transcribed **exactly as it was said** — including the hesitation, the broken
grammar, the wrong word order. You are recording what a person said, not what they should
have said. Fixing the phrasing is the first step toward recording something they didn't say.

Locator: use the timestamp `[MM:SS]` or `[HH:MM:SS]` if the transcript has one. If it does
not, use an approximate position (`[~mitad de la reunión]`) and say so — never fabricate a
timestamp, because a fabricated locator makes a claim unfalsifiable, which is worse than
having no locator at all.

**Corollary:** if you remember something was discussed but cannot find the line, it does
not go in the file. Search the transcript again; if it isn't there, it isn't evidence.

## 2. Decided ≠ committed ≠ suggested ≠ discussed

Four different things, four different buckets. The distinction is the single most valuable
thing this skill produces, because the tutor's *suggestions* and the tutor's *instructions*
carry very different weight for a thesis.

| What was said (Spanish, as spoken) | Goes in |
| :--- | :--- |
| "Entonces queda así, lo dejamos en X" | **Decisiones** |
| "Yo me encargo de mandarte el dato" | **Compromisos** |
| "Yo eso lo movería a anexos" (nadie confirma) | **Discutido sin conclusión** |
| "¿Y si probamos con…?" | **Discutido sin conclusión** |
| "No sé, habría que mirarlo" | **Preguntas abiertas** |

A decision needs **someone deciding and nobody objecting**. If the tutor proposes something
and the conversation moves on, that is a suggestion, not a decision — record it as
discussed and let the humans decide whether to adopt it.

When a decision is conditional, keep the condition: *"se mueve a anexos **si** el formato
lo permite"* is not *"se mueve a anexos"*.

## 3. Uncertain attribution gets marked, not guessed

Diarization fails constantly — it merges speakers, swaps them, and invents turn boundaries.
When you cannot tell who said something:

```markdown
- **<el hecho>** — «<cita>» [MM:SS] · `[hablante incierto]`
```

This matters more than it looks. "El tutor dijo que sobra el capítulo" and "alguien dijo
que sobra el capítulo" justify completely different actions. If the attribution changes what
someone would do, and you are not sure of it, mark it.

Same rule for the transcript mangling a technical term: if it reads *"cubernetes"* or
*"be-el-el-eme"*, quote it as it appears and add your reading in brackets —
«cubernetes [Kubernetes]» — so the reader can tell the transcript apart from your inference.

## 4. Cross-check against `ADR.md` — and do it first

[`project-context/ADR.md`](../project-context/ADR.md) is the register of questions blocking
the document. Read the open entries **before** extracting: you will not recognize an answer
to ADR-011 if you don't know ADR-011 was asked.

For each open entry, ask: *did this meeting answer it?* When one is answered:

```markdown
- **ADR-011** — SAAMFI significa «<cita literal>» [MM:SS]
  · **pendiente de aplicar** · la entrada dice que se usa en: `thesis/main.tex`
```

Copy the *Dónde se usa* field from the entry into the insight — that field exists precisely
so whoever applies the answer doesn't have to re-read the thesis.

**Do not delete the ADR entry.** The entry is deleted when the answer is *applied to the
document*, which is a separate, human-approved step. An entry deleted on the strength of a
transcript line is a question that silently stops being tracked.

A partial answer is worth recording as partial: *"responde la mitad de ADR-008 (fecha de
inicio), la duración por fase sigue abierta"*.

## 5. Cross-check against `project-context/` — contradictions are the payload

`project-context/` is the project's ground truth, and meetings are exactly where it gets
invalidated. When something said contradicts something written, report **both sides with
their locators**, and resolve neither:

```markdown
- **VRAM por nodo** — la reunión dice «tienen 24» [00:14:32];
  `project-context/requirements.md` dice «RTX 4080 (16 GB GDDR6X VRAM) per compute node»
  · **sin resolver**: ¿se corrige la fuente, o el hablante se equivocó?
```

These are the highest-value lines in the whole file, and the reason the cross-check is not
optional. A contradiction found here costs one edit; the same contradiction found by an
evaluator costs the document's credibility.

Note the second-order effect too: when a `project-context/` fact changes, everything derived
from it changes. Say so — *"si se confirma, hay que revisar también los tres sitios que citan
los 16 GB"* — rather than leaving the reader to discover it.

## 6. Nothing enters as a project fact on a transcript's word alone

A fact stated in a meeting is a **candidate**. It becomes a project fact when a human writes
it into `project-context/`, and only then may the Redactor cite it. Until that happens it
lives under *Hechos nuevos del proyecto (candidatos)* in the insight, with its quote.

This is rule 6 of [`CLAUDE.md`](../CLAUDE.md) applied to speech: *"never invent facts,
requirements, technical details, or citations"* — and a plausible sentence that a
transcription engine may have garbled is exactly the kind of gap that rule is about.

If a fact was stated **hedged** ("creo que", "me parece que", "no estoy seguro pero"), keep
the hedge in the quote and mark it. The tutor's *"creo que no son 16 GB"* is a reason to
verify, not a new number.

## 7. Language

Write the insight in the language of the meeting — Spanish for this project. **Quotes are
never translated**: a translated quote is a paraphrase wearing quotation marks. If the
meeting mixed languages (English technical terms in Spanish speech, which is normal here),
keep the mix.

## 8. What to leave out

Greetings, scheduling chatter, connection problems, jokes, and topics belonging to other
projects. Two exceptions worth keeping:

- **Scheduling that creates an obligation** ("nos vemos el martes con el cronograma listo")
  is a commitment, not chatter.
- **A tangent that reveals a project fact** stays, even if the meeting's topic was something
  else.

When in doubt about whether something matters, `Discutido sin conclusión` is the cheap,
honest place to put it. Dropping it entirely is a decision you make silently; recording it
there is one the reader can review.
