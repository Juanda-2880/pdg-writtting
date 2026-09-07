# PDG Project Requirements & Specifications: IAsLab Web Extension

This document specifies the functional requirements, non-functional constraints, governance rules, and infrastructure parameters for the **Project of Degree (PDG)**: *"Extension of the IAsLab web system: distributed deployment of artificial intelligence models, governance, and infrastructure monitoring"*, Universidad Icesi.

---

## 1. Context & Operational Vision

The IAsLab computational ecosystem requires an end-to-end MLOps platform running strictly **on-premise** on university infrastructure. The system acts as a centralized control plane enabling students, researchers, and elective courses to deploy, run inference on, and monitor open-weight artificial intelligence models (such as LLMs and vision models) across distributed GPU/CPU worker nodes without requiring individual paid cloud AI subscriptions.

---

## 2. Functional Requirements (FR)

### FR-01: User Model Deployment & Remote Inference
- **FR-01.1 (Model Provisioning):** Users must be able to deploy pre-trained open-weight models (e.g., LLaMA, Mistral, Qwen, DeepSeek) by supplying a model repository identifier (Hugging Face / ModelScope / Git) or uploading configuration artifacts.
- **FR-01.2 (Node & Hardware Targeting):** The user interface must provide a graphical node-selector allowing users to specify target hardware (e.g., dedicated GPU node with RTX 4080 vs. CPU worker node).
- **FR-01.3 (Quantization Support):** The deployment engine must support model quantization schemes (AWQ, GPTQ, GGUF, bitsandbytes 4-bit/8-bit) to maximize concurrent sessions on available VRAM.
- **FR-01.4 (Inference Engine Abstraction):** The backend must interface with a technology-agnostic inference orchestration engine (e.g., vLLM, Ollama, Llama.cpp, TGI) exposed through a unified API gateway (LiteLLM Proxy).
- **FR-01.5 (Remote Consumption & IDE Access):** Students must be able to query deployed models via OpenAI-compatible endpoints or secure remote sessions (API key tokens) from any location/IDE.

### FR-02: Resource Reservation & Quota Governance (Fair-Share)
- **FR-02.1 (Time-Slot & Resource Reservations):** Students and faculty must be able to reserve computing slots in advance with automated start and termination windows.
- **FR-02.2 (Class & Academic Priority):** Academic courses (e.g., the 24-student AI elective) must have configurable reservation priority over individual thesis or exploratory tasks.
- **FR-02.3 (Overbooking / Over-quota Buffer):** The reservation engine must support a controlled over-allocation buffer (10% to 20%) under statistical assumption that not all concurrent students exhaust peak burst inference simultaneously.
  - **Origin of the 10–20% range (confirmed 2026-09-06):** this is an **IAsLab design decision**, not a figure taken from literature. Its stated rationale is the lab administrators' experience managing concurrent workloads and optimising GPU resources, informed by usage patterns observed in previous course offerings. Write it up as a design decision attributed to the laboratory — **never** cite it to an external source. No historical-usage dataset is on file in this repository, so the thesis must not present numbers, charts, or statistics derived from those observations unless the lab supplies the underlying data.
- **FR-02.4 (Fine-Grained Dynamic RBAC):** Dynamic role-based access control coupled with Universidad Icesi's **SAAMFI** identity provider, distinguishing between:
  - *Undergraduate Thesis Students (PDG / TFG)*
  - *Elective Course Students (Electiva IA)*
  - *Cross-faculty non-CS Students (Special request reservations)*
  - *Seed Researchers (Semilleros de Investigación)*
  - *Research Professors & Lab Administrators*
- **FR-02.5 (Automated Session Cutoff & Notifications):** When a reserved session reaches its expiration threshold, the system must warn the user, save inference logs/session state, and gracefully deallocate or freeze the compute container.

### FR-03: Infrastructure Observability & Telemetry
- **FR-03.1 (Hardware Telemetry Collection):** Real-time monitoring of GPU metrics (RTX 4080 temperature, VRAM utilization, power draw in Watts, PCIe throughput) and node metrics (CPU usage, system RAM, disk I/O).
- **FR-03.2 (Model & Inference Telemetry):** Tracking input/output tokens per second, request latency (Time to First Token - TTFT, Inter-Token Latency - ITL), queue wait times, and concurrency saturation.
- **FR-03.3 (Centralized Logging Stack - LGP):** Centralized log aggregation and tracing (e.g., Loki / Fluentd, Prometheus, Grafana) to diagnose node crashes, GPU freezing, and out-of-memory (OOM) events.
- **FR-03.4 (Automated Health & Recovery Diagnostics):** Automated detection when a worker node or GPU becomes unresponsive (e.g., when VRAM hits 90%+ saturation or hardware freezes), triggering diagnostic alerts and self-healing container restarts.

### FR-04: Automated Benchmarking & Evaluation Suite
- **FR-04.1 (Evaluation Pipeline):** Python-driven automated benchmarking engine executing test suites defined in declarative YAML files.
- **FR-04.2 (Code & Reasoning Tasks):** Generating code and reasoning responses from deployed models against structured user stories, measuring output quality, accuracy, token generation speed, and runtime latency.
- **FR-04.3 (Inference Engine Comparison):** Providing formal comparative data to benchmark different inference engines under identical workloads.

---

## 3. Non-Functional Requirements (NFR)

| ID | Category | Requirement Specification |
| :--- | :--- | :--- |
| **NFR-01** | **Deployment Environment** | Strictly **on-premise** deployment within IAsLab physical servers and workstation clusters. No reliance on commercial public clouds (AWS, GCP, Azure). |
| **NFR-02** | **Heterogeneous Architecture** | High-performance GPU machines (NVIDIA RTX 4080 nodes) dedicated to inference/computation, while legacy dedicated servers handle orchestration planes, control nodes, and database persistence. |
| **NFR-03** | **Storage Partitioning** | High-volume storage separation: dedicated fast NVMe/SSD partitions for model weights (10GB–50GB per checkpoint) isolated from system logs and root OS drives. |
| **NFR-04** | **Usability & Low Friction** | Intuitive web interface designed for students across disciplines, minimizing command-line complexity for model deployment and reservation. |
| **NFR-05** | **Security & Authentication** | Mandatory SSO integration with Universidad Icesi's **SAAMFI** service; secure API token management with expiration periods. |
| **NFR-06** | **Fault Tolerance & Node Isolation** | Failure or freeze of a single student inference container must not destabilize neighboring containers or the host Kubernetes/Ray node. |

---

## 4. Hardware Constraints & Operational Assumptions

- **Target Accelerator Hardware:** NVIDIA GeForce RTX 4080 (16 GB GDDR6X VRAM) per compute node.
- **Cluster Control Plane:** Run on dedicated host servers that remain permanently energized without unannounced restarts.
- **Model Size Constraints:** Models must fit within 16 GB VRAM using appropriate quantization (e.g., 4-bit AWQ/GGUF for 7B–14B models, or distributed tensor-parallelism if multi-GPU clusters are engaged).
- **Network Environment:** Universidad Icesi internal campus intranet with reverse-proxy routing for authorized remote access.
