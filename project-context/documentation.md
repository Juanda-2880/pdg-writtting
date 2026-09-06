# Barberi Faculty of Engineering, Design and Applied Sciences

## Extension of the IAsLab web system: distributed deployment of artificial intelligence models, governance, and infrastructure monitoring.

**Responsible Tutor:** Kevin David Rodríguez Belalcazar

**Accompanying Professors:** Alejandro Muñoz Bravo

**Macro-project Title:** Computational ecosystem of software services for the development of IAsLab projects for Industry 4.0 and e-Health in the context of Digital Transformation.

**Macro-project Director:** Juan Carlos Muñoz Fernández

---

## Introduction

The Artificial Intelligence and Software Architecture Laboratory (IAsLab) of Universidad Icesi manages computational infrastructures used in academic and research projects in critical areas such as data science and artificial intelligence.

Historically, the use of these resources faced barriers related to manual configuration and hardware underutilization, which limited the scalability and reproducibility of experiments.

To address this need, a web system was developed in a first phase, designed as a control plane that centralized the configuration, execution, and tracking of distributed training tasks. This development solved the initial problem by enabling automated and secure provisioning of processing nodes, integrating institutional security mechanisms such as SAAMFI for identity management.

However, the machine learning lifecycle (MLOps) extends beyond the training and experimentation stage. As the laboratory's projects advance, it becomes necessary to enable model deployment for consumption, ensure equitable hardware management as concurrency increases, and provide the system with technical observability. This new phase seeks to mature the web system built so far in order to consolidate a comprehensive computational ecosystem.

## Problem Description

Although the first phase of the project mitigated the operational bottleneck associated with model training and basic task orchestration, the current system presents limitations regarding the productive stages of the artificial intelligence lifecycle and the progressive scaling of its users.

Currently, researchers using the platform do not have a mechanism within the web system to configure and manage the distributed deployment and inference of previously trained models (especially large-scale architectures such as LLMs). This gap fragments the workflow and limits putting research into production. On the other hand, the growing adoption of the system creates a latent risk of monopolization of graphics processing units (GPUs), since the platform does not incorporate a governance system with quotas or formal role-based restrictions. Finally, the software requires stabilization through the resolution of user stories from the backlog, and its monitoring module lacks fine-grained telemetry, preventing administrators from observing exact infrastructure consumption metrics in real time.

## Formulation of Objectives

Extend the IAsLab's web orchestration system with distributed artificial intelligence model deployment capabilities, resource governance policies, and advanced monitoring tools, toward consolidating the MLOps lifecycle over the institution's computational infrastructure.

1. Enhance the observability of the current platform by scaling the primitive telemetry module toward the generation of advanced and interactive graphical visualizations for detailed analysis of hardware and model metrics.
2. Design a logical system for quota management and infrastructure restriction coupled to the role attributes provided by SAAMFI, under the principle of Fair-Share allocation.
3. Integrate an inference orchestration engine, independent of the underlying technology, with the capability to configure and concurrently deploy artificial intelligence models from the user interface.
4. Evaluate the performance of the web extension in the IAsLab's production environment through load testing and usability validations with end users, ensuring satisfactory levels of operational acceptance.

## Scope

- **High-level requirements:** The project will deliver the extension of the current frontend and backend, which will include: an expanded telemetry panel with granular metrics, an administrative quota module linked to SAAMFI user profiles, stabilization of backlog-based components, and a new deployment interface connected to a technology-agnostic inference orchestrator.
- **Exclusions:** No neural network architectures, proprietary AI models, or underlying mathematical algorithms will be developed. Migration to commercial public cloud providers (such as AWS, GCP, or Azure) is also not contemplated.
- **Constraints:** The software will run strictly on-premise, operating within the bandwidth and physical capacity limits of the units installed in the laboratory.
- **Assumptions:** A stabilized codebase inherited from the training phase is available, uninterrupted availability of IAsLab clusters for testing is guaranteed, and the SAAMFI authentication service will remain persistent.

## Expected Results

As a result of this extension, a new version of the web system is expected to be delivered, capable of supporting end-to-end MLOps operations within Universidad Icesi. The platform will allow users not only to schedule training runs but also to interactively deploy generative models or other advanced architectures. At the same time, laboratory administrators will be provided with strict and observable control over hardware through automated quota schemes, ensuring that equipment is not overloaded and that an equitable service is provided to seed researchers ("semilleros"), researchers, and undergraduate thesis students.

## Deliverables

- **Functional and packaged software:** Source code for the web system extension, deployed on IAsLab infrastructure and structured under standards that allow its registration as a copyrighted technology-based product.
- **Technical and user documentation:** Updated manuals detailing the new model deployment processes, telemetry visualization, and quota policy administration.

## Benefits

The development of this extension will maximize the return on investment in institutional hardware. By implementing the quota and governance system, equitable access to critical resources is democratized, preventing hoarding and reducing the need to purchase costly public cloud credits. Academically, enabling the deployment of complex models (such as LLMs) will foster advanced projects in the areas of Industry 4.0 and eHealth, ensuring that processing remains on local servers, which safeguards information privacy. Additionally, the improved interface and in-depth monitoring will drastically reduce cognitive and administrative burden.
