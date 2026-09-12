# Technical Stack & Architectural Ecosystem: IAsLab PDG

This document defines the technology stack, architectural layers, orchestration frameworks, and telemetry tooling selected for the **IAsLab Web Extension Project of Degree (PDG)** at Universidad Icesi.

---

## 1. High-Level Architectural Layers (This archecture has not been defined fully yet, but the following is a preliminary outline of the system's layered architecture.)

The system architecture is structured across four primary layers:

```
┌────────────────────────────────────────────────────────────────────────┐
│ 1. PRESENTATION & ACCESS LAYER (Frontend & API Gateway)                │
│    • Web GUI (React / Next.js control plane for deployment & quotas)   │
│    • AI Gateway (OpenAI-compatible entry point + quota enforcement;    │
│      NOT LiteLLM — adopted or built, see section B.1)                  │
│    • SAAMFI (Institutional Identity Provider & OAuth/SAML Auth)        │
├────────────────────────────────────────────────────────────────────────┤
│ 2. ORCHESTRATION & CLUSTERING LAYER (Distributed Workload Management)  │
│    • Kubernetes (Container orchestration, node selectors, pods)        │
│    • KubeRay / Ray Core (Distributed AI compute & worker scaling)      │
│    • NVIDIA GPU Operator (Hardware passthrough & driver provisioning)  │
├────────────────────────────────────────────────────────────────────────┤
│ 3. INFERENCE SERVING ENGINES & OPTIMIZATION (Hardware Acceleration)    │
│    • vLLM (PagedAttention, continuous batching, high-throughput)       │
│    • Ollama / Llama.cpp (Low-overhead quantized GGUF execution)        │
│    • Quantization Kernels (AWQ, GPTQ, bitsandbytes 4-bit/8-bit)        │
├────────────────────────────────────────────────────────────────────────┤
│ 4. OBSERVABILITY, LOGGING & BENCHMARKING (Telemetry & Validation)      │
│    • PLG / LGP Stack (Prometheus, Loki / Fluentd, Grafana)             │
│    • NVIDIA DCGM Exporter (GPU power, temp, VRAM, PCIe metrics)        │
│    • Automated Python Benchmark Engine (YAML-driven test harness)      │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Component Specifications & Technical Rationale

### A. Orchestration & Distributed Computing

#### 1. Kubernetes (K8s)
- **Role:** Base container orchestrator managing worker nodes, storage volumes, and service discovery.
- **Key Features Used:**
  - **Node Selectors & Taints/Tolerations:** Directing GPU-heavy pods specifically to RTX 4090 nodes while isolating control services on legacy CPU machines.
  - **Resource Quotas & Limits:** Enforcing physical memory and CPU constraints per container.
  - **Persistent Volume Claims (PVCs):** Mounting high-speed NVMe storage partitions dedicated to model repositories and checkpoints.

#### 2. KubeRay & Ray Core
- **Role:** Distributed runtime designed specifically for scalable Python and AI workloads.
- **Key Features Used:**
  - **Ray Actors & Serves:** Managing dynamic lifecycle of inference workers without Kubernetes container recreation overhead.
  - **Heterogeneous Cluster Scheduling:** Seamlessly executing distributed tasks across mixed CPU and GPU topologies.
  - **Cluster State Tracking:** Detecting disconnected nodes and rescheduling pending jobs automatically.

#### 3. NVIDIA GPU Operator
- **Role:** Automates the management of all NVIDIA software components needed to provision GPUs in Kubernetes.
- **Key Features Used:**
  - Automatic driver injection, NVIDIA Container Toolkit runtime, and device plugin exposure to the cluster.

---

### B. Inference Gateway & Serving Engines

#### 1. AI Gateway (LiteLLM Proxy **not adopted** — corrected by the authors 2026-09-12, ADR-024 closed)
- **Decision:** the project does **not** adopt LiteLLM Proxy as its gateway, even though the laboratory already has it deployed. Reason: the platform must govern **any** AI/ML workload, not only LLM traffic, and a token-oriented LLM proxy does not cover non-LLM models. The tutor had said the same on 2026-08-26 (*"no tengamos que usar LightLLM [LiteLLM], toca hacer el LightLLM pero puramente enfocado a cualquier AI Gateway"*).
- **How the decision resolves:** if the theoretical-framework review (`thesis/chapters/05-marco-teorico.tex`) identifies an existing technology that enforces quotas across arbitrary model workloads, that technology is adopted. If none fits, the quota-enforcement layer is built by the project.
- **Role the component still has to play:** a single entry point exposing an OpenAI-compatible surface (`/v1/chat/completions`, `/v1/models`) so standard clients (Python `openai`, LangChain, LlamaIndex, IDE plugins) work against local IAsLab models; routing across available model replicas; and per-user quota and rate-limit enforcement with usage logging.
- **Status in the thesis:** LiteLLM belongs in the *estado del arte* as prior art, not in the architecture as a dependency (tutor, 2026-08-26: *"Puede ir en el documento como, por ejemplo, estado de la práctica"*).

#### 2. High-Performance Inference Engines
- **vLLM:**
  - *Strengths:* Implements PagedAttention to eliminate memory fragmentation in KV-cache; supports continuous request batching and high-concurrency throughput.
  - *Target Workloads:* Multi-user concurrent access during elective courses and high-load empirical tests.
- **Ollama / Llama.cpp:**
  - *Strengths:* Minimal runtime overhead, native support for quantized GGUF weights, and CPU offloading fallback.
  - *Target Workloads:* Single-user lightweight sessions and lower-spec exploratory models.

#### 3. Quantization Technologies (consumed, not implemented — ADR-021 closed 2026-09-12)
- **AWQ / GPTQ / GGUF:**
  - *Purpose:* 4-bit/8-bit representations of 7B, 13B and 14B parameter models are what let a model instance fit inside the 24 GB VRAM of an RTX 4090 node (confirmed 2026-09-12 by the authors — see `requirements.md` §4).
  - *Project boundary:* **the platform does not run a quantization process of its own.** It deploys weights that already come quantized, and it may rely on whatever quantization the serving engine applies natively at load time (`llama.cpp` does this when a model is selected and deployed). A model that would require a separate, project-run quantization step is out of scope and must be supplied pre-quantized. See FR-01.3.

---

### C. Governance, Identity & Access

#### 1. SAAMFI (Universidad Icesi)
- **Role:** Institutional authentication and authorization directory.
- **Integration:** Maps authenticated student and faculty credentials directly to internal platform roles (Undergraduate Thesis, AI Elective, Research Faculty, Lab Admin), controlling access permissions and reservation-based GPU allocation, with professors holding priority to claim resources and control room-level allocation (corrected 2026-09-12, see `requirements.md` FR-02.7 — not a Fair-Share scheme).

---

### D. Observability & Telemetry Stack (LGP / PLG)

#### 1. Prometheus
- **Role:** Time-series metric collection and alerting engine.
- **Metrics Collected:** Node CPU, RAM, disk space, and Kubernetes container resource usage.

#### 2. NVIDIA DCGM Exporter (Data Center GPU Manager)
- **Role:** Exposes low-level hardware metrics from the NVIDIA RTX 4090 cards directly to Prometheus.
- **Metrics Tracked:**
  - GPU Core & Memory Temperature (°C).
  - VRAM Utilization (allocated vs. free bytes).
  - Active Power Draw (Watts) and throttle states.
  - PCIe bandwidth transmission rates.

#### 3. Grafana
- **Role:** Interactive dashboarding and real-time visualization layer.
- **Panels Provided:** Real-time hardware telemetry dashboard, student quota consumption views, and inference performance charts (latency, TTFT, tokens/sec).

#### 4. Loki & Promtail (or Fluentd)
- **Role:** Centralized log aggregation.
- **Purpose:** Captures stdout/stderr from model containers, detects CUDA out-of-memory (OOM) failures, freezes, and enables forensic debugging of unresponsive nodes.

---

### E. Automated Benchmarking Engine

#### 1. Custom Python Benchmark Harness
- **Role:** Automated evaluation pipeline for empirical validation of model performance and inference engine speed.
- **Architecture:**
  - Declarative YAML test suites defining structured prompt tasks, user stories, and coding challenges.
  - Python test runner tracking Time to First Token (TTFT), Inter-Token Latency (ITL), token generation rates, and automated syntactic correctness verification.
