# Source Fidelity for Indirect Citations

A rule the authors added on 2026-09-13, specific to this project and stricter than APA 7th.
APA only asks that a paraphrase be attributed. This rule decides **what a paraphrase is allowed
to attribute**. It applies before the mechanics in `indirect-reference.md` and next to the age
limit in `recency.md`.

## The rule

An indirect citation may attribute to a source **only what that source says, in its own
terms**. Every technical term, figure, qualifier and claim in the sentence that carries the
citation must trace back to a passage of the cited document. The passage must be the source's
**own** statement or finding, not something the source attributes to someone else.

The authors' own reading (why a finding matters for the IAsLab, what the project takes from
it) is allowed and useful. It goes in **its own sentence, without the citation**, so the reader
can see where the source ends and the authors begin.

**Why (from the authors):** the tutor had already flagged citations in the draft as *"algunas
forzadas"* (commit `fb9ee6b`). On 2026-09-13 the authors checked chapter 01's *Contexto*
against the full texts and found the paragraph attributing to Kreuzberger et al. and Lima et
al. "gobernanza de acceso, cuotas y telemetría de infraestructura". None of those words appear
in either paper. A citation that makes the literature say what the project needs it to say is
the fastest way to lose an evaluator's trust, because anyone who opens the paper can check it.

## Failure patterns found in this document

Every row below happened in this thesis, and the fix is what the text says now.

| Pattern | What happened | Fix |
| :--- | :--- | :--- |
| **Term injection** | "Kreuzberger et al. y Lima et al. confirman que la gobernanza de acceso, las cuotas y la telemetría de infraestructura son prácticas centrales". Neither paper uses *quota*, *telemetry* or *access governance*. | Say what they do say: the MLOps definition (conceptualization, implementation, monitoring, deployment, scalability) and the monitoring component. |
| **Selection criterion reported as a finding** | "Gao et al. reportan una utilización promedio de GPU igual o inferior al 50 %". The ≤ 50 % was the threshold used to **select** the 400 jobs, not a result. | "400 trabajos … elegidos entre los que usaban en promedio el 50 % o menos de sus GPU". |
| **Unit drift** | "el 84.99 % de los casos". The paper counts 706 *issues*, several per job. | "706 problemas de baja utilización, el 84.99 % corregible…". |
| **Dropped hedge or added intensifier** | "Sculley et al. muestran que [X] es la fuente principal de la deuda técnica". The paper never ranks a main source, and it says the debt *may be* difficult to detect. | Keep the source's modality: *puede*, *sugieren*, *señalan*. Never add *principal*, *siempre*, *confirma* unless the source does. |
| **Secondhand attribution** | Citing Lima et al. for a claim that appears in their background section attributed to another study (for example, that monitoring is among the most relevant MLOps activities, which Lima et al. credit to Cardoso Silva et al.). | Cite the review's own findings (its RQ answers and conclusions), or go to the original study. |
| **Interpretation fused with the citation** | "Esta línea de base … justifica que el IAsLab busque mecanismos de observación y gobernanza equivalentes a los que documenta la literatura". Gao et al. document no governance mechanism, and "línea de base" is not their term. | Put the connection to the project in a separate sentence without the citation, and make it state only what the source supports (Prometheus and DCGM are what Gao et al. describe). |

## Procedure before a citation enters the thesis

1. **Work from the full text.** Not the abstract, not a blog summary, not an AI summary, not
   another paper's description of it. Look for it in the order set by
   [`../../fuentes/README.md`](../../fuentes/README.md) (open access, then the university's
   licensed portals, ACM Digital Library first, then preprints), save it as
   `fuentes/pdf/<bibtex-key>.pdf` and add its row to `fuentes/INDEX.md`. If the portal blocks the
   download, ask a person to fetch it; don't fall back to the abstract.
2. **Find the passage.** Note the page and section. `pdftotext` does not extract text inside
   figures: if the claim rests on a figure, render the page (`pdftoppm`) and look at it.
3. **Check whose statement it is.** Is it the source's own finding, definition or conclusion?
   If the source is citing someone else there, either cite the original or drop the claim.
4. **Term check.** List the technical terms and numbers in the sentence you are about to
   write. Each one must appear in the passage, or be a direct translation of a term that does.
   One that doesn't either leaves the cited sentence or moves to the authors' own sentence.
5. **Modality check.** Match the source's hedging (`indirect-reference.md` §6, *Attribution
   Distortion*).
6. **Record it** in [`../../thesis/CITAS-VERIFICADAS.md`](../../thesis/CITAS-VERIFICADAS.md):
   the thesis location, the claim as written, the literal passage in the original language with
   its locator, and the version of the document consulted.
7. **Only then write the sentence.**

A citation without a ledger entry is unverified. The Revisor does not approve a section that
contains one, and the Redactor does not keep one in new text: it becomes `\citep{cite_needed}`
plus an ADR entry, per `CLAUDE.md` rule 7.

## Scope

- Applies to every indirect citation in `thesis/`, new or already written. Existing ones are
  verified chapter by chapter during the human review passes (`skills/revision-humana/`), and
  each check is recorded in the ledger even when the citation turns out to be correct.
- Direct quotations already require the literal text and a locator (`direct-reference.md`);
  this rule brings indirect citations to the same level of checkability.
- It does not apply to `project-context/` facts, which are cited as project facts, not as
  literature.
