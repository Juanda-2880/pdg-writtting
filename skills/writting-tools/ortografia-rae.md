# RAE Orthography: Prefixes, Foreign Words and Calques

Two orthographic rules the thesis must follow, plus one project-specific decision about
literal calques from English. The first two are general RAE norms (verified against the
sources at the end); the third was adopted by the authors on 2026-09-12 after reviewing
the second version of the anteproyecto.

This binds the thesis text in `thesis/`. Quotations and official titles keep their
original spelling, always.

---

## 1. Prefixes are written joined to a one-word base

Since the *Ortografía de la lengua española* (2010), every prefix follows the same rule,
restated in the current *Diccionario panhispánico de dudas* ("prefijos", §1):

| Base | How the prefix is written | Examples |
| :--- | :--- | :--- |
| One word | **Joined, no hyphen, no space** | *macroproyecto, precuantizado, multiusuario, posentrenamiento, sobreasignación* |
| Starts with a capital, an acronym or a number | **Hyphen** | *anti-ALCA, mini-USB, pre-1945, sub-21* |
| Several words acting as a unit | **Separated** | *ex alto cargo, pro derechos humanos, pre Segunda Guerra Mundial* |

The DPD marks the hyphenated and separated spellings of a one-word base as incorrect
(*⊗anti-cancerígeno*, *⊗anti cancerígeno*). So *macro-proyecto* and *pre-cuantizados* are
errors, not stylistic variants. This is not a recent change: the rule dates from 2010.

A hyphen is only admitted exceptionally, to force the literal etymological reading of a
word that already has a settled meaning (*re-presentar* vs. *representar*). Nothing in this
thesis needs that exception.

## 2. Unadapted foreign words go in italics

A foreign word used with its original spelling and pronunciation (*extranjerismo crudo*)
is written in **italics** in typeset text (`\emph{}` in LaTeX). An adapted word follows
Spanish spelling and accent rules and goes in **roman**.

How to tell them apart: look the word up in the DLE (<https://dle.rae.es>).

- The DLE prints the headword **in italics** → crude, use `\emph{}`. Checked 2026-09-12:
  *hardware*, *software*, *sprint*, *streaming*, *script*.
- The DLE prints it **in roman**, usually with a Spanish accent → adapted, no italics:
  *clúster*, *caché*, *escalable*, *granularidad*.
- **Not in the DLE** → treat as crude, use `\emph{}`: *token*, *throughput*, *framework*,
  *kernel*, *backlog*, *benchmarking*, *proxy*, *enforcement*, *on-premise*, *footprint*,
  *harness*, *fine-grained*.

Proper names of products, projects and tools stay in roman even when they are English
(Kubernetes, Prometheus, Grafana, Jira, Bitbucket, GitOps). File formats and acronyms stay
in roman (YAML, GGUF, GPU). The engine name *llama.cpp* is already set in italics
throughout the document; keep it that way for consistency.

Inside a span that is already italic (a work title in `\emph{}`), a foreign word would go
in roman. `\emph{}` nested inside `\emph{}` does this automatically.

## 3. Project decision: italic anglicism instead of a literal calque

**Rule (authors, 2026-09-12):** when the only Spanish rendering of a technical term is a
word-for-word calque that does not read as natural Spanish, write the English term in
italics instead of the calque.

The authors' reason: phrases like *de grano fino* read as machine translation. In a
document the tutor already reviews for AI tells (§4 of [`puntuation.md`](./puntuation.md)),
that is the same risk.

What this rule does **not** do: replace Spanish technical terms that are already
established in the discipline. Those stay in Spanish and in roman. A useful test is
whether the term appears in the Spanish edition of the tool's own documentation or in the
DLE with the technical meaning.

| Calque (don't write) | Write instead |
| :--- | :--- |
| *de grano fino*, *fina* (observabilidad fina), *granular* (telemetría granular) | `\emph{fine-grained}` |
| *servido* (el servido de modelos) | *servicio* (*servicio de modelos*, *servicio de inferencia*), or rephrase with the verb *servir*. **Never** `\emph{serving}`: the authors rejected it on 2026-09-12. |
| *huella* (huella de memoria, huella de despliegue) | `\emph{footprint}` |
| *arnés* (arnés de pruebas) | `\emph{harness}` |
| *los primitivos* (Kubernetes primitives) | *las primitivas* (the Spanish noun is feminine) |

**Established, keep in Spanish (roman):** *servicio de modelos* / *servicio de inferencia* (not *serving*), *plano de control* (write `(\emph{control plane})`
on first use), *espacio de nombres*, *tiempo real*, *carga de trabajo*, *contenedor*,
*clúster*, *caché*, *cuello de botella*, *línea base*, *autoescalado*, *planificador*.

`granular` alone is in the DLE, but only with the physical sense (made of grains). The noun
*granularidad* does carry "grado de detalle de una información", so *de alta granularidad*
is a correct alternative to `\emph{fine-grained}` if the authors ever prefer a Spanish form.

Extend the two lists above whenever a new case gets decided, so the next agent doesn't have
to decide it again.

---

## 4. Checks

Run from the repository root. Each should print nothing; review any output by hand.

```bash
# §1: hyphenated prefixes on a lowercase one-word base (skips LaTeX comments)
grep -nE '\b(macro|micro|pre|pos|post|anti|multi|sub|super|semi|inter|intra|sobre|auto|co|re|ex)-[a-záéíóúñ]' thesis/chapters/*.tex thesis/main.tex | grep -vE ':[0-9]+:\s*%'

# §3: known calques
grep -nE 'grano fino|observabilidad fina|telemetría granular|visibilidad granular|\bel servido\b|\bserving\b|huella de (memoria|despliegue)|arnés|los primitivos' thesis/chapters/*.tex thesis/main.tex

# §2: crude anglicisms left in roman. A first filter only: it also flags words inside a
# multi-word \emph{...} or \textbf{...}, so check each hit. Expected false positives
# today: "Arquitectura de Software" (part of the IAsLab's proper name) and "servicios de
# software" (inside the macroproyecto's italic title), both in chapter 01, line 30.
grep -nE '(^|[^{a-zA-Z-])(hardware|software|tokens?|sprints?|backlog|throughput|framework|kernels?|enforcement|proxy|on-premise|scripts?)([^a-zA-Z}-]|$)' thesis/chapters/*.tex thesis/main.tex | grep -vE ':[0-9]+:\s*%'
```

Remember that LaTeX command arguments (`\caption{}`, `\section{}`, table cells in
`\textbf{}`) are prose too: the reader sees them, so the same rules apply there.

## Sources

- RAE y ASALE, *Diccionario panhispánico de dudas*, entry "prefijos", §1.1–1.3.
  <https://www.rae.es/dpd/prefijos>
- RAE, Duda rápida: "¿Los prefijos se escriben pegados a la palabra?"
  <https://www.rae.es/duda-linguistica/los-prefijos-se-escriben-pegados-la-palabra>
- RAE, Español al día: "Los extranjerismos y latinismos crudos (no adaptados) deben
  escribirse en cursiva". <https://www.rae.es/espanol-al-dia/los-extranjerismos-y-latinismos-crudos-no-adaptados-deben-escribirse-en-cursiva>
- RAE y ASALE, *Ortografía de la lengua española* (2010), "Extranjerismos crudos".
  <https://www.rae.es/ortografía/extranjerismos-crudos>
- RAE y ASALE, *Diccionario de la lengua española*, 23.ª ed., versión electrónica 23.8.1:
  entries *hardware*, *software*, *sprint*, *script*, *granular*, *granularidad* (consulted
  2026-09-12). <https://dle.rae.es>
