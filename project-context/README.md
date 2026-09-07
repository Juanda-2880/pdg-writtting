# Project Context: IAsLab Web Extension (PDG)

This directory contains the foundational specifications, institutional documentation, system requirements, and technical stack details for the **Degree Project (PDG / Proyecto de Grado)** at Universidad Icesi:
> *"Extension of the IAsLab web system: distributed deployment of artificial intelligence models, governance, and infrastructure monitoring."*

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
- **Budget (confirmed 2026-09-06):** the project has **no budget**. It deploys and runs the cluster on hardware already installed in the lab — no new hardware is purchased — and the whole software stack is open source. No money is involved.

## File Overview

| File | Description |
| :--- | :--- |
| [`documentation.md`](./documentation.md) | Official institutional project charter: Problem statement, general and specific objectives, macro-project context, scope boundaries, deliverables, and benefits. |
| [`requirements.md`](./requirements.md) | Detailed functional and non-functional requirements: Model deployment, Fair-Share quota reservations, overbooking buffers, SAAMFI RBAC, telemetry, and automated benchmarking. |
| [`technologies.md`](./technologies.md) | Architectural layers and technology stack: Kubernetes, KubeRay, NVIDIA GPU Operator, LiteLLM Proxy, vLLM, Ollama, Prometheus, Grafana, Loki, and DCGM exporter. |
| [`formato-anteproyecto.md`](./formato-anteproyecto.md) | The faculty's official *anteproyecto* format: required sections, what each must contain, and maximum lengths. The thesis document's chapter layout derives from this file. |
| [`ADR.md`](./ADR.md) | **Open-questions register.** Every gap an agent cannot fill without a human decision (missing thresholds, dates, team roles, unverifiable figures) is recorded here with the exact file and marker where it is used, so applying the answer costs a `grep`, not a re-read of the thesis. Entries are **deleted** once resolved — see the usage rules at the top of the file. |
