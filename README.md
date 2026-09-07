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

The repository is organized into six writing-reference modules, plus a multi-agent harness (agent roles, a LaTeX configuration module, and a scratch build directory) that governs how AI agents use them, plus the actual thesis document itself:

```text
pdg-writtting/
├── CLAUDE.md                # Harness-wide rules every agent must follow
├── agent-roles/              # Multi-agent workflow: Coordinador, Investigador, Redactor, Revisor
├── compiled-output/          # Scratch directory for generated/compiled artifacts (gitignored)
├── latex/                    # LaTeX config, build rules & skill (preamble, Makefile, citation setup)
├── thesis/                   # The actual thesis document — one file per chapter, see thesis/README.md
├── project-context/          # Institutional PDG charter, requirements & tech stack
├── thesis-writing/           # Global thesis orchestration & end-to-end workflow (from upstream)
├── objectives-writting/      # Formulation & audit of research objectives
├── parragraph-structure/     # Academic paragraph architecture & typologies
├── reference-writting/       # Attribution, direct quotes & paraphrasing (APA 7th)
└── writting-tools/           # APA formatting, paragraph mechanics & punctuation
```

---

## Module Summaries

### 1. [`project-context/`](./project-context/README.md)
The empirical ground truth and architectural specifications for the IAsLab Degree Project (PDG):
- **Project Charter:** Universidad Icesi official scope, background, objectives, and deliverables.
- **System Requirements:** Functional requirements (model provisioning, Fair-Share quotas, 20% overbooking, SAAMFI RBAC, hardware telemetry, benchmark harness) and non-functional constraints.
- **Technology Stack:** Multi-tiered architecture encompassing Kubernetes, KubeRay, NVIDIA GPU Operator, LiteLLM Proxy, vLLM, Ollama, LGP monitoring stack (Loki/Prometheus/Grafana), and DCGM telemetry.
- **Anteproyecto Format:** The faculty's official section-by-section format the thesis document follows.
- **`ADR.md` — Open-questions register:** The single list of unresolved doubts blocking the document, each recorded with the exact file and marker where it is used so another agent can apply the answer with a `grep` instead of re-reading the thesis. Entries are deleted, not archived, once resolved.

### 2. [`thesis-writing/`](./thesis-writing/README.md)
The central workflow module governing the full lifecycle of an empirical research thesis:
- **Scoping & Definition:** Transforming a broad topic into a research question, identifying research gaps, and verifying feasibility.
- **Outlining:** Detailed chapter and subsection architectures for undergraduate (TFG), master's (TFM), and doctoral dissertations.
- **Drafting:** Academic writing moves (Claim $\rightarrow$ Evidence $\rightarrow$ Interpretation), keeping Results factual and Discussion interpretive.
- **Macro & Micro Review:** Auditing flow, structural transitions, tone, and empirical consistency.

### 3. [`objectives-writting/`](./objectives-writting/README.md)
Specialized guidelines for formulating and evaluating research objectives:
- **Hierarchy:** Clear boundary between 1 General Objective (terminal contribution) and 3–5 Specific Objectives (tactical milestones).
- **Standards:** Strict enforcement of SMART criteria, syntactic formula ($Verb + Variable + Context + Purpose$), and Bloom's Taxonomy cognitive alignment.
- **Anti-patterns:** Identifying and fixing common errors, including confusing operational activities with objectives, compound verbs, and unmeasurable statements.

### 4. [`parragraph-structure/`](./parragraph-structure/README.md)
Frameworks for building self-contained, cohesive micro-arguments:
- **Tri-Part Model:** *Fase Organizadora* (Topic sentence/claim), *Contenido* (Empirical evidence and analysis), and *Fase de Cierre* (Local conclusion/transition).
- **Typologies:** 7 development patterns (Concept Definition, Problem-Solution, Cause-Effect, Comparison-Contrast, Sequence, Enumeration, Framing).
- **Opening Strategies:** 6 introductory paragraph styles (Synthesis, Assertive Claims, Epigraph/Quote, Guiding Questions, Analogy, Critical Incident).

### 5. [`reference-writting/`](./reference-writting/README.md)
Ethical and technical standards for attributing external scholarship under APA 7th:
- **Direct Quotations:** Explicit guidelines for short in-text quotes (<40 words) and indented block quotations ($\ge 40$ words) with mandatory locators (`p.`, `pp.`, `para.`).
- **Indirect Citations & Paraphrasing:** Synthesis of single and multi-source literature, narrative vs. parenthetical citations, and reporting verb taxonomies.
- **Error Avoidance:** Preventing patchwriting, quote over-reliance, and attribution boundaries blurring.

### 6. [`agent-roles/`](./agent-roles/README.md)
The multi-agent workflow that turns the modules above into a repeatable writing process:
- **Coordinador:** Plans tasks, assigns work, tracks thesis status; the only role that makes structural decisions.
- **Investigador:** Sources and verifies evidence from `project-context/` and outside literature; flags gaps instead of guessing.
- **Redactor:** Drafts prose/LaTeX from approved outlines and verified evidence, applying the modules above.
- **Revisor:** Runs the micro/macro review checklist, checks citations and structure, validates the build.

### 7. [`compiled-output/`](./compiled-output/README.md)
A gitignored scratch directory where agents write generated or compiled artifacts (LaTeX build files, draft exports, test compilations) so the source modules stay clean.

### 8. [`latex/`](./latex/README.md)
LaTeX configuration, build tooling, and a dedicated skill so agents don't reinvent the toolchain each session:
- **Preamble & build**: a ready-to-copy `preamble.tex`, `Makefile`, and `latexmkrc` (report class, Spanish/babel, `latexmk`, output routed to `compiled-output/`).
- **APA 7 citations in LaTeX**: `natbib` + `apalike`, chosen to match `reference-writting/` and `writting-tools/normas-APA.md`.
- **Semantic-markup rules**: correct `description`/`itemize`/`enumerate` use, `cleveref` cross-references, `csquotes` quotations, `booktabs`/`longtable` tables.

### 9. [`thesis/`](./thesis/README.md)
The actual thesis document — real, submittable content, not guidance:
- **One file per chapter/section** under `chapters/`, so an agent can read/edit a single section instead of loading 60+ pages of prose into context.
- **Anteproyecto structure**: the document currently follows the faculty's *anteproyecto* format (`project-context/formato-anteproyecto.md`) — Motivación y antecedentes, Descripción del problema, Hipótesis y restricciones, Objetivos, Marco teórico, Estado del arte, Metodología, Contribución y resultados, Anexos — **not** the final-thesis structure in `thesis-writing/structure.md`.
- **`STATUS.md`**: the single source of truth for what's drafted/under review/approved, plus the standing structural decisions, kept current by the Coordinador role.
- **`main.tex`**: a thin skeleton (`\input{../latex/preamble}` + front matter + `\include{chapters/...}`) — never the place to "see the whole thesis."

### 10. [`writting-tools/`](./writting-tools/README.md)
Technical reference manuals and orthographic conventions:
- **APA 7th Standard:** Margins, font recommendations, 5-level heading hierarchy, empirical table/figure structures, and reference lists.
- **Paragraph Integration:** Informational flow, the Given-New principle, and avoiding loose demonstratives.
- **Punctuation Precision:** Mandatory rules for *Punto y Seguido*, *Punto y Aparte*, citation punctuation, comma splices, semicolons, and dashes.

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

# Multi-agent thesis writing (Claude Code)
"Act as the Coordinador (see agent-roles/) and plan the next task for drafting Chapter 3."
```

For Claude Code specifically, [`CLAUDE.md`](./CLAUDE.md) is loaded automatically and defines the harness-wide rules (structure/README sync, where generated output goes, the agent-role workflow, no invented facts/citations) — read it before working in this repo.

---

## Installation into AI Assistants

### Codex
```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/Juanda-2880/pdg-writtting/tree/main/thesis-writing
```

### Manual Install
Copy the skill folders into your agent's local skills directory:
```bash
# Codex
cp -R thesis-writing objectives-writting parragraph-structure reference-writting writting-tools project-context ~/.codex/skills/

# Claude / Antigravity
cp -R thesis-writing objectives-writting parragraph-structure reference-writting writting-tools project-context ~/.claude/skills/
```

---

## Acknowledgments & Upstream Repository

This project is a fork of and contains foundational material from:
- **Original Repository:** [santifs/thesis-writing-skill](https://github.com/santifs/thesis-writing-skill)
- **Original Author:** [santifs](https://github.com/santifs)

---

## License

MIT.
