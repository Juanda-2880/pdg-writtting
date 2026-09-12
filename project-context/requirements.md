# PDG Project Requirements & Specifications: IAsLab Web Extension

This document specifies the functional requirements, non-functional constraints, governance rules, and infrastructure parameters for the **Project of Degree (PDG)**: *"Extension of the IAsLab web system: distributed deployment of artificial intelligence models, governance, and infrastructure monitoring"*, Universidad Icesi.

---

## 1. Context & Operational Vision

The IAsLab computational ecosystem requires an end-to-end MLOps platform running strictly **on-premise** on university infrastructure. The system acts as a centralized control plane enabling students, researchers, and elective courses to deploy, run inference on, and monitor open-weight artificial intelligence models (such as LLMs and vision models) across distributed GPU/CPU worker nodes without requiring individual paid cloud AI subscriptions.

---

## 2. Functional Requirements (FR)

### FR-01: User Model Deployment & Remote Inference
- **FR-01.1 (Model Provisioning):** Users must be able to deploy pre-trained open-weight models (e.g., LLaMA, Mistral, Qwen, DeepSeek) by supplying a model repository identifier (Hugging Face / ModelScope / Git) or uploading configuration artifacts.
- **FR-01.2 (Node & Hardware Targeting):** The user interface must provide a graphical node-selector allowing users to specify target hardware (e.g., dedicated GPU node with RTX 4090 vs. CPU worker node).
- **FR-01.3 (Quantization Support):** The deployment engine must support model quantization schemes (AWQ, GPTQ, GGUF, bitsandbytes 4-bit/8-bit) to maximize concurrent sessions on available VRAM.
- **FR-01.4 (Inference Engine Abstraction):** The backend must interface with a technology-agnostic inference orchestration engine (e.g., vLLM, Ollama, Llama.cpp, TGI) exposed through a unified API gateway (LiteLLM Proxy).
- **FR-01.5 (Remote Consumption & IDE Access):** Students must be able to query deployed models via OpenAI-compatible endpoints or secure remote sessions (API key tokens) from any location/IDE.

### FR-02: Resource Reservation & Quota Governance
- **Governance model (corrected by the authors, 2026-09-12): this is a reservation system with role-based priority, not a Fair-Share allocation scheme.** Earlier drafts of this document and of the thesis describe quota governance "under the principle of Fair-Share allocation" — that framing is wrong and is being phased out (see the pending redaction note in `thesis/STATUS.md`). The actual mechanism is: students and professors reserve compute slots, and **professors have priority to claim resources and to control how the room's capacity is allocated overall** — not an algorithm that distributes resources proportionally/fairly among equal peers (which is what "Fair-Share"/DRF-style scheduling means in the scheduling literature). Don't reintroduce "Fair-Share" language in new writing without the authors' sign-off.
- **FR-02.1 (Time-Slot & Resource Reservations):** Students and faculty must be able to reserve computing slots in advance with automated start and termination windows.
- **FR-02.2 (Class & Academic Priority):** Academic courses (e.g., the 24-student AI elective) must have configurable reservation priority over individual thesis or exploratory tasks.
- **FR-02.7 (Professor Priority & Room-Level Control, confirmed by the authors 2026-09-12):** Professors (Research Professors / Lab Administrators role, FR-02.4) have reservation priority over students — including the ability to claim resources ahead of, or instead of, an existing student reservation — and can manage how the room's overall capacity is allocated, not only their own slot. This is a separate priority tier from FR-02.2's course-vs-individual priority: FR-02.2 ranks *reservation types*, FR-02.7 gives a *role* override authority over the room.
- **FR-02.3 (Overbooking / Over-quota Buffer):** The reservation engine must support a controlled over-allocation buffer (10% to 20%) under statistical assumption that not all concurrent students exhaust peak burst inference simultaneously.
  - **Origin of the 10–20% range (confirmed 2026-09-06):** this is an **IAsLab design decision**, not a figure taken from literature. Its stated rationale is the lab administrators' experience managing concurrent workloads and optimising GPU resources, informed by usage patterns observed in previous course offerings. Write it up as a design decision attributed to the laboratory — **never** cite it to an external source. No historical-usage dataset is on file in this repository, so the thesis must not present numbers, charts, or statistics derived from those observations unless the lab supplies the underlying data.
- **FR-02.4 (Fine-Grained Dynamic RBAC):** Dynamic role-based access control coupled with Universidad Icesi's **SAAMFI** identity provider, distinguishing between:
  - *Undergraduate Thesis Students (PDG / TFG)*
  - *Elective Course Students (Electiva IA)*
  - *Cross-faculty non-CS Students (Special request reservations)*
  - *Seed Researchers (Semilleros de Investigación)*
  - *Research Professors & Lab Administrators*
- **FR-02.5 (Automated Session Cutoff & Notifications):** When a reserved session reaches its expiration threshold, the system must warn the user, save inference logs/session state, and gracefully deallocate or freeze the compute container.
- **FR-02.6 (Training Workload Compatibility, confirmed by the authors 2026-09-12):** The quota/reservation system must recognize and account for GPU/CPU resource consumption from **training jobs**, not only inference sessions — a node running a training job submitted through the sibling project's control plane must be visible to and governed by the same reservation-priority and overbooking rules as an inference session, not treated as an invisible, unmanaged workload. This project does not implement training itself (see `documentation.md`'s Scope/Exclusions); it must, however, keep training workloads from silently defeating the governance this FR builds. **Open integration detail:** see ADR-020 in `project-context/ADR.md` for how the quota system is meant to detect/tag a training job as such.

### FR-03: Infrastructure Observability & Telemetry
- **FR-03.1 (Hardware Telemetry Collection):** Real-time monitoring of GPU metrics (RTX 4090 temperature, VRAM utilization, power draw in Watts, PCIe throughput) and node metrics (CPU usage, system RAM, disk I/O).
- **FR-03.2 (Model & Inference Telemetry):** Tracking input/output tokens per second, request latency (Time to First Token - TTFT, Inter-Token Latency - ITL), queue wait times, and concurrency saturation.
- **FR-03.3 (Centralized Logging Stack - LGP):** Centralized log aggregation and tracing (e.g., Loki / Fluentd, Prometheus, Grafana) to diagnose node crashes, GPU freezing, and out-of-memory (OOM) events.
- **FR-03.4 (Automated Health & Recovery Diagnostics):** Automated detection when a worker node or GPU becomes unresponsive (e.g., when VRAM hits 90%+ saturation or hardware freezes), triggering diagnostic alerts and self-healing container restarts.
- **FR-03.5 (Workload-Agnostic Telemetry, confirmed by the authors 2026-09-12):** Node-level hardware telemetry (FR-03.1) must not assume the active workload is always inference. GPU/VRAM/power/PCIe metrics must be captured regardless of whether the node is running an inference session or a training job from the sibling project's control plane, so administrators keep visibility into training-induced saturation instead of a blind spot.

### FR-04: Automated Benchmarking & Evaluation Suite
- **FR-04.1 (Evaluation Pipeline):** Python-driven automated benchmarking engine executing test suites defined in declarative YAML files.
- **FR-04.2 (Code & Reasoning Tasks):** Generating code and reasoning responses from deployed models against structured user stories, measuring output quality, accuracy, token generation speed, and runtime latency.
- **FR-04.3 (Inference Engine Comparison):** Providing formal comparative data to benchmark different inference engines under identical workloads.

---

## 3. Non-Functional Requirements (NFR)

| ID | Category | Requirement Specification |
| :--- | :--- | :--- |
| **NFR-01** | **Deployment Environment** | Strictly **on-premise** deployment within IAsLab physical servers and workstation clusters. No reliance on commercial public clouds (AWS, GCP, Azure). |
| **NFR-02** | **Heterogeneous Architecture** | High-performance GPU machines (NVIDIA RTX 4090 nodes) dedicated to inference and/or training computation — the same physical nodes are shared with training workloads from the sibling project (FR-02.6, FR-03.5) — while legacy dedicated servers handle orchestration planes, control nodes, and database persistence. |
| **NFR-03** | **Storage Partitioning** | High-volume storage separation: dedicated fast NVMe/SSD partitions for model weights (10GB–50GB per checkpoint) isolated from system logs and root OS drives. |
| **NFR-04** | **Usability & Low Friction** | Intuitive web interface designed for students across disciplines, minimizing command-line complexity for model deployment and reservation. |
| **NFR-05** | **Security & Authentication** | Mandatory SSO integration with Universidad Icesi's **SAAMFI** service; secure API token management with expiration periods. |
| **NFR-06** | **Fault Tolerance & Node Isolation** | Failure or freeze of a single student inference container must not destabilize neighboring containers or the host Kubernetes/Ray node. |

---

## 4. Hardware Constraints & Operational Assumptions

- **Room inventory (confirmed 2026-09-04):** The IAsLab room **104M** houses **31 workstations** usable as compute nodes. Source: meeting with lab staff member Alejandro Muñoz Bravo — «En la sala hay 31 máquinas» (`project-context/meetings/2026-09-04-alejandro-elicitacion.md`, [7:34]).
- **Per-node CPU/RAM (confirmed 2026-08-26):** Each workstation carries an **Intel Core i9** processor (exact model/generation not stated) and approximately **32 GB of system RAM**. Source: meeting with the tutor — student Juan David Pacheco Vargas stated «las capacidades de los computadores son como de 32 de RAM, 24 de GPU y como son estos i9», confirmed by the tutor with «Perfecto» (`project-context/meetings/2026-08-26-tutor-arquitectura.md`, [28:34]–[28:47]).
- **Target Accelerator Hardware (confirmed 2026-09-12 by the authors):** NVIDIA GeForce RTX 4090 (24 GB GDDR6X VRAM) per compute node. Previously recorded as "RTX 4080 (16 GB)" — both the model and the VRAM figure were wrong; corrected directly by the authors. ADR-013 is now closed.
- **Cluster Control Plane:** Run on dedicated host servers that remain permanently energized without unannounced restarts.
- **Model Size Constraints:** Models must fit within 24 GB VRAM using appropriate quantization (e.g., 4-bit AWQ/GGUF for 7B–14B models, or distributed tensor-parallelism if multi-GPU clusters are engaged).
- **Network Environment:** Universidad Icesi internal campus intranet with reverse-proxy routing for authorized remote access.
