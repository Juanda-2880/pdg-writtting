# Academic & Thesis Writing Skills Suite (PDG Writing)

An integrated, modular AI-agent skills suite and reference system for planning, structuring, drafting, citing, and reviewing academic research, empirical theses, dissertations, undergraduate capstone projects (PDG / TFG), and master's theses (TFM).

The suite is intentionally format-neutral: it supports Markdown, LaTeX, Word-oriented prose, and Google Docs workflows, prioritizing academic rigor, logical coherence, and empirical precision.

---

## Provenance & Attribution (Fork Information)

> [!NOTE]
> This project builds upon and extends the work from [santifs/thesis-writing-skill](https://github.com/santifs/thesis-writing-skill), from which it was originally forked.
>
> While the original repository provided the core `thesis-writing` skill, this repository significantly broadens the scope into a comprehensive, modular suite by adding dedicated modules for:
> - Degree Project Context, Requirements & Technologies (`project-context/`)
> - Research Objectives Definition & Pitfall Avoidance (`objectives-writting/`)
> - Academic Paragraph Architecture & Typologies (`parragraph-structure/`)
> - Academic Citations & APA 7th Referencing (`reference-writting/`)
> - Academic Writing Tools, Punctuation & Formatting Conventions (`writting-tools/`)

---

## Suite Architecture & Modules

The repository separates *how to write* from *what is true about the project*: every reference/procedure module (workflow, LaTeX, citations, punctuation, meeting extraction, agent roles) lives under `skills/`, everything that is fact or open-question about the IAsLab project (including raw meeting evidence) lives under `project-context/`, and the actual thesis document is its own top-level module:

```text
pdg-writtting/
├── CLAUDE.md                # Harness-wide rules every agent must follow
├── compiled-output/          # Scratch directory for generated/compiled artifacts (gitignored)
├── thesis/                   # The actual thesis document — one file per chapter, see thesis/README.md
├── project-context/          # Institutional PDG charter, requirements, tech stack & open questions (ADR.md)
│   └── meetings/              # Meeting insights: one traceable record per meeting, plus INDEX.md
└── skills/                   # Every reference/procedure module an agent applies while writing
    ├── README.md              # Loading index: which modules a given task needs, and which it doesn't
    ├── agent-roles/           # Multi-agent workflow: Coordinador, Investigador, Redactor, Revisor
    ├── latex/                 # LaTeX config, build rules & skill (preamble, Makefile, citation setup)
    ├── meeting-insights/      # Turns a pasted meeting transcript into a record in project-context/meetings/
    ├── thesis-writing/        # Global thesis orchestration & end-to-end workflow (from upstream)
    ├── objectives-writting/   # Formulation & audit of research objectives
    ├── parragraph-structure/  # Academic paragraph architecture & typologies
    ├── reference-writting/    # Attribution, direct quotes & paraphrasing (APA 7th)
    └── writting-tools/        # APA formatting, paragraph mechanics & punctuation
```

> [!TIP]
> Before loading any module under `skills/`, check [`skills/README.md`](./skills/README.md) — it's a task → module table (drafting thesis prose, sourcing evidence, reviewing a section, extracting a meeting, fixing the LaTeX build, ...) that says exactly which modules a given task needs and which to leave unloaded. `meeting-insights/` in particular is meant to be loaded **alone**, never alongside the prose-mechanics modules.

---

## Module Summaries

### 1. [`project-context/`](./project-context/README.md)
The empirical ground truth and architectural specifications for the IAsLab Degree Project (PDG):
- **Project Charter:** Universidad Icesi official scope, background, objectives, and deliverables.
- **System Requirements:** Functional requirements (model provisioning, Fair-Share quotas, 20% overbooking, SAAMFI RBAC, hardware telemetry, benchmark harness) and non-functional constraints.
- **Technology Stack:** Multi-tiered architecture encompassing Kubernetes, KubeRay, NVIDIA GPU Operator, LiteLLM Proxy, vLLM, Ollama, LGP monitoring stack (Loki/Prometheus/Grafana), and DCGM telemetry.
- **Anteproyecto Format:** The faculty's official section-by-section format the thesis document follows.
- **`ADR.md` — Open-questions register:** The single list of unresolved doubts blocking the document, each recorded with the exact file and marker where it is used so another agent can apply the answer with a `grep` instead of re-reading the thesis. Entries are deleted, not archived, once resolved.
- **`meetings/`** (see module 11 below): meeting evidence lives here, nested under project-context, because it is project-related material, but it stays *proposed* evidence until a human promotes a claim into `requirements.md`/`technologies.md` — never treat a row in `meetings/` as an established project fact.

### 2. [`skills/thesis-writing/`](./skills/thesis-writing/README.md)
The central workflow module governing the full lifecycle of an empirical research thesis:
- **Scoping & Definition:** Transforming a broad topic into a research question, identifying research gaps, and verifying feasibility.
- **Outlining:** Detailed chapter and subsection architectures for undergraduate (TFG), master's (TFM), and doctoral dissertations.
- **Drafting:** Academic writing moves (Claim $\rightarrow$ Evidence $\rightarrow$ Interpretation), keeping Results factual and Discussion interpretive.
- **Macro & Micro Review:** Auditing flow, structural transitions, tone, and empirical consistency.

### 3. [`skills/objectives-writting/`](./skills/objectives-writting/README.md)
Specialized guidelines for formulating and evaluating research objectives:
- **Hierarchy:** Clear boundary between 1 General Objective (terminal contribution) and 3–5 Specific Objectives (tactical milestones).
- **Standards:** Strict enforcement of SMART criteria, syntactic formula ($Verb + Variable + Context + Purpose$), and Bloom's Taxonomy cognitive alignment.
- **Anti-patterns:** Identifying and fixing common errors, including confusing operational activities with objectives, compound verbs, and unmeasurable statements.

### 4. [`skills/parragraph-structure/`](./skills/parragraph-structure/README.md)
Frameworks for building self-contained, cohesive micro-arguments:
- **Tri-Part Model:** *Fase Organizadora* (Topic sentence/claim), *Contenido* (Empirical evidence and analysis), and *Fase de Cierre* (Local conclusion/transition).
- **Typologies:** 7 development patterns (Concept Definition, Problem-Solution, Cause-Effect, Comparison-Contrast, Sequence, Enumeration, Framing).
- **Opening Strategies:** 6 introductory paragraph styles (Synthesis, Assertive Claims, Epigraph/Quote, Guiding Questions, Analogy, Critical Incident).

### 5. [`skills/reference-writting/`](./skills/reference-writting/README.md)
Ethical and technical standards for attributing external scholarship under APA 7th:
- **Direct Quotations:** Explicit guidelines for short in-text quotes (<40 words) and indented block quotations ($\ge 40$ words) with mandatory locators (`p.`, `pp.`, `para.`).
- **Indirect Citations & Paraphrasing:** Synthesis of single and multi-source literature, narrative vs. parenthetical citations, and reporting verb taxonomies.
- **Error Avoidance:** Preventing patchwriting, quote over-reliance, and attribution boundaries blurring.

### 6. [`skills/agent-roles/`](./skills/agent-roles/README.md)
The multi-agent workflow that turns the modules above into a repeatable writing process:
- **Coordinador:** Plans tasks, assigns work, tracks thesis status; the only role that makes structural decisions.
- **Investigador:** Sources and verifies evidence from `project-context/` and outside literature; flags gaps instead of guessing.
- **Redactor:** Drafts prose/LaTeX from approved outlines and verified evidence, applying the modules above.
- **Revisor:** Runs the micro/macro review checklist, checks citations and structure, validates the build.

### 7. [`compiled-output/`](./compiled-output/README.md)
A gitignored scratch directory where agents write generated or compiled artifacts (LaTeX build files, draft exports, test compilations) so the source modules stay clean.

### 8. [`skills/latex/`](./skills/latex/README.md)
LaTeX configuration, build tooling, and a dedicated skill so agents don't reinvent the toolchain each session:
- **Preamble & build**: a ready-to-copy `preamble.tex`, `Makefile`, and `latexmkrc` (report class, Spanish/babel, `latexmk`, output routed to `compiled-output/`).
- **APA 7 citations in LaTeX**: `natbib` + `apalike`, chosen to match `skills/reference-writting/` and `skills/writting-tools/normas-APA.md`.
- **Semantic-markup rules**: correct `description`/`itemize`/`enumerate` use, `cleveref` cross-references, `csquotes` quotations, `booktabs`/`longtable` tables.

### 9. [`thesis/`](./thesis/README.md)
The actual thesis document — real, submittable content, not guidance:
- **One file per chapter/section** under `chapters/`, so an agent can read/edit a single section instead of loading 60+ pages of prose into context.
- **Anteproyecto structure**: the document currently follows the faculty's *anteproyecto* format (`project-context/formato-anteproyecto.md`) — Motivación y antecedentes, Descripción del problema, Hipótesis y restricciones, Objetivos, Marco teórico, Estado del arte, Metodología, Contribución y resultados, Anexos — **not** the final-thesis structure in `skills/thesis-writing/structure.md`.
- **`STATUS.md`**: the single source of truth for what's drafted/under review/approved, plus the standing structural decisions, kept current by the Coordinador role.
- **`main.tex`**: a thin skeleton (`\input{../skills/latex/preamble}` + front matter + `\include{chapters/...}`) — never the place to "see the whole thesis."

### 10. [`skills/writting-tools/`](./skills/writting-tools/README.md)
Technical reference manuals and orthographic conventions:
- **APA 7th Standard:** Margins, font recommendations, 5-level heading hierarchy, empirical table/figure structures, and reference lists.
- **Paragraph Integration:** Informational flow, the Given-New principle, and avoiding loose demonstratives.
- **Punctuation Precision:** Mandatory rules for *Punto y Seguido*, *Punto y Aparte*, citation punctuation, comma splices, semicolons, and dashes.
- **Banned AI tells (§4):** the em dash (`—`) as a parenthetical, and the antithetical `no es X, es Y` construction — both prohibited in the thesis text, with the substitution table and the `grep` checks that verify it.

### 11. [`skills/meeting-insights/`](./skills/meeting-insights/README.md)
Turns a meeting transcript, pasted into the chat and never committed, into a durable record in `project-context/meetings/`:
- **Traceable extraction:** every recorded claim carries a literal quote and a timestamp; a line without one does not enter the file.
- **Four buckets, not one:** decided / committed / suggested / merely discussed are kept apart, so a tutor's passing suggestion never reads as an instruction.
- **Two cross-checks:** which entries of `project-context/ADR.md` the meeting answers, and where what was said contradicts what `project-context/` already states.
- **Proposes, never applies:** the skill writes only into `project-context/meetings/`; promoting a spoken fact into the rest of `project-context/` or the thesis is a separate, human-approved step.

### 12. [`project-context/meetings/`](./project-context/meetings/README.md)
The output of the module above: one Markdown file per meeting (`AAAA-MM-DD-<slug>.md`) plus `INDEX.md`, the one-row-per-meeting summary an agent reads before opening any full record. Raw transcripts are deliberately not versioned. Nested under `project-context/` because it is project-related evidence, but see module 1's note above: it is *proposed*, not established, until a human promotes it.

---

## Recommended AI Agent Usage

Instruct your AI coding or writing assistant to leverage the relevant module based on your task:

```text
# Referencing Project Requirements & Architecture
"Consult project-context/requirements.md and technologies.md to check our GPU telemetry specifications."

# Planning & Scoping Objectives
"Use the objectives-writting skill to evaluate my proposed General and Specific Objectives."

# Structural Outlining & Drafting Chapters
"Use the thesis-writing skill to outline my Methodology chapter and review it against structure.md."

# Paragraph Development & Argumentation
"Apply the paragraph-structure skill to draft a Problem-Solution paragraph discussing our database bottleneck."

# Referencing & Attribution
"Use reference-writting and writting-tools to format these external citations and tables according to APA 7th."

# Capturing what was decided in a meeting
"Aquí va la transcripción de la reunión con el tutor: <...>. Extrae los insights con meeting-insights."

# Multi-agent thesis writing (Claude Code)
"Act as the Coordinador (see skills/agent-roles/) and plan the next task for drafting Chapter 3."
```

For Claude Code specifically, [`CLAUDE.md`](./CLAUDE.md) is loaded automatically and defines the harness-wide rules (structure/README sync, where generated output goes, the agent-role workflow, no invented facts/citations) — read it before working in this repo.

---

## Installation into AI Assistants

### Codex
```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/Juanda-2880/pdg-writtting/tree/main/skills/thesis-writing
```

### Manual Install
Copy the skill folders into your agent's local skills directory:
```bash
# Codex
cp -R skills/thesis-writing skills/objectives-writting skills/parragraph-structure skills/reference-writting skills/writting-tools skills/meeting-insights project-context ~/.codex/skills/

# Claude / Antigravity
cp -R skills/thesis-writing skills/objectives-writting skills/parragraph-structure skills/reference-writting skills/writting-tools skills/meeting-insights project-context ~/.claude/skills/
```

---

## Acknowledgments & Upstream Repository

This project is a fork of and contains foundational material from:
- **Original Repository:** [santifs/thesis-writing-skill](https://github.com/santifs/thesis-writing-skill)
- **Original Author:** [santifs](https://github.com/santifs)

---

## License

MIT.
