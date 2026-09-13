---
name: revision-humana
description: Human-driven correction pass over one specific part of the thesis (a section, subsection, paragraph, objective or table), or a sweep over a whole chapter. Only a person invokes it, with /revision-humana <apartado> [feedback]. The feedback that person writes in the chat is the only thing applied to the text. The AI may add suggestions in a separate block, applied only if the person approves each one by id. Every applied item is logged in thesis/REVISIONES.md with its origin.
argument-hint: <apartado> [feedback]
disable-model-invocation: true
---

# Revisión humana de un apartado

## Why this exists

The harness already has AI roles that draft and review the thesis (Redactor, Revisor in
`../agent-roles/`). What it lacked is a pass where **a person decides what changes**. The
tutor judged the second draft as *"buena forma y mal fondo"*. Substance problems like that
are not caught by an AI reviewing AI prose, and letting the AI decide its own corrections is
exactly how the document drifts toward sounding machine-written.

This skill inverts the roles. The person is the only source of corrections. The AI resolves
where the text is, applies what the person asked, checks that the project rules still hold,
and keeps the record. It may point things out, but its observations stay proposals until
the person approves them one by one.

Everything the person sees (text excerpts, reports, questions, the log) is **in Spanish**.

## Locating the repository

The repository root is the directory that contains `CLAUDE.md` and `thesis/`. This file
lives at `<root>/skills/revision-humana/SKILL.md`. Sessions are sometimes started from a
sibling folder (`../workspace`), where the root is `../pdg-writtting`. Resolve it before step
1 and use absolute paths.

## Hard rules

1. **Only human feedback changes the text.** Human feedback means what the person writes in
   this conversation after invoking the skill, including the invocation arguments. These
   **do not count**: your own review, meeting records in `project-context/meetings/`,
   `\todo{}` or comments left by agents, notes from previous sessions, and suggestions from
   an earlier round that nobody approved.
2. **AI suggestions never touch the text without item-specific approval.** Valid approvals
   name the suggestion: *"aplica S2"*, *"S1 sí, pero sin la segunda frase"*. A generic *"ok"*,
   *"dale"* or *"siguiente"* approves **no** suggestion. An approved suggestion is logged as
   *sugerencia IA aprobada por <persona>*, never as human feedback.
3. **Scope lock.** Edit only the lines of the requested apartado. If an item needs a change
   elsewhere (a renamed `\label`, an objective whose wording ripples into chapters 07 and 08,
   `STATUS.md`), list the ripple and ask. Don't edit outside the apartado without a yes.
4. **Project rules still bind** ([`../../CLAUDE.md`](../../CLAUDE.md) rules 6 to 9,
   [`ortografia-rae.md`](../writting-tools/ortografia-rae.md),
   [`puntuation.md`](../writting-tools/puntuation.md) §4, [`nivel-de-detalle.md`](../writting-tools/nivel-de-detalle.md),
   [`objectives-project-rules.md`](../objectives-writting/objectives-project-rules.md) when
   the apartado is an objective, [`recency.md`](../reference-writting/recency.md) when a
   citation is involved). If a human item conflicts with one of them (it asks for an em
   dash, cites a meeting, asserts a fact that is not in `project-context/`), don't apply it
   silently and don't drop it silently. Say which rule it conflicts with, in one line, and
   ask how to proceed.
5. **Facts and citations still need a real origin.** If an item needs a project fact that
   is not in `project-context/`, offer two paths. Either the person supplies it and approves
   the exact line to add to `project-context/`, or the text gets a `[verify: ADR-NNN — ...]`
   marker plus an entry in `project-context/ADR.md`. If an item needs literature, search for
   a real, checkable source, show it to the person (author, year, venue, the sentence it
   supports), and apply it only after approval.
6. **Never commit.** The person reviews the diff and commits.

## Step 1: Resolve the apartado

Accepted forms, all matched against `thesis/chapters/*.tex`:

| Form | Example |
| :--- | :--- |
| Chapter number or file | `cap05`, `05-marco-teorico` |
| `\label` | `sec:gobernanza-recursos-compartidos`, `obj:gobernanza`, `tab:cronograma` |
| Section title fragment | `"Justificación"`, `"riesgos"` |
| Paragraph inside a section | `sec:identidad-rbac ¶2` |

Use `grep -n` on labels and `\section{`/`\subsection{` titles. If more than one place
matches, list the candidates with `file:line` and ask. A whole chapter, or several
sections, switches to **barrido** mode (step 5).

Show the person:

- `archivo:línea_inicio–línea_fin`.
- The actual text split into numbered paragraphs `¶1 … ¶n`, each prefixed with its first
  line number. Make it readable: `\emph{x}` → *x*, `\citet{clave}` → `(clave)`, drop `\,`
  and similar spacing macros. Keep every word. **Don't summarize.** The person has to read
  the real text to give feedback on it.

Load only what the apartado needs: the chapter's header comment (it states what the chapter
must and must not contain), the rule files from hard rule 4 that apply, and the
`project-context/` passages the apartado draws facts from. Don't load the rest of the
thesis. Check `thesis/STATUS.md` for the chapter's page limit.

## Step 2: Collect the human feedback

- **Feedback given with the invocation:** split it into items `F1 … Fn`. Each item quotes the
  person's words literally and names the `¶` it refers to. Infer the `¶` only when there is a
  single reasonable reading; otherwise ask before applying that item (apply the clear ones).
- **No feedback given:** show the text (step 1) and your suggestions (step 3) and ask for
  feedback. Apply nothing.

## Step 3: AI suggestions (separate block, optional)

At most 5, limited to the apartado, under the heading **«Sugerencias de la IA (no
aplicadas)»**. Each one carries:

- an id (`S1 …`) and the `¶`;
- the problem, in one line;
- what backs it: a rule (`ortografia-rae.md §3`), a contradiction (`requirements.md FR-02.4`),
  a claim without support, a missing link to its objective (the Marco teórico format
  requires it);
- the proposed rewrite, in two lines at most.

Prefer checkable problems (rule violations, contradictions with `project-context/`,
unsupported claims, broken links to the objectives) over matters of taste. If there is
nothing worth raising, write *«Sin sugerencias»*. Never pad the list.

**Order.** If there are `F` items, apply them first (step 4) and show the suggestions
afterwards, over the updated text. If there are none, show text and suggestions together
and wait.

## Step 4: Apply and verify

For each approved item (`F`, or an `S` approved by id), make the minimal edit that satisfies
it. Don't restyle surrounding sentences the item didn't ask about.

Then verify:

1. `cd thesis && make build`: zero `Citation ... undefined` and `Reference ... undefined` in
   `../compiled-output/latex-build/main.log`.
2. Length: report how many pages the chapter now takes (start page of the **next** chapter
   in `../compiled-output/latex-build/main.toc`). The authors decided on 2026-09-13 not to
   apply the faculty format's maximum lengths, so this is information for the person, not a
   reason to trim on your own.
3. The `grep` checks in `puntuation.md` §5 and `ortografia-rae.md` §4, on the edited file.

Report per item, in Spanish:

```text
F1 ✓ ¶2 «…texto anterior…» → «…texto nuevo…»   (líneas 49–50)
F2 ✗ no aplicado: pide citar la reunión del 09-09 (regla 9). ¿Lo paso a project-context/?
S3 ✓ aprobada por Melo · ¶4 «…» → «…»
Compilación: OK · Cap. 5 sigue empezando en p. 10 · greps: sin hallazgos
```

Then the pending suggestions block, if any.

## Step 5: Barrido mode (chapter or several sections)

Walk the sections in document order, **one at a time**:

1. Show the section (step 1) and its suggestions (step 3).
2. Wait for the person. Feedback → apply and report (step 4). *«siguiente»* or *«ok»* with no
   items → no change; log the section as *revisado sin cambios*.
3. Continue with the next section.

The person can stop at any point (*«paramos aquí»*). Record in the log where the sweep
stopped. `/revision-humana cap05 --continuar` resumes from the first section the log does
not mark as reviewed.

## Step 6: Log

Append one block per invocation to `thesis/REVISIONES.md`. It is the record that every change
came from a person. Use the name from `git config user.name`, or ask once if it's empty.

```markdown
### 2026-09-13 · cap05 · sec:gobernanza-recursos-compartidos

- **Revisó:** Juan Camilo Melo López
- **F1** (humano, ¶1): «suena a definición de diccionario, conectarlo con la sala 104M» → aplicado · líneas 49–50
- **F2** (humano, ¶2): «citar lo que dijo el tutor» → no aplicado: regla 9, pendiente de promover a project-context
- **S2** (IA, aprobada por Juan Camilo Melo López): repetición de «reserva» → aplicado
- **S1** (IA): no aprobada
- **Barrido:** completo · o · detenido antes de sec:identidad-rbac
```

Quote human feedback literally in the log, the same way meeting records quote speakers.
Don't change the status column of `thesis/STATUS.md`: only the person declares a section
`approved`. If they do, update the row and name the reviewer in its notes.

## What this skill never does

- Apply its own suggestions without approval by id.
- Edit outside the apartado without a yes.
- Treat meeting records, agent-written `\todo{}`, or its own earlier suggestions as human
  feedback.
- Summarize the text instead of showing it.
- Commit.
