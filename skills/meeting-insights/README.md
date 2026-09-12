# Meeting Insights Module

This module turns a meeting transcript — pasted into the chat, never committed — into a
durable, traceable record in [`meetings/`](../../project-context/meetings/README.md).

---

## Purpose

1. **Stop losing decisions to speech.** Scope calls, confirmed figures, and tutor
   instructions get settled in meetings and then exist nowhere the harness can read. Every
   session afterwards re-derives them, or worse, re-flags them as open.
2. **Close the loop with [`project-context/ADR.md`](../../project-context/ADR.md).** That file
   registers the questions blocking the document, each with the exact file and marker where
   its answer goes. Meetings are where those questions actually get answered — this module
   is what connects the two.
3. **Surface contradictions with `project-context/`.** A meeting is the most common way the
   project's ground truth becomes wrong. Catching it here costs one edit; catching it at
   evaluation costs credibility.
4. **Keep speech from becoming a citable fact by accident.** Transcripts mishear technical
   vocabulary and mis-attribute speakers. The module's output is explicitly *proposed*
   evidence: every line carries a literal quote, and a human decides what gets promoted.

## File Overview

| File | Description |
| :--- | :--- |
| [`SKILL.md`](./SKILL.md) | The skill agents load when a transcript arrives — procedure, output template, and the hard limits on what it may edit. |
| [`extraction-guide.md`](./extraction-guide.md) | The extraction rules: mandatory literal quotes, the decided/committed/suggested/discussed split, uncertain attribution, and the two cross-checks. |

The output lives in [`meetings/`](../../project-context/meetings/README.md) — one file per meeting plus an
index — not in this folder. Same split as [`latex/`](../latex/README.md) (rules) versus
[`thesis/`](../../thesis/README.md) (content).

## How it fits the harness

- **Role:** this is [`Investigador`](../agent-roles/Investigador.md) work — sourcing and
  verifying evidence and flagging what it could not verify. No new role was added; a
  transcript is just another source that must be quoted with a locator.
- **Boundary:** the skill writes **only** into `project-context/meetings/`. It never edits `ADR.md`,
  `thesis/`, or `project-context/*.md`, even when a meeting plainly answers an open
  question. It names what should change; a human approves; the normal role workflow applies
  it.
- **Rule 6 of [`CLAUDE.md`](../../CLAUDE.md)** ("never invent facts") is what the whole module
  is built around. A sentence from a meeting is a candidate fact, not a fact.

## Usage

Paste the transcript into the chat and ask for the insight:

```text
"Aquí va la transcripción de la reunión con el tutor del 7 de septiembre: <...>
 Extrae los insights con la skill meeting-insights."
```

The agent will read the open ADR entries first, extract into the template, write
`project-context/meetings/AAAA-MM-DD-<slug>.md`, add its row to `project-context/meetings/INDEX.md`, and report back which
ADR entries the meeting appears to answer and any contradiction it found.

If the transcript is too long to fit in context, save it to the session scratchpad and point
the agent at the file — it will read it in slices rather than skim it.
