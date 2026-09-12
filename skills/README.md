# Skills

Every reference/procedure module an agent applies while working in this repository — as
opposed to `project-context/` (facts) and `thesis/` (the actual document). This file is the
**loading index**: before starting a task, find the row that matches it and load only that
row's modules. Loading modules a task doesn't need wastes context and, worse, invites
guidance meant for a different job (a meeting-extraction rule bleeding into thesis prose,
or vice versa).

## Load by task

| Task | Load | Don't load |
| :--- | :--- | :--- |
| **Draft or revise thesis prose** (Redactor) | [`agent-roles/Redactor.md`](./agent-roles/Redactor.md) · [`thesis-writing/`](./thesis-writing/README.md) · [`objectives-writting/`](./objectives-writting/README.md) (only if touching objectives) · [`parragraph-structure/`](./parragraph-structure/README.md) · [`reference-writting/`](./reference-writting/README.md) · [`writting-tools/`](./writting-tools/README.md) · [`latex/`](./latex/README.md) (if the LaTeX mechanics themselves are in question) | `meeting-insights/` |
| **Source or verify evidence** (Investigador) | [`agent-roles/Investigador.md`](./agent-roles/Investigador.md) · [`reference-writting/`](./reference-writting/README.md) | `meeting-insights/` · `parragraph-structure/` · `writting-tools/` |
| **Review a drafted section** (Revisor) | [`agent-roles/Revisor.md`](./agent-roles/Revisor.md) · [`thesis-writing/review-checklist.md`](./thesis-writing/review-checklist.md) · [`reference-writting/`](./reference-writting/README.md) · [`writting-tools/`](./writting-tools/README.md) · [`objectives-writting/`](./objectives-writting/README.md) (if objectives are in scope) · [`latex/references/troubleshooting.md`](./latex/references/troubleshooting.md) (only on a build failure) | `meeting-insights/` |
| **Plan/assign work, track status** (Coordinador) | [`agent-roles/Coordinador.md`](./agent-roles/Coordinador.md) | Everything else — delegate instead of loading it yourself |
| **Extract insights from a meeting transcript** | [`meeting-insights/`](./meeting-insights/README.md) **only** | `thesis-writing/` · `objectives-writting/` · `parragraph-structure/` · `reference-writting/` · `writting-tools/` · `latex/` — none of the writing-mechanics modules apply to extraction, and mixing them in risks the extraction rules absorbing thesis-style phrasing |
| **Fix the LaTeX build, add a package, touch the preamble** | [`latex/`](./latex/README.md) (`SKILL.md` + the relevant file under `references/`) | `meeting-insights/` · the prose-mechanics modules, unless the fix also touches wording |
| **Reorganize the harness itself** (this repo's structure, `CLAUDE.md`, READMEs) | Just [`../CLAUDE.md`](../CLAUDE.md) and this file | None of the content modules below — their guidance doesn't bear on repo structure |

If a task doesn't match a row above, it's probably a Coordinador judgment call: read
`agent-roles/README.md` for the full role split, then load the specific module(s) that
role's brief points to — don't load the whole `skills/` tree "to be safe."

## What's in here

| Module | What it's for |
| :--- | :--- |
| [`agent-roles/`](./agent-roles/README.md) | The four-role workflow (Coordinador, Investigador, Redactor, Revisor) that the table above is organized around. |
| [`thesis-writing/`](./thesis-writing/README.md) | Global thesis workflow: scoping, outlining, drafting moves, macro/micro review. |
| [`objectives-writting/`](./objectives-writting/README.md) | Formulating and auditing General/Specific Objectives (SMART, Verb+Variable+Context+Purpose). |
| [`parragraph-structure/`](./parragraph-structure/README.md) | Paragraph architecture: the tri-part model, 7 development typologies, 6 opening strategies. |
| [`reference-writting/`](./reference-writting/README.md) | APA 7th citation mechanics: direct quotes, paraphrasing, attribution boundaries. |
| [`writting-tools/`](./writting-tools/README.md) | APA formatting, paragraph mechanics, punctuation — including the banned-AI-tells rule (§4 of `puntuation.md`). |
| [`latex/`](./latex/README.md) | LaTeX preamble, build tooling, and citation/package conventions specific to this project's toolchain. |
| [`meeting-insights/`](./meeting-insights/README.md) | Turns a pasted meeting transcript into a traceable record in `../project-context/meetings/`. Self-contained — it doesn't use, and isn't used by, any other module in this folder. |

## Why `meeting-insights/` stays isolated

Every other module here shapes *how the thesis reads*. `meeting-insights/` shapes *how a
transcript becomes a record* — a different task, with its own output location
(`project-context/meetings/`, not `thesis/`) and its own failure mode (a garbled quote
becoming a false record, not a stylistic slip). Loading the writing-mechanics modules
during extraction, or the extraction rules during drafting, is how the two failure modes
start bleeding into each other. Keep the two loads separate even when the same agent does
both in one session — one task, then the other, not both at once.
