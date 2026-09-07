# Harness Rules for This Repository

This repository is a writing harness for an academic thesis (PDG, Universidad Icesi) — a set of reference modules plus an agent-role workflow. These rules apply to every agent working in this repo, regardless of which role (see [`agent-roles/`](./agent-roles/README.md)) it is acting as.

## Structural rules

1. **Any change to the repository's folder/file structure must be followed by an update to the root [`README.md`](./README.md)** (the architecture tree, the module summary table/list, and any installation or usage instructions it affects). This applies to adding, removing, renaming, or repurposing a top-level folder or a module's file set — not to routine edits inside an existing file. Do this in the same change, not as a follow-up.
2. **Generated/temporary/compiled output goes in [`compiled-output/`](./compiled-output/README.md), never in a source module folder.** This includes LaTeX build artifacts (`.aux`, `.log`, `.out`, `.pdf`, `.synctex.gz`), draft exports, and any other throwaway file produced while working.
3. **Reuse existing modules instead of re-deriving guidance.** Project facts live in `project-context/`; thesis workflow and structure in `thesis-writing/`; objectives rules in `objectives-writting/`; paragraph mechanics in `parragraph-structure/`; citation rules in `reference-writting/`; formatting/orthography in `writting-tools/`; LaTeX-specific configuration, build rules, and a dedicated skill in `latex/`. Don't improvise LaTeX conventions (packages, citation style, preamble changes) — `latex/SKILL.md` and `latex/references/` already cover this project's toolchain.
4. **The actual thesis text lives only in [`thesis/`](./thesis/README.md).** Read `thesis/README.md` before touching it — it explains why the document is split one file per chapter and which file(s) a given task actually needs. Don't load the whole thesis into context when a task only concerns one chapter; check `thesis/STATUS.md` for the overview instead.

## Workflow rule

5. **Follow the role workflow in [`agent-roles/`](./agent-roles/README.md)** when doing substantive thesis work: Coordinador plans and assigns, Investigador sources evidence, Redactor drafts, Revisor checks. Don't skip Investigador/Revisor to save a step — the whole point of the split is to prevent invented facts and structural drift.

## Content rules

6. **Never invent facts, requirements, technical details, or citations.** Anything about the IAsLab project must trace back to `project-context/`; anything about outside literature must be a real, checkable source. If evidence is missing, flag it (`[cite_needed]`, `[verify: ...]`) rather than filling the gap with something plausible-sounding.
7. **Every gap that needs a human decision gets an entry in [`project-context/ADR.md`](./project-context/ADR.md).** Marking `[verify: ...]` in the text is only half the job: the marker must name an ADR id (`[verify: ADR-012 — ...]`) and the matching entry must record *where* the gap is used, so whoever applies the answer finds it with a `grep` instead of re-reading the document. When a question is answered and applied, **delete its entry** — that file holds only what is still open.
