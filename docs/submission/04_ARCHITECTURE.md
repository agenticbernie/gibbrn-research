# 04 — Systems Architecture and The Three Research Engines (Submission)

**Project Name:** GIBBRN  
**Document Track:** Systems Engineering & Engine Architecture (Version 2)  
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Audience:** Systems Architects, Distributed Infrastructure Engineers, 1517 Fund  
**Engineering Principle:** Minimalist Substrate; Maximum State Semantics  

---

## 1. Architectural Consolidation: 5 Concepts $\to$ 3 Physical Engines

In response to the adversarial diligence audit (`AUDIT_05`), Dossier V2 eliminates subsystem bloat. While five conceptual areas remain useful for theoretical analysis, gibbrn implements **exactly three cohesive physical research engines**:

```
+-----------------------------------------------------------------------------------+
|                        GIBBRN THREE PHYSICAL ENGINES                              |
+-----------------------------------------------------------------------------------+
| ENGINE 1: THE CAUSAL STATE SPINE (Storage & Lineage Substrate)                   |
| - Merges State Spine + Flight Recorder.                                           |
| - Backed by append-only PostgreSQL / SQLite WAL.                                  |
| - Manages Merkle DAG event trees, effect receipts, and checkpoint snapshots.      |
+-----------------------------------------------------------------------------------+
| ENGINE 2: THE DETERMINISTIC EFFECT GATE (Inline Policy & Kernel Sandbox)          |
| - Merges Authority Plane + Effect Gate + Lifetime Risk Ledger.                   |
| - Runs out-of-process as a synchronous interceptor proxy.                         |
| - Couples capability tokens with gVisor/seccomp kernel containment.              |
+-----------------------------------------------------------------------------------+
| ENGINE 3: THE EXPERIENCE ADMISSION ENGINE (Verifier-Rich Skill Governance)        |
| - Manages candidate skill extraction, Git quarantine branches, and micro-tests.   |
| - Narrowed strictly to verifier-rich domains (Python/Bash scripts inside sandbox).|
+-----------------------------------------------------------------------------------+
```

---

## 2. High-Level Systems Topology and Dataflow

Figure 4.1 illustrates the runtime interaction between the agent harness, the three gibbrn engines, and the external environment.

```mermaid
flowchart TD
    subgraph HostProcess["Untrusted User-Space (Python Agent Process)"]
        LLM["Foundation Model (Cognitive Layer)"]
        Harness["Agent Harness (LangGraph / AutoGen / Custom)"]
    end

    subgraph gibbrnControlPlane["Isolated Control Plane (Out-of-Process Daemon)"]
        Gate["ENGINE 2: Deterministic Effect Gate\n- Capability Tokens & Budget Balances\n- Short-Lived Single-Use Leases (TTL <= 2s)\n- TOCTOU Concurrency Arbiter"]
        Spine["ENGINE 1: Canonical State & Adaptation Lineage\n- Append-Only PostgreSQL / SQLite WAL\n- Merkle Causal DAG & Provenance\n- Checkpoint Snapshots & Effect Receipts"]
        Admission["ENGINE 3: Verified Adaptation Engine\n- Git Quarantine Staging Branch\n- Micro-Sandbox Regression Runner\n- Validated Operational Knowledge (S_ops)"]
    end-Only PostgreSQL / SQLite WAL\n- Merkle Causal DAG & Provenance\n- Checkpoint Snapshots & Effect Receipts"]
        Admission["ENGINE 3: Experience Admission\n- Git Quarantine Staging Branch\n- Micro-Sandbox Regression Runner\n- Validated Operational Knowledge (S_ops)"]
    end

    subgraph SandboxedExecution["Kernel-Contained Execution (gVisor Micro-Sandbox)"]
        Sandbox["Ephemeral Container (seccomp / isolated netns)"]
        ExternalWorld["External APIs / DB / Git Filesystem"]
    end

    LLM -->|1. Proposed Action Token| Harness
    Harness -->|2. Intercept Proposed Action via Socket| Gate
    Gate -->|3. Query Capabilities & Budget| Spine
    Gate -->|4a. DENY (Violation)| Harness
    Gate -->|4b. ALLOW (Issue Lease)| Sandbox
    Sandbox -->|5. Execute Contained Tool| ExternalWorld
    ExternalWorld -->|6. Raw Environment Return| Sandbox
    Sandbox -->|7. Verified Effect Receipt| Gate
    Gate -->|8. Append Immutable Event| Spine
    Spine -->|9. Materialized Context View| Harness
    Spine -.->|10. Candidate Trajectory| Admission
    Admission -.->|11. Promoted Skill| Spine
```

---

## 3. Physical Engine Detailed Specifications

### 3.1 Engine 1: Canonical State & Adaptation Lineage Substrate
*   **Responsibility:** Acts as the immutable source of truth for all agent transitions, causal parent-child dependencies, external-effect receipts, checkpoint references, and *adaptation provenance*.
*   **Physical Storage:** Backed by PostgreSQL 16 (production) or SQLite in WAL mode (edge/local). Does **not** invent a novel database; utilizes standard ACID transactions with optimistic concurrency control.
*   **Event Structure:**
    ```json
    {
      "event_id": "evt_0192a812",
      "parent_event_id": "evt_0192a7f0",
      "trajectory_id": "traj_swe_341",
      "agent_id": "worker_agent_04",
      "step_depth": 18,
      "event_type": "EFFECT_COMMITTED",
      "timestamp_utc": "2026-09-03T19:20:00.104Z",
      "adaptation_lineage": {
          "active_skill_id": "sk_parser_v2",
          "harness_variant": "hv_3"
      },
      "payload_hash": "sha256:4f83b165..."
    }
    ```
*   **Hermetic Replay vs. Causal Auditability:**
    - *Hermetic Replay:* For sealed environments, the Spine deterministically restores filesystem and database state to checkpoint $C_k$, injecting recorded tool outputs up to step $k$.
    - *Open-World Causal Audit:* For unmockable open-web APIs, the Spine provides high-fidelity forensic divergence tracking, identifying the exact step where environment state diverged.

### 3.2 Engine 2: The Deterministic Effect Gate (Inline Policy & Kernel Sandbox)
*   **Responsibility:** Serves as the active reference monitor intercepting all proposed external mutations, connecting agent actions strictly to the Trust Substrate (identity, delegated authority, IAM policies).
*   **Deployment Topology:** Runs out-of-process as a standalone Rust or Go daemon communicating via Unix domain sockets. This guarantees that if the Python agent harness is compromised via prompt injection or memory corruption, the attacker cannot tamper with the Effect Gate's memory.
*   **TOCTOU Safeguard:** All capability grants are issued as single-use leases with a maximum TTL $\le 2000\text{ms}$. The lease is atomically verified and burned at the exact millisecond of tool invocation.
*   **Defense Against Parameter Smuggling:** Tool authorization is strictly coupled with **OS-level kernel containment**:
    - Every mutating tool executes inside an ephemeral **gVisor (runsc) micro-container**.
    - Strict Linux seccomp filters block raw socket creation and prevent access to sensitive host directories, neutralizing parameter-level data exfiltration.

### 3.3 Engine 3: Verified Adaptation Engine
*   **Responsibility:** Governs the transition of transient trajectory successes into permanent, reusable operational knowledge ($\mathcal{S}_{\text{ops}}$) and portable runtime strategies.
*   **Disciplined Scope Reduction:** Engine 3 focuses explicitly on two empirical adaptation pipelines:
    1.  *Experience $\to$ Procedural Skill:* Extracting verified Python/Bash macros from raw trajectories and evaluating them against deterministic test matrices.
    2.  *Harness Variant $\to$ Model Binding:* Identifying whether a learned harness optimization transfers to a hidden task or alternative model.
*   **Admission Lifecycle:**
    ```text
    Raw Trajectory Success (Depth d >= 5)
                     |
                     v
      [Candidate Abstraction / Harness Mutation]
                     |
                     v
    Commit to Git Staging Branch (Status: QUARANTINE)
                     |
                     v
    Execute against Canonical Regression Tasks in gVisor
                     |
             +--------+--------+
             | Passes          | Regresses or Times Out
             v                 v
    Signed & Promoted to   Discarded / Quarantined
      Active Substrate       (Zero Production Impact)
    ```json
    {
      "event_id": "evt_0192a812",
      "parent_event_id": "evt_0192a7f0",
      "trajectory_id": "traj_swe_341",
      "agent_id": "worker_agent_04",
      "step_depth": 18,
      "event_type": "EFFECT_COMMITTED",
      "timestamp_utc": "2026-09-03T19:20:00.104Z",
      "payload_hash": "sha256:4f83b165...",
      "effect_receipt": {
        "idempotency_key": "idem_88f91a",
        "tool_name": "git_commit",
        "return_code": 0
      }
    }
    ```
*   **Hermetic Replay vs. Causal Auditability:**
    - *Hermetic Replay:* For sealed environments (local Docker containers, mock network, fixed git trees), the Spine deterministically restores filesystem and database state to checkpoint $C_k$, injecting recorded tool outputs up to step $k$.
    - *Open-World Causal Audit:* For unmockable open-web APIs where environment entropy prevents deterministic replay, the Spine provides high-fidelity forensic divergence tracking, identifying the exact step where environment state diverged.

### 3.2 Engine 2: The Deterministic Effect Gate (Inline Policy & Kernel Sandbox)
*   **Responsibility:** Serves as the active reference monitor intercepting all proposed external mutations before they execute.
*   **Deployment Topology:** Runs out-of-process as a standalone Rust or Go daemon communicating via Unix domain sockets. This guarantees that if the Python agent harness is compromised via prompt injection or memory corruption, the attacker cannot tamper with the Effect Gate's memory.
*   **TOCTOU Safeguard:** All capability grants are issued as single-use leases with a maximum TTL $\le 2000\text{ms}$. The lease is atomically verified and burned at the exact millisecond of tool invocation.
*   **Defense Against Parameter Smuggling:** Tool authorization is strictly coupled with **OS-level kernel containment**:
    - Every mutating tool (e.g., shell command, Python script) executes inside an ephemeral **gVisor (runsc) micro-container**.
    - Strict Linux seccomp filters block raw socket creation and prevent access to sensitive host directories (`/etc`, `~/.ssh`, `~/.aws`), neutralizing parameter-level data exfiltration even if the agent is authorized to run bash commands.

### 3.3 Engine 3: The Experience Admission Engine (Verifier-Rich Skill Governance)
*   **Responsibility:** Governs the transition of transient trajectory successes into permanent, reusable operational knowledge ($\mathcal{S}_{\text{ops}}$).
*   **Disciplined Scope Reduction:** In Dossier V2, broad "autonomous skill induction" is explicitly deferred. Engine 3 focuses exclusively on **verifier-rich execution domains**:
    1.  *Deterministic Python Functions:* Automated data parsers, regex extractors, and transformation scripts.
    2.  *Bash / DevOps Tool Macros:* Repository-specific build commands, linting scripts, and test runners.
*   **Admission Lifecycle:**
    ```
    Raw Trajectory Success (Depth d >= 5)
                     |
                     v
      [Candidate Heuristic Extraction]
                     |
                     v
    Commit to Git Staging Branch (Status: QUARANTINE)
                     |
                     v
    Execute against 20 Canonical Regression Tasks in gVisor
                     |
             +--------+--------+
             | Passes          | Regresses or Times Out
             v                 v
    Signed & Promoted to   Discarded / Quarantined
      Active S_ops         (Zero Production Impact)
    ```

---

## 4. Latency Budget and Performance Profile

Table 4.1 outlines the target latency budget for the Deterministic Effect Gate during synchronous tool interception.

### Table 4.1: Effect Gate Latency Budget — ENGINEERING DESIGN TARGETS (Target: $\le 15\text{ms}$ in-process; $\le 30\text{ms}$ end-to-end)

> **Note:** All latency figures in this table are ENGINEERING DESIGN TARGETS established prior to experimental validation. These are design goals informed by known Unix domain socket IPC latencies (<1ms typical) and gVisor warm-pool spawn latencies (1–15ms range in production configurations). Actual measured performance will be reported in Gate M3 deliverables.

| Pipeline Step | Mechanism | Target Latency Budget |
| :--- | :--- | :--- |
| **1. Socket Ingestion** | Unix Domain Socket IPC from Agent Harness | $< 1.5\text{ms}$ |
| **2. Schema Validation** | Fast Pydantic / Rust Serde JSON AST validation | $< 2.0\text{ms}$ |
| **3. Capability & Lease Check** | In-memory bitmask query against active token set | $< 1.0\text{ms}$ |
| **4. Budget & Risk Balance Query** | In-memory atomic CAS counter verification | $< 1.5\text{ms}$ |
| **5. Sandbox Dispatch** | gVisor microVM spawn / reuse from warm pool | $< 8.0\text{ms}$ |
| **TOTAL SYNCHRONOUS OVERHEAD** | Pre-Execution Interception Phase | **$\le 14.0\text{ms}$** |
