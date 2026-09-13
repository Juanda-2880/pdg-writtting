# Academic Punctuation & Orthographic Precision

In empirical scientific and technical writing, punctuation is a tool of logical precision, not stylistic ornament. Accurate punctuation defines the hierarchy of ideas, prevents syntactical ambiguity, and ensures rigorous communication.

---

## 1. Mandatory Uses of the Period / Full Stop (Usos Obligatorios del Punto)

The period represents the highest-level syntactic delimiter within a paragraph.

### A. Punto y Seguido (Sentence-Final Period)
- **Rule:** Separates complete, grammatically independent thoughts within the same paragraph that share the same thematic focus.
- **Mandatory Requirement:** Must always be followed by an initial capital letter.
- **Academic Practice:** Use to maintain sentence agility (average sentence length: 15–28 words). Break convoluted, runaway compound sentences into clear propositions using *punto y seguido*.

### B. Punto y Aparte (Paragraph-Final Period)
- **Rule:** Marks the complete closure of an argument, micro-claim, or thematic unit.
- **Mandatory Requirement:** The subsequent line must begin a new paragraph with standard indentation (0.5 in / 1.27 cm in APA).
- **Academic Practice:** Use when switching analytical angles, advancing to the next chronological phase, or pivoting from methodology to empirical results.

### C. Punto Final (Document / Section Final Period)
- **Rule:** Concludes an entire chapter, section, or document.

### D. Punctuation with Citations and Quotations
- **Parenthetical Citation at End of Sentence:** Place the period **outside** the closing parenthesis of the citation:
  - ✔️ *"The neural model attained a 94.2% F1-score on the evaluation dataset (Vaswani et al., 2017)."*
  - ❌ *"The neural model attained a 94.2% F1-score on the evaluation dataset. (Vaswani et al., 2017)"*
- **Block Quotations (≥40 words):** Place the period **before** the parenthetical citation at the very end of the block.

---

## 2. Punctuation Delimiters: Comma, Semicolon, and Colon

### A. The Comma (La Coma)
1. **Introductory / Adverbial Clauses:** Always follow introductory phrases with a comma.
   - *"En consecuencia, los resultados preliminares confirman la hipótesis nula."*
   - *"To evaluate system scalability, we conducted synthetic stress tests."*
2. **Compound Sentences with Coordinating Conjunctions:** Use before coordinating conjunctions (*pero, mas, sino, and, but, yet*) when connecting two independent clauses with distinct subjects.
   - *"El procesador completó la tarea de inferencia en 12 ms, pero el ancho de banda del bus limitó la tasa de refresco."*
3. **Oxford / Serial Comma (APA 7 Requirement in English):** Place a comma before the conjunction in a series of three or more items.
   - ✔️ *"We measured latency, throughput, and error rates."*
4. **Avoid the "Comma Splice" (Coma Criminal):** Never separate a grammatical subject from its verb with a single comma.
   - ❌ *"El algoritmo de optimización bayesiana, converge rápidamente."*
   - ✔️ *"El algoritmo de optimización bayesiana converge rápidamente."*

### B. The Semicolon (El Punto y Coma)
- **Joining Closely Related Independent Clauses:** Replaces a period between two grammatically complete clauses that have an immediate conceptual or cause-and-effect relationship.
  - *"La memoria caché de nivel 1 reduce la latencia de acceso a datos inmediatos; la memoria caché de nivel 2 optimiza el trasvase masivo hacia la memoria principal."*
- **Complex Enumerations:** Separates items in a list when one or more items already contain internal commas.
  - *"Las muestras provinieron de tres ubicaciones: Bogotá, Colombia; Lima, Perú; y Santiago, Chile."*
- **Preceding Adversative Connectors in Extended Sentences:** Use before connectors such as *sin embargo, no obstante, por consiguiente, therefore, however* when linking independent clauses:
  - *"El modelo presentó una alta tasa de convergencia en el conjunto de entrenamiento; sin embargo, exhibió sobreajuste pronunciado al evaluar los datos de validación."*

### C. The Colon (Los Dos Puntos)
- **Preceding Deductive Explanations or Conclusions:** Introduces an elaboration, consequence, or concrete explanation of the preceding clause.
  - *"El diagnóstico del servidor arrojó una conclusión concluyente: la degradación se debió a un bloqueo concurrente en la tabla de transacciones."*
- **Introducing Formal Lists / Enumerations:** Use only when preceded by a complete, grammatically intact clause.
  - ✔️ *"La arquitectura implementa tres capas fundamentales: presentación, lógica de negocio y persistencia de datos."*
  - ❌ *"Las tres capas son: presentación, lógica y datos."* (Do not break the predicate).

> [!IMPORTANT]
> The uses above are valid general Spanish, but **this project restricts the colon in thesis prose** (§4.3). Read that section before using one.

---

## 3. Em-Dash (—), En-Dash (–), and Hyphens (-)

| Punctuation Mark | Character | Primary Academic Function | Example |
| :--- | :--- | :--- | :--- |
| **Hyphen (Guion corto)** | `-` | Compound words, prefixes, technical adjectives. | *State-of-the-art*, *pre-processing*, *socio-técnico*. |
| **En-dash (Guion medio)** | `–` | Number ranges, page spans, dates, equal associations. | *pp. 120–145*, *2018–2024*, *Dijkstra–Fletcher model*. |
| **Em-dash (Guion largo)** | `—` | **Banned in this project.** See §4.1. | ~~*"El consumo energético —medido con instrumentación de precisión— disminuyó un 18%."*~~ → *"El consumo energético, medido con instrumentación de precisión, disminuyó un 18%."* |

---

## 4. Markers of Machine-Written Prose

Three patterns are **banned** from this project's document. They are not grammar errors: they
are style markers an evaluator associates with AI-generated text, and the tutor flagged the
first one explicitly as a risk of being misread as such.

### 4.1 The em dash (`—`) as a parenthetical

**Banned.** The tutor asked for it literally, three times in his review: *"Evitar escribir
guiones largos (—) para evitar malentendidos sobre uso de IA"*.

The em dash remains valid in general academic Spanish. This prohibition is **local to this
project** and answers to how the document is read, not to the norm. The en dash (`–`) for
numeric ranges **stays**: it is a different mark and is not in question.

How to replace it, in order of preference:

| What the em dash was doing | Replace with | Example |
| :--- | :--- | :--- |
| A short aside | Commas | *La telemetría, medida cada cinco minutos, alimenta el panel.* |
| A long or technical aside | Parentheses | *El motor de inferencia (vLLM en la propuesta inicial, llama.cpp en la práctica) determina el rendimiento.* |
| A clarification closing the sentence | Full stop, or a connector that states the relation (*porque*, *ya que*, *de modo que*) | *El cuello de botella está en la red, cuya velocidad limita la carga.* Never a colon (§4.3). |
| Two ideas forced into one sentence | Full stop | *El clúster reparte la carga. Cada nodo sirve un modelo distinto.* |

If the sentence turns confusing once the dash is gone, that almost always means it was
carrying too many ideas. Split it.

### 4.2 The antithetical construction (`no es X, es Y`)

**Banned** in all its variants:

- *No es un problema de red, es un problema de memoria.*
- *El objetivo no es describir, sino justificar.*
- *No solo reduce la latencia, sino que también mejora la equidad.*
- *Esto no es una limitación; es una decisión de diseño.*

Two reasons, and the second matters more than the first:

1. **It is a recognizable tic of machine-written prose.** Its binary rhythm appears at a
   frequency human academic writing does not have.
2. **It substitutes emphasis for argument.** The construction *asserts* a contrast instead
   of demonstrating it: it presents the discarded thesis as though someone had defended it,
   and takes its own as proven without evidence. In a document where every claim must rest
   on a source or a datum, that is precisely the hole an evaluator looks for.

**How to fix it:** state directly what you mean and support it. If the contrast is real and
carries weight, develop it as an argument with its evidence, not as a rhetorical turn.

| Instead of | Write |
| :--- | :--- |
| *No es un problema de red, es un problema de memoria.* | *El cuello de botella está en la memoria de video, porque la saturación de VRAM precede al congelamiento del nodo (\citealp{...}).* |
| *El objetivo no es describir, sino justificar.* | *El objetivo es justificar la elección metodológica.* |
| *No solo reduce la latencia, sino que también mejora la equidad.* | *Reduce la latencia. Además, distribuye el acceso entre roles con cuotas distintas.* |

When the contrast genuinely is the point (refuting an alternative in the state of the art,
for instance), the correct form is the **Comparación y Contraste** pattern from
[`../parragraph-structure/paragraph-types.md`](../parragraph-structure/paragraph-types.md):
present the alternative, evaluate it against evidence, and explain why it does not solve
the problem. That is a paragraph, not a sentence with a comma.

### 4.3 The colon as a sentence splice (`idea: explicación`)

**Banned in thesis prose** (authors, 2026-09-13). The authors saw it across many paragraphs and
asked to avoid it: *"es mejor evitarlo y seguir una secuencia lógica que conecte las ideas y
que no parezcan cortadas"*. Examples taken from this document:

- *Detrás de la restricción operaba un criterio de equidad económica: no todos los estudiantes pueden…*
- *El laboratorio cuenta, además, con un antecedente técnico directo: antes de este proyecto…*
- *…porque su alcance es amplio: MLOps aborda retos muy diversos…*

The colon cuts the sentence in two and leaves the reader to work out how the halves relate.
It is the same kind of shortcut as the em dash (§4.1) and the antithesis (§4.2): the rhythm
looks deliberate, but the logical connection that academic prose owes the reader never gets
written. A string of these reads as a list of fragments, not an argument.

**How to fix it.** Write the relation the colon was hiding:

| The colon was introducing… | Write | Example |
| :--- | :--- | :--- |
| a cause or reason | *porque*, *ya que*, *dado que* | *Esa restricción respondía a un criterio de equidad económica, dado que no todos los estudiantes pueden…* |
| a consequence | *de modo que*, *por lo que*, *así que* | *…sin ninguna plataforma que automatizara el proceso, de modo que solo quienes tenían acceso podían hacerlo.* |
| an explanation of the same idea | a new sentence that names the subject again | *…construyó un sistema web que actúa como plano de control. Ese sistema centraliza…* |
| a list | the list as part of the clause (*entre ellas*, *que son*, *como*) | *…retos como la baja utilización de las GPU y las largas demoras en cola.* |

**Still allowed:** introducing a block quotation (APA 7th), inside direct quotations and work
titles, which keep their original punctuation, and in labels outside running prose (table
headers, LaTeX comments).

---

## 5. Punctuation Diagnostic Checklist

Before submitting drafts, verify these mechanical checkpoints:
- [ ] No comma between grammatical subject and main verb.
- [ ] In-text parenthetical citations end with the period **outside** the closing parenthesis `)...`.
- [ ] Semicolons are used strictly to link independent clauses or separate lists with internal commas.
- [ ] Number and page ranges use en-dashes (`–`), not short hyphens (`-`).
- [ ] **Zero em dashes (`—`) in the document** (§4.1). Count occurrences, not lines:
      `grep -o '—' thesis/chapters/*.tex thesis/main.tex | wc -l`
- [ ] **No antithetical constructions** (§4.2). The grep is a first filter only and **yields
      false positives** (it also flags em-dash asides), so its output is reviewed by hand:
      `grep -nE 'no (es|son|solo|se trata)[^.;]{3,80}(sino|, (es|son))' thesis/chapters/*.tex`
      The cases no pattern catches (`Esto no es una limitación; es una decisión`) are only
      found by reading.
- [ ] **No colon splices in prose** (§4.3). First filter only: it skips LaTeX comments, but it
      still flags colons inside quotations and titles, so review each hit by hand:
      `grep -nE '[^:0-9]: [[:alpha:]¿«\\]' thesis/chapters/*.tex | grep -vE ':[0-9]+:\s*%'`
- [ ] In English prose adhering to APA 7, the Oxford comma is consistently applied.
