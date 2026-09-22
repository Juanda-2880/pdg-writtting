# Project Context: IAsLab ORCHID (PDG)

This directory contains the foundational specifications, institutional documentation, system requirements, and technical stack details for the **Degree Project (PDG / Proyecto de Grado)** at Universidad Icesi:
> *"IAsLab ORCHID: Plataforma de Orquestación y Gobernanza de Cargas de IA/ML en la Infraestructura de la Universidad Icesi"*

(Title propagado de ADR-001, 2026-09-12. Former working title: *"Extension of the IAsLab web system: distributed deployment of artificial intelligence models, governance, and infrastructure monitoring."* The project builds the platform; it does not extend a prior system.)

---

## Authors:

This project and thesis is developed by the following students of the **Universidad Icesi**. The degree each author is graduating in matters for the thesis cover page — Juan Jose De La Pava graduates in **two** programmes:

| Author | Degree(s) awarded |
| :--- | :--- |
| Juan Jose De La Pava | Ingeniería Telemática **and** Ingeniería de Sistemas |
| Juan David Pacheco Vargas | Ingeniería Telemática |
| Juan Camilo Melo | Ingeniería Telemática |

> [!NOTE]
> The programme is **Telemática**, not Sistemas, for all three authors (with De La Pava holding both). Earlier drafts of the cover page said "Ingeniero(a) de Sistemas"; that was wrong and has been corrected in `thesis/main.tex`.

## Working Model & Budget

- **Team organisation (confirmed 2026-09-06):** responsibility is **shared, not divided by module**. All three authors take part in implementing the subsystems, running the tests, and writing the document — there is no per-person module ownership. Do not invent a role split.
- **Tutor cadence:** one meeting per week with the tutor, used to review the current iteration's progress and adjust the next one's scope.
- **Course requirement for PDG I (stated by the authors 2026-09-13; sprint content from `meetings/2026-08-26-tutor-arquitectura.md` [52:07]):** Proyecto de Grado I requires, **at minimum, the anteproyecto and two sprints**. Sprint 1 covers the proposed architecture, data modelling and mockups; sprint 2 delivers the first features of the system.
- **Academic calendar (stated by the authors 2026-09-13):** the project spans two courses. **Proyecto de Grado I** runs from the project start on 10 August 2026 (ADR-008) until **the first days of December 2026**. **Proyecto de Grado II**, in the following semester, runs **from February to May 2027**. The period between the two courses is not part of either.
- **Budget (confirmed 2026-09-06):** the project has **no budget**. It deploys and runs the cluster on hardware already installed in the lab — no new hardware is purchased — and the whole software stack is open source. No money is involved.

## File Overview

| File | Description |
| :--- | :--- |
| [`documentation.md`](./documentation.md) | Official institutional project charter: Problem statement, general and specific objectives, macro-project context, scope boundaries, deliverables, and benefits. |
| [`requirements.md`](./requirements.md) | Detailed functional and non-functional requirements: model deployment and orchestration, reservation-based quotas with role priority, overbooking buffers, SAAMFI RBAC, hardware and workload telemetry, and automated benchmarking. Section 2 groups the requirements under the objective they serve (these may be written into `thesis/`); section 3 holds the `Sin compromiso` requirements, which are built but never written into the document. |
| [`technologies.md`](./technologies.md) | Architectural layers and technology stack: Kubernetes, KubeRay, NVIDIA GPU Operator, the AI Gateway (LiteLLM **not** adopted, see ADR-024), vLLM, Ollama, llama.cpp, Prometheus, Grafana, Loki, and DCGM exporter. |
| [`formato-anteproyecto.md`](./formato-anteproyecto.md) | The faculty's official *anteproyecto* format: required sections, what each must contain, and maximum lengths. The thesis document's chapter layout derives from this file. |
> `alcance-moscow.md` (the MoSCoW scope ladder) was **deleted on 2026-09-20**; its capabilities were folded into `requirements.md`, which is now the only requirements document.
| [`ADR.md`](./ADR.md) | **Open-questions register.** Every gap an agent cannot fill without a human decision (missing thresholds, dates, team roles, unverifiable figures) is recorded here with the exact file and marker where it is used, so applying the answer costs a `grep`, not a re-read of the thesis. Entries are **deleted** once resolved — see the usage rules at the top of the file. |
| [`meetings/`](./meetings/README.md) | **Proposed, not established, evidence.** One record per meeting, produced by the `skills/meeting-insights/` skill. A claim here becomes project fact only once a human writes it into `documentation.md`/`requirements.md`/`technologies.md` — see rule 9 of `../CLAUDE.md`. |
