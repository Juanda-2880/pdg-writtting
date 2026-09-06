# Academic & Thesis Writing Skills Suite (PDG Writing)

An integrated, modular AI-agent skills suite and reference system for planning, structuring, drafting, citing, and reviewing academic research, empirical theses, dissertations, undergraduate capstone projects (PDG / TFG), and master's theses (TFM).

The suite is intentionally format-neutral: it supports Markdown, LaTeX, Word-oriented prose, and Google Docs workflows, prioritizing academic rigor, logical coherence, and empirical precision.

---

## Suite Architecture & Modules

The repository is organized into five specialized, interconnected modules:

```text
pdg-writtting/
├── thesis-writing/          # Global thesis orchestration & end-to-end workflow
├── objectives-writting/      # Formulation & audit of research objectives
├── parragraph-structure/    # Academic paragraph architecture & typologies
├── reference-writting/      # Attribution, direct quotes & paraphrasing (APA 7th)
└── writting-tools/          # APA formatting, paragraph mechanics & punctuation
```

---

## Module Summaries

### 1. [`thesis-writing/`](./thesis-writing/README.md)
The central workflow module governing the full lifecycle of an empirical research thesis:
- **Scoping & Definition:** Transforming a broad topic into a research question, identifying research gaps, and verifying feasibility.
- **Outlining:** Detailed chapter and subsection architectures for undergraduate (TFG), master's (TFM), and doctoral dissertations.
- **Drafting:** Academic writing moves (Claim $\rightarrow$ Evidence $\rightarrow$ Interpretation), keeping Results factual and Discussion interpretive.
- **Macro & Micro Review:** Auditing flow, structural transitions, tone, and empirical consistency.

### 2. [`objectives-writting/`](./objectives-writting/README.md)
Specialized guidelines for formulating and evaluating research objectives:
- **Hierarchy:** Clear boundary between 1 General Objective (terminal contribution) and 3–5 Specific Objectives (tactical milestones).
- **Standards:** Strict enforcement of SMART criteria, syntactic formula ($Verb + Variable + Context + Purpose$), and Bloom's Taxonomy cognitive alignment.
- **Anti-patterns:** Identifying and fixing common errors, including confusing operational activities with objectives, compound verbs, and unmeasurable statements.

### 3. [`parragraph-structure/`](./parragraph-structure/README.md)
Frameworks for building self-contained, cohesive micro-arguments:
- **Tri-Part Model:** *Fase Organizadora* (Topic sentence/claim), *Contenido* (Empirical evidence and analysis), and *Fase de Cierre* (Local conclusion/transition).
- **Typologies:** 7 development patterns (Concept Definition, Problem-Solution, Cause-Effect, Comparison-Contrast, Sequence, Enumeration, Framing).
- **Opening Strategies:** 6 introductory paragraph styles (Synthesis, Assertive Claims, Epigraph/Quote, Guiding Questions, Analogy, Critical Incident).

### 4. [`reference-writting/`](./reference-writting/README.md)
Ethical and technical standards for attributing external scholarship under APA 7th:
- **Direct Quotations:** Explicit guidelines for short in-text quotes (<40 words) and indented block quotations ($\ge 40$ words) with mandatory locators (`p.`, `pp.`, `para.`).
- **Indirect Citations & Paraphrasing:** Synthesis of single and multi-source literature, narrative vs. parenthetical citations, and reporting verb taxonomies.
- **Error Avoidance:** Preventing patchwriting, quote over-reliance, and attribution boundaries blurring.

### 5. [`writting-tools/`](./writting-tools/README.md)
Technical reference manuals and orthographic conventions:
- **APA 7th Standard:** Margins, font recommendations, 5-level heading hierarchy, empirical table/figure structures, and reference lists.
- **Paragraph Integration:** Informational flow, the Given-New principle, and avoiding loose demonstratives.
- **Punctuation Precision:** Mandatory rules for *Punto y Seguido*, *Punto y Aparte*, citation punctuation, comma splices, semicolons, and dashes.

---

## Recommended AI Agent Usage

Instruct your AI coding or writing assistant to leverage the relevant module based on your task:

```text
# Planning & Scoping
"Use the objectives-writting skill to evaluate my proposed General and Specific Objectives."

# Structural Outlining & Drafting
"Use the thesis-writing skill to outline my Methodology chapter and review it against structure.md."

# Paragraph Development & Argumentation
"Apply the paragraph-structure skill to draft a Problem-Solution paragraph discussing our database bottleneck."

# Referencing & Attribution
"Use reference-writting and writting-tools to format these external citations and tables according to APA 7th."
```

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
cp -R thesis-writing objectives-writting parragraph-structure reference-writting writting-tools ~/.codex/skills/

# Claude / Antigravity
cp -R thesis-writing objectives-writting parragraph-structure reference-writting writting-tools ~/.claude/skills/
```

---

## License

MIT.
