# Agent Roles

This directory defines the multi-agent workflow used to write the IAsLab PDG thesis in this repository. Each file is the persona/brief for one role. Splitting the work this way keeps each agent's context small and focused, and reduces the two failure modes this harness is designed against: **hallucinated content** (invented data, sources, or requirements) and **inconsistent structure** (chapters that drift from the approved outline or from each other).

## The roles

| Role | File | One job |
| :--- | :--- | :--- |
| Coordinator | [`Coordinador.md`](./Coordinador.md) | Plans the work, breaks a request into tasks, assigns them to the right role, tracks overall thesis status. Never writes prose itself. |
| Researcher | [`Investigador.md`](./Investigador.md) | Gathers and verifies evidence — project facts from `project-context/`, external literature, citations. Never drafts prose. |
| Writer | [`Redactor.md`](./Redactor.md) | Drafts chapters/sections/paragraphs from approved outlines and verified evidence, following the `thesis-writing/`, `objectives-writting/`, `parragraph-structure/`, and `writting-tools/` modules. |
| Reviewer | [`Revisor.md`](./Revisor.md) | Runs the micro/macro review passes, checks citations and structure, validates the LaTeX build. Never rewrites content wholesale — flags issues and hands them back. |

## Standard workflow

```text
User request
     │
     ▼
Coordinador  ──► breaks the request into tasks, checks the outline/status
     │
     ├──► Investigador  ──► evidence, sources, verified facts, flagged gaps
     │
     ├──► Redactor       ──► draft prose / LaTeX using that evidence
     │
     └──► Revisor        ──► micro + macro review, citation check, build check
                               │
                               └──► back to Coordinador for the next task
```

A single agent (or the user) can play more than one role in a given session, but should still follow the brief for whichever role it is acting as — this keeps output predictable regardless of who (or what model) is doing the work.

## Rules that apply to every role

These supplement the harness-wide rules in the repository root [`CLAUDE.md`](../../CLAUDE.md) — read that file first.

1. **Don't invent facts, requirements, or citations.** If evidence is missing, the Redactor asks the Investigador or flags it with `[cite_needed]` / `[verify]` — it does not fill the gap with plausible-sounding content.
2. **Respect the approved outline.** Nobody restructures chapters/sections unilaterally; structural changes go through the Coordinador and, once accepted, must be reflected back into the relevant module (and the root `README.md`, per the structure-change rule).
3. **All generated/temporary output goes in [`compiled-output/`](../../compiled-output/README.md)**, never into the source module folders.
4. **Reuse the existing modules** — `project-context/` for facts about the project, `objectives-writting/` for objectives, `parragraph-structure/` and `writting-tools/` for prose mechanics, `reference-writting/` for citations, `thesis-writing/` for the overall chapter workflow, `latex/` for LaTeX-specific mechanics (preamble, build, citation commands, cross-references). Don't re-derive guidance that already lives in one of these.
5. **The actual thesis text lives in [`thesis/`](../../thesis/README.md), one file per chapter.** Read `thesis/STATUS.md` for the overview and only the chapter file(s) a task actually concerns — never load the whole document into context by default.
