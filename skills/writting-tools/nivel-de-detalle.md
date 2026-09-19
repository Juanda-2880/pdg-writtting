# Level of Detail, Explicit Subjects and Formal Register

Project rules the authors set on 2026-09-13 while reviewing chapter 01, section by section. They
govern *what* a section says and *how clearly*, next to the mechanics of `puntuation.md` and
`ortografia-rae.md`. Every "before" example below was in this thesis.

---

## 1. The level of detail belongs to the section

Each section of the anteproyecto works at one level of abstraction. A detail that is true but
belongs to another level breaks the section's thread, even when it is well sourced.

The authors' diagnosis of the old second paragraph of *Antecedentes del problema*: *"mientras
que el primer y los últimos párrafos manejan un nivel arquitectónico y conceptual muy sólido
(hablando de MLOps, gobernanza y orquestación), el segundo párrafo desciende abruptamente a un
nivel de bitácora de laboratorio (hablando de archivos YAML, descartar vLLM y medir 20 tokens por
segundo)"*.

| Section | Belongs here | Goes elsewhere |
| :--- | :--- | :--- |
| **Contexto** | The discipline and the sector, with sources. The institutional and technical scenario **at architecture level**: which systems exist, what they do, what the project builds on. | Room inventories (room number, workstation count, GPU model). Tools used by other organizations (Prometheus, DCGM), which belong to the Marco teórico or the Estado del arte. |
| **Antecedentes del problema** | **Systemic gaps and prior efforts**: how access to the equipment worked, whether deployment was manual, what the previous degree project automated and what it left out, and literature showing those same problems elsewhere. | Logs of exploratory tests (configuration formats such as YAML, engines tried and discarded, tokens per second, response times), which go to Metodología or the final thesis. **Implementation decisions** (which engine runs inside), which go to Marco teórico, Estado del arte or Metodología. |
| Justificación, Descripción del problema, Objetivos, Marco teórico, Metodología, Contribución | *Not reviewed yet.* Add a row when the authors review each one. | |

**The test.** Does this detail help the reader understand **why the platform is needed**? If it
only explains how something was tested, which software runs inside, or how many units there
are, it belongs to another section or to `project-context/`.

**Example.**

| Before | After |
| :--- | :--- |
| *A partir de esa práctica, construyó un harness de benchmarking propio (un script de Python guiado por especificaciones YAML que mide tokens de entrada y salida por segundo y el tiempo de respuesta) y, tras descartar vLLM por resultados insuficientes, concluyó que una compilación de llama.cpp…* | *Poner un modelo en operación también era un proceso manual. Antes de este proyecto, el laboratorio desplegaba modelos ejecutando a mano scripts de Python que instalaban los motores de inferencia y sus dependencias, sin ninguna plataforma que automatizara el proceso…* |

The facts removed from the text are not lost: they remain in `project-context/documentation.md`
and can return in the section where they belong.

### Keep the thread between paragraphs

Each paragraph has to follow from the previous one. A paragraph that opens with an unrelated
actor, a company or a tool the reader hasn't met is usually a jump. Reorder from general to
particular and write the bridge sentence that connects them.

| Before | After |
| :--- | :--- |
| Contexto ¶3 opened with *"Fuera del laboratorio, Gao et al. analizaron…"* after the paragraph about the IAsLab, and closed on Prometheus and NVIDIA DCGM. | ¶1 MLOps → ¶2 *"Cuando esa infraestructura es compartida, optimizar el uso de sus GPU se vuelve un reto adicional"* (Gao et al.) → ¶3 *"Ese reto se presenta, a menor escala, en la infraestructura de cómputo que el IAsLab administra…"* |

## 2. Every verb has a visible subject

When the subject changes, or could be read as someone else, name it again.

| Before | Problem | After |
| :--- | :--- | :--- |
| *A partir de esa práctica, construyó un harness…* | Who built it? The subject is three clauses back. | Name the actor, or rewrite the sentence around the fact that matters. |
| *En la plataforma interna de Microsoft analizaron 400 trabajos…* | Did Microsoft analyze them, or the researchers? | *Los autores analizaron 400 trabajos reales de la plataforma interna de aprendizaje profundo de Microsoft…* |

## 3. A relative clause has one possible antecedent

| Before | Problem | After |
| :--- | :--- | :--- |
| *…sigue sin lograrse, por la diversidad de retos de llevar modelos a producción que abarca.* | *Que abarca*: MLOps, the diversity or the challenges? | *…porque MLOps tiene un alcance amplio y aborda retos muy diversos para llevar modelos a producción.* |

## 4. Formal register, and qualifiers taken from the source

| Before | Problem | After |
| :--- | :--- | :--- |
| *aprovechar bien sus GPU* | Colloquial. | *optimizar el uso de sus GPU* |
| *una utilización bastante baja* | Subjective. | *una utilización notablemente baja* (the source says *rather low*) |

When the qualifier describes a finding from a source, take its strength from the source
(`../reference-writting/source-fidelity.md`, modality). *Significativamente* suggests a
statistical test, so use it only when the source reports one.

## 5. Internal identifiers stay out of the prose (added 2026-09-19)

Harness artifacts — requirement IDs (`FR-03.4`, `NFR-01`), ADR numbers, internal file names —
belong to the agents' context, not to the thesis reader. In rendered prose, **describe the
behavior or the decision**; the identifier lives only in `% [verify: ADR-NNN: ...]` comments,
where a `grep` can find it. A parenthetical pointing at "los requisitos del sistema" is the
same leak in disguise: the reader cannot open `requirements.md`, and requirement IDs mean
nothing in a document that ships on its own.

| Before | Problem | After |
| :--- | :--- | :--- |
| *…genere las alertas de diagnóstico automatizado que exige FR-03.4…* | Reader meets an ID that doesn't exist in their world. | *…genere alertas tempranas y active el diagnóstico automatizado de salud de los nodos…* |
| *…niveles de saturación críticos (definido en los requisitos del sistema para umbrales de VRAM superiores al 90 %)…* | The parenthesis cites an internal file as authority. | *…niveles de saturación críticos de la VRAM…* (the threshold, if it is ever decided, becomes prose of its own or a `[verify]` marker) |

The checklist grep catches raw IDs; the disguised ones (parentheticals, "conforme a
FR-…", "definido en los requisitos") are caught only by reading.

## 6. Checklist for a reviewed section

- [ ] Every detail passes the test in §1 for **this** section.
- [ ] Each paragraph follows from the previous one, with no jump to an unrelated actor or tool.
- [ ] Every verb has a subject the reader can identify without going back.
- [ ] No relative clause (*que*, *cuyo*, *el cual*) can be attached to two antecedents.
- [ ] No colloquial phrasing, and every qualifier on a cited finding is as strong as the source's.
- [ ] No colon splices (`puntuation.md` §4.3), em dashes (§4.1) or antithetical constructions (§4.2).
- [ ] No internal identifier (`FR-xx`, `NFR-xx`, `ADR-NNN`) or pointer to the harness files appears in the prose (§5).
