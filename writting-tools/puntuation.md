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

---

## 3. Em-Dash (—), En-Dash (–), and Hyphens (-)

| Punctuation Mark | Character | Primary Academic Function | Example |
| :--- | :--- | :--- | :--- |
| **Hyphen (Guion corto)** | `-` | Compound words, prefixes, technical adjectives. | *State-of-the-art*, *pre-processing*, *socio-técnico*. |
| **En-dash (Guion medio)** | `–` | Number ranges, page spans, dates, equal associations. | *pp. 120–145*, *2018–2024*, *Dijkstra–Fletcher model*. |
| **Em-dash (Guion largo)** | `—` | **Prohibido en este proyecto.** Ver §4. | ~~*"El consumo energético —medido con instrumentación de precisión— disminuyó un 18%."*~~ → *"El consumo energético, medido con instrumentación de precisión, disminuyó un 18%."* |

---

## 4. Rasgos que delatan redacción automática

Dos patrones están **prohibidos** en el documento de este proyecto. No son errores de gramática: son marcas de estilo que un evaluador asocia con texto generado por IA, y el tutor las señaló explícitamente como riesgo de malentendido sobre el uso de IA en el trabajo.

### 4.1 Guion largo (`—`) como signo parentético

**Prohibido.** El tutor lo pidió de forma literal, tres veces en su revisión: *"Evitar escribir guiones largos (—) para evitar malentendidos sobre uso de IA"*.

El guion largo sigue siendo válido en español académico general; la prohibición es **local a este proyecto** y responde a cómo se lee el documento, no a la norma. El `–` (en-dash) para rangos numéricos **sí se conserva**: es otro signo y no está en cuestión.

Cómo sustituirlo, en orden de preferencia:

| El guion largo hacía… | Sustituir por | Ejemplo |
| :--- | :--- | :--- |
| Un inciso corto | Comas | *La telemetría, medida cada cinco minutos, alimenta el panel.* |
| Un inciso largo o técnico | Paréntesis | *El motor de inferencia (vLLM en la propuesta inicial, llama.cpp en la práctica) determina el rendimiento.* |
| Una aclaración que remata la frase | Dos puntos | *El cuello de botella es uno solo: la velocidad de la red.* |
| Dos ideas que se estaban forzando en una frase | Punto y seguido | *El clúster reparte la carga. Cada nodo sirve un modelo distinto.* |

Si al sustituirlo la frase se vuelve confusa, casi siempre significa que la frase cargaba demasiadas ideas: pártela.

### 4.2 Estructura antitética (`no es X, es Y`)

**Prohibida** en todas sus variantes:

- *No es un problema de red, es un problema de memoria.*
- *El objetivo no es describir, sino justificar.*
- *No solo reduce la latencia, sino que también mejora la equidad.*
- *Esto no es una limitación; es una decisión de diseño.*

Dos razones, y la segunda importa más que la primera:

1. **Es un tic reconocible de redacción automática.** Su ritmo binario aparece con una frecuencia que la prosa académica humana no tiene.
2. **Sustituye argumento por énfasis.** La construcción afirma un contraste en lugar de demostrarlo: presenta la tesis descartada como si alguien la hubiera sostenido, y da por probada la propia sin evidencia. En un anteproyecto donde cada afirmación debe apoyarse en una fuente o en un dato, es exactamente el hueco que un evaluador busca.

**Cómo corregirla:** afirma directamente lo que quieres decir y respáldalo. Si el contraste es real y aporta, desarróllalo como argumento con su evidencia, no como giro retórico.

| En vez de | Escribe |
| :--- | :--- |
| *No es un problema de red, es un problema de memoria.* | *El cuello de botella está en la memoria de video: la saturación de VRAM precede al congelamiento del nodo (\citealp{...}).* |
| *El objetivo no es describir, sino justificar.* | *El objetivo es justificar la elección metodológica.* |
| *No solo reduce la latencia, sino que también mejora la equidad.* | *Reduce la latencia. Además, distribuye el acceso entre roles con cuotas distintas.* |

Cuando el contraste sí es el punto (por ejemplo, al refutar una alternativa en el estado del arte), la forma correcta es la del patrón **Comparación y Contraste** de [`../parragraph-structure/paragraph-types.md`](../parragraph-structure/paragraph-types.md): expones la alternativa, la evalúas con evidencia y explicas por qué no resuelve el problema. Eso es un párrafo, no una frase con coma.

---

## 5. Punctuation Diagnostic Checklist

Before submitting drafts, verify these mechanical checkpoints:
- [ ] No comma between grammatical subject and main verb.
- [ ] In-text parenthetical citations end with the period **outside** the closing parenthesis `)...`.
- [ ] Semicolons are used strictly to link independent clauses or separate lists with internal commas.
- [ ] Number and page ranges use en-dashes (`–`), not short hyphens (`-`).
- [ ] **Cero guiones largos (`—`) en el documento** (§4.1). Contar ocurrencias, no líneas:
      `grep -o '—' thesis/chapters/*.tex thesis/main.tex | wc -l`
- [ ] **Ninguna estructura antitética** (§4.2). El grep es solo un primer filtro y **produce falsos positivos** (marca también los incisos con guion largo), así que sus resultados se revisan a mano:
      `grep -nE 'no (es|son|solo|se trata)[^.;]{3,80}(sino|, (es|son))' thesis/chapters/*.tex`
      Los casos que ningún patrón atrapa (`Esto no es una limitación; es una decisión`) solo los encuentra una lectura.
- [ ] In English prose adhering to APA 7, the Oxford comma is consistently applied.
