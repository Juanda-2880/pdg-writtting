# Barberi Faculty of Engineering, Design and Applied Sciences

## Extension of the IAsLab web system: distributed deployment of artificial intelligence models, governance, and infrastructure monitoring.

**Responsible Tutor:** Kevin David Rodríguez Belalcazar

**Accompanying Professors:** Alejandro Muñoz Bravo

**Macro-project Title:** Computational ecosystem of software services for the development of IAsLab projects for Industry 4.0 and e-Health in the context of Digital Transformation.

**Macro-project Director:** Juan Carlos Muñoz Fernández

---

> [!NOTE]
> **This project is not a continuation of a single prior project with an inherited backlog.** The macro-project above was split into separate degree projects — an earlier one and this one — related through the shared macro-project umbrella, not through a shared codebase or a handed-over backlog. Earlier drafts of this document implied backlog stabilization as an inherited obligation from "the training phase"; that framing was wrong and has been corrected below (confirmed by the authors, 2026-09-12).

## Introduction

The Artificial Intelligence and Software Architecture Laboratory (IAsLab) of Universidad Icesi manages computational infrastructures used in academic and research projects in critical areas such as data science and artificial intelligence.

Historically, the use of these resources faced barriers related to manual configuration and hardware underutilization, which limited the scalability and reproducibility of experiments.

To address this need, a web system was developed in a first phase, designed as a control plane that centralized the configuration, execution, and tracking of distributed training tasks. This development solved the initial problem by enabling automated and secure provisioning of processing nodes, integrating institutional security mechanisms such as SAAMFI for identity management.

However, the machine learning lifecycle (MLOps) extends beyond the training and experimentation stage. As the laboratory's projects advance, it becomes necessary to enable model deployment for consumption, ensure equitable hardware management as concurrency increases, and provide the system with technical observability. **This project builds the platform that provides those capabilities** (framing corrected by the authors 2026-09-12, after the tutor's observation on 2026-09-09: *"puede que ustedes no hagan eso, sino que ustedes van a directamente levantar la base del sistema web de orquestación"*). Earlier drafts described the work as maturing or extending the web system built in the first phase; that was wrong. The prior system is a separate degree project under the same macro-project, and no component of it is inherited, extended or refactored here. The only preexisting institutional component this project integrates with is SAAMFI, purely as an identity provider.

### Institutional antecedents: hardware access and manual deployment (from tutor and lab communications, 2026-08-26 and 2026-09-04)

> Recorded from `project-context/meetings/2026-08-26-tutor-arquitectura.md` (tutor, ADR-014 answers) and `project-context/meetings/2026-09-04-alejandro-elicitacion.md` (IAsLab staff member Alejandro Muñoz Bravo). Authorized by the authors (2026-09-12) for use as project fact per `CLAUDE.md` rule 9.

Before this first phase, the IAsLab had no formal policy for granting access to its computing equipment. The access mechanism was binary: a user either received ZeroTier VPN keys plus root credentials, or received nothing at all ("que es la decisión que hemos tomado hasta ahora", tutor, 2026-08-26). Credentials were granted individually, to a maximum of four or five people at a time, and only to those already inside the laboratory's circle (former students of a prior elective, IAsLab members, or professors). Students outside that circle used external services such as Google Colab, or used no specialized computing at all, which produced sustained underutilization of the installed hardware ("realmente no usan la infraestructura de acá", tutor, 2026-08-26). Behind the restriction sat an economic-equity rationale: not every student can sustain the cost of a commercial cloud-computing subscription. As of the 2026-09-04 meeting, the laboratory's own use of its infrastructure remains at the experimentation stage, not continuous production use ("estamos simplemente...haciendo experimentos, no...uso continuo o explotación directa", Alejandro Muñoz Bravo, 2026-09-04). No wait-time figures or formal access-request records are on file; this account is limited to what the tutor and lab staff reported directly.

Separately, before this project the laboratory deployed models manually: installing candidate inference engines and packages via Python scripts run by hand, without any platform automating the process ("fue básicamente como la ejecución de un par de scripts y ya. No hicieron una plataforma ellos directamente", tutor, 2026-08-26). Building on that practice, the laboratory evaluated inference engines with its own benchmarking harness, a Python script driven by declarative YAML specifications that measures input/output tokens per second and end-to-end response time (Alejandro Muñoz Bravo, 2026-09-04). Based on those benchmarks, the laboratory concluded that a purpose-compiled build of llama.cpp, compiled specifically for the hardware in room 104M, lets them deploy the best-performing models among those tried, after vLLM failed to produce good results in the lab's own trials. The measured baseline is approximately 20 tokens per second, with 10 to 15 minute response times, across the room's 31 workstations.

## Problem Description

Although the first phase of the project mitigated the operational bottleneck associated with model training and basic task orchestration, the current system presents limitations regarding the productive stages of the artificial intelligence lifecycle and the progressive scaling of its users.

Currently, researchers using the platform do not have a mechanism within the web system to configure and manage the distributed deployment and inference of previously trained models (especially large-scale architectures such as LLMs). This gap fragments the workflow and limits putting research into production. On the other hand, the growing adoption of the system creates a latent risk of monopolization of graphics processing units (GPUs), since the platform does not incorporate a governance system with quotas or formal role-based restrictions. Finally, its monitoring module lacks fine-grained telemetry, preventing administrators from observing exact infrastructure consumption metrics in real time.

## Formulation of Objectives

> [!IMPORTANT]
> **Rewritten 2026-09-12.** These objectives were reformulated after the tutor's review, and the authoritative Spanish wording now lives in `thesis/chapters/04-objetivos.tex`. The rules they must satisfy are in `skills/objectives-writting/objectives-project-rules.md` (one infinitive verb, no ambiguous adjectives, no parenthetical enumerations, no dates, an explicit measurable criterion). The English below is a translation kept for context, not the source of truth: **edit the chapter, then mirror it here.**

**General objective.** Build the IAsLab platform for orchestrating and governing artificial intelligence and machine learning workloads, by means of inference-deployment, role-based resource governance and infrastructure observability modules, in order to consolidate the on-premise MLOps lifecycle at Universidad Icesi.

1. **Observability.** Develop an observability module in the IAsLab web system for capturing and visualizing hardware and workload metrics of the compute nodes, aimed at supervising node state regardless of whether a node is running inference or training (FR-03.5). Wording adopted from the tutor's own proposed rewrite (ADR-028).
2. **Governance.** Implement a quota and infrastructure-restriction system, coupled to the roles SAAMFI provides plus a platform administrator role, reserving compute slots for inference and training workloads with professors holding priority over how the room's capacity is allocated, in order to prevent GPU monopolization. It **implements**, it does not merely design (ADR-015); the role taxonomy is SAAMFI's plus one administrator (ADR-022); the model is reservation with role priority, never Fair-Share.
3. **Orchestration.** Incorporate into the platform an inference orchestration engine that is agnostic to the underlying serving engine and packaged as a container image, able to deploy already-trained models concurrently. No prior IAsLab interface exists to integrate into (ADR-027), and no specific engine is committed to in advance.
4. **Evaluation.** Evaluate the platform's performance and acceptance through load testing with **twenty simultaneous users** and usability validations with laboratory users, in order to determine whether it reaches a satisfactory level of operational acceptance (ADR-004).

## Scope

- **High-level requirements:** The project will deliver the platform's frontend and backend, comprising: a telemetry panel with granular per-node metrics, an administrative quota module linked to the roles SAAMFI provides, and a deployment interface connected to a technology-agnostic inference orchestrator. (Corrected 2026-09-12: earlier wording said "the extension of the current frontend and backend", which presupposed a preexisting system with this scope. There is none.)
- **Exclusions:** No neural network architectures, proprietary AI models, or underlying mathematical algorithms will be developed. Migration to commercial public cloud providers (such as AWS, GCP, or Azure) is also not contemplated. **This project does not build model-training features** (that remains the sibling degree project's scope, under the same macro-project) — but this is a feature-development exclusion, not an infrastructure one: see the training-workload compatibility requirement below, which this project *does* own.
- **Scope clarification (confirmed by the authors, 2026-09-12):** the reservation-based quota/governance system and the observability module must **not assume every GPU-node workload is inference**. Training jobs run on the same physical hardware (the sibling project's control plane schedules them on the same 31 workstations in room 104M), and today they run **ungoverned** — this is itself part of the monopolization risk described in Problem Description above. A quota system that only accounts for inference sessions and stays blind to training jobs would leave that risk half-solved. See `requirements.md` FR-02.6 and FR-03.5.
- **Constraints:** The software will run strictly on-premise, operating within the bandwidth and physical capacity limits of the units installed in the laboratory.
- **Assumptions:** Uninterrupted availability of IAsLab clusters for testing is guaranteed, and the SAAMFI authentication service will remain persistent.

## Expected Results

As a result of this extension, a new version of the web system is expected to be delivered, capable of supporting end-to-end MLOps operations within Universidad Icesi. The platform will allow users not only to schedule training runs but also to interactively deploy generative models or other advanced architectures. At the same time, laboratory administrators will be provided with strict and observable control over hardware through automated quota schemes, ensuring that equipment is not overloaded and that an equitable service is provided to seed researchers ("semilleros"), researchers, and undergraduate thesis students.

## Deliverables

- **Functional and packaged software:** Source code for the web system extension, deployed on IAsLab infrastructure and structured under standards that allow its registration as a copyrighted technology-based product.
- **Technical and user documentation:** Updated manuals detailing the new model deployment processes, telemetry visualization, and quota policy administration.

## Benefits

The development of this extension will maximize the return on investment in institutional hardware. By implementing the quota and governance system, equitable access to critical resources is democratized, preventing hoarding and reducing the need to purchase costly public cloud credits. Academically, enabling the deployment of complex models (such as LLMs) will foster advanced projects in the areas of Industry 4.0 and eHealth, ensuring that processing remains on local servers, which safeguards information privacy. Additionally, the improved interface and in-depth monitoring will drastically reduce cognitive and administrative burden.
