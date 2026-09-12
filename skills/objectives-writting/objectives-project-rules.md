# Objective-Writing Rules Specific to This Project

Rules the authors adopted on 2026-09-12 after the tutor reviewed the objectives of the
anteproyecto (ADR-028, now closed). They sit **on top of** the generic guidance in
[`objectives-definition.md`](./objectives-definition.md) and
[`objectives-avoid.md`](./objectives-avoid.md): where the generic guidance explains *how to
formulate* an objective, this file records what **this tutor and this faculty format** will
reject. When the two conflict, this file wins for the IAsLab PDG.

Same status as [`../reference-writting/recency.md`](../reference-writting/recency.md): a
project decision, not a general academic norm.

## Why these rules carry weight

The faculty format states it plainly: *"los objetivos definen los compromisos que se
adquieren por parte del investigador... es contra esta lista de objetivos que el lector y/o
revisor mide al finalizar la lectura el alcance y logro de cada uno de ellos"*
([`../../project-context/formato-anteproyecto.md`](../../project-context/formato-anteproyecto.md)).
An objective is not a description of intent. It is the contract the evaluator grades
against, so every word that is vague, doubled, or unmeasurable is a word that will be read
against the authors at the end.

## The rules

1. **One infinitive verb per objective.** Not two, not a verb plus a purpose-verb. *"Extender
   el sistema... para consolidar el ciclo de vida"* is two commitments wearing one sentence.
   Pick the verb that names what actually gets built or evaluated; express the rest as
   purpose (*"con el fin de..."*) or method (*"mediante..."*).

2. **No ambiguous adjectives.** The tutor named *"interactivas"* specifically. The test: can
   an evaluator point at the delivered artifact and say yes or no? *"visualizaciones
   interactivas"*, *"observabilidad avanzada"*, *"telemetría fina"* all fail it. Name the
   capability instead of grading it.

3. **No parenthetical enumerations inside the objective.** Lists such as *"(temperatura,
   VRAM, consumo energético)"* or *"(pregrado, electiva, semilleros y profesores)"* belong in
   the chapter that develops the objective, not in the objective. They inflate a one-page
   chapter and they commit the authors to every item in the list.

4. **No dates or durations inside an objective.** *"en ocho meses"* comes out. The timeline
   lives in the Cronograma of the Metodología chapter, where the format asks for it.

5. **No `[verify: ...]` or `\todo{}` markers inside an objective.** The tutor flagged this
   directly. If a threshold is still undecided, the objective is not ready to be written:
   open the entry in [`../../project-context/ADR.md`](../../project-context/ADR.md) and leave
   the objective for when the answer arrives. A commitment with a hole in it is worse than a
   commitment postponed.

6. **Measurable means a number or an observable artifact.** *"niveles satisfactorios de
   aceptación operacional"* is not measurable; *"soportar 20 usuarios simultáneos"* is. If the
   objective promises an evaluation, the criterion it will be evaluated against has to be in
   the sentence.

7. **The verb must match what the project really does.** The tutor's warning, verbatim:
   *"hay como unas ligerezas en verbos que ustedes utilicen y tengan cuidado porque va a haber
   quejas respecto a ello"* ([`../../project-context/meetings/2026-09-09-tutor-alcance-y-revision.md`](../../project-context/meetings/2026-09-09-tutor-alcance-y-revision.md)).
   *Extender* presupposes an existing system with that scope; if the project builds the base,
   the verb is *construir*, *desarrollar* or *implementar*. Choosing a verb that overstates
   invites the complaint; choosing one that understates gives away credit for work actually
   done.

8. **Design and implementation are different commitments.** If the artifact will be running
   at the end, the objective says so. *"Diseñar un esquema lógico de cuotas"* promised less
   than the project delivers, which is why the tutor corrected it: *"no solamente lo van a
   diseñar, plano. Ustedes van a hacer el sistema de cuotas"*. Note the interaction with
   rule 1: the answer is not *"diseñar e implementar"*, it is the single verb that already
   contains the design.

## Checklist before an objective is considered written

- [ ] Exactly one infinitive verb.
- [ ] No adjective an evaluator could not verify.
- [ ] No parentheses enumerating components.
- [ ] No date, duration, or deadline.
- [ ] No `[verify:]` / `\todo{}` marker.
- [ ] The measurable criterion is present, as a number or a nameable artifact.
- [ ] The verb states neither more nor less than the project will actually deliver.
- [ ] Taken together, the specific objectives cover the general objective, and none exceeds it.
