# 04: Systems Architecture & Engine Design

**Document Track:** Systems Engineering & Implementation (Version 4.0)  
**Date:** September 2026 | **Dossier Version:** 4.0 (36-Month Systems Research & Prototype Program)  
**Audience:** Systems Engineers, Security Auditors

## 1. Core Systems Design: The Three-Substrate Boundary

In response to the rapid emergence of adaptive agent architectures (e.g., continual skill learning, self-improving harnesses), the gibbrn architecture explicitly models the boundary between mutable cognition and immutable governance via three conceptual substrates, physically implemented across three primary engines. **V4 preserves exactly three physical engines.** Goal Contract, migration semantics, team-state, world-state research, and governance are conceptual layers or experimental modules evaluated by the engines — they do not become new daemons.

### 1.1 The Conceptual Substrates

1.  **Adaptive Cognition (The Mutable Layer):** The probabilistic LLM layer and its immediate working context. This layer is permitted to dynamically mutate skills, tool strategies, workflows, and harness policies based on environmental feedback.
2.  **Execution Substrate (The Isolation Layer):** The physical runtime that brokers state, enforces isolation boundaries, and manages scheduling/recovery for the cognitive layer.
3.  **Trust Substrate (Externally Governed Layer):** The hard boundary governing identity, capability grants, enterprise policy, and cryptographic provenance. The Trust Substrate acts as the absolute control plane: *Cognition may propose actions; it may never independently expand its own authority in the Trust Substrate.*

### 1.2 The Three Physical Engines (V4)

```text
+-----------------------------------------------------------------------------------+
| ENGINE 1: CAUSAL & CONTINUITY STATE SPINE                                       |
| (Canonical State, Identity & Adaptation Lineage Substrate)                        |
| - High-throughput Merkle DAG event-spine (Rust/gRPC) replacing scattered context. |
| - Records identity lineage, Goal Contract lineage, authority chains, skill        |
|   lineage, validation versions, permits, effect receipts, outcome evidence,       |
|   migration checkpoints, pending commitments.                                     |
+-----------------------------------------------------------------------------------+
| ENGINE 2: DETERMINISTIC EFFECT GATE / END-TO-END AUTHORITY & CONSEQUENCE          |
| INTEGRITY PIPELINE (Inline Policy, Network Authority & Kernel Sandbox) [WEDGE]    |
| - Enforces the Trust Substrate boundary across the full instruction-to-effect     |
|   path: authorization witness → endpoint resolution → network policy →             |
|   credential binding → execution permit → bounded executor → effect receipt.       |
| - Runs out-of-process as a synchronous interceptor proxy.                         |
| - Couples capability tokens with Tool Network Authority Broker + gVisor/seccomp.  |
+-----------------------------------------------------------------------------------+
| ENGINE 3: PROCEDURAL SKILL COMPILATION & VERIFIED ADAPTATION ENGINE               |
| - Pipeline: episodes → attribution → clustering → family abstraction →             |
|   de-instantiation → candidate procedure → deterministic checks → semantic         |
|   evaluator (advisory) → held-out evaluation → regression suite →                  |
|   commit / reject / quarantine → runtime specialization.                           |
+-----------------------------------------------------------------------------------+
```

---

## 2. High-Level Systems Topology and Dataflow

Figure 4.1 illustrates the runtime interaction between the agent harness, the three gibbrn engines, and the external environment. The V4 action path extends the V3 interception flow with endpoint authority, permit binding, and consequence reconciliation stages (Engine 2 pipeline, §3.2).

```mermaid
flowchart TD
    subgraph HostProcess["Untrusted User-Space (Python Agent Process)"]
        LLM["Foundation Model (Cognitive Layer)"]
        Harness["Agent Harness (LangGraph / AutoGen / Custom)"]
    end

    subgraph gibbrnControlPlane["Isolated Control Plane (Out-of-Process Daemon)"]
        Gate["ENGINE 2: Authority & Consequence Pipeline\n- Goal/Policy Context + Canonical Action\n- Authorization Witness + Tool/Network Authority Broker\n- Short-Lived Single-Use Leases (TTL <= 2s)\n- Execution Permits + Effect/Outcome Reconciliation"]
        Spine["ENGINE 1: Causal & Continuity Spine\n- Append-Only PostgreSQL / SQLite WAL\n- Merkle Causal DAG & Provenance\n- Identity/Goal/Authority/Skill Lineage\n- Permits, Receipts, Migration Checkpoints"]
        Admission["ENGINE 3: Procedural Skill Compilation\n- Procedural Clustering + Family Abstraction\n- Git Quarantine Staging Branch\n- Deterministic Checks + Advisory Semantic Evaluator\n- Held-Out Evaluation + Regression Runner"]
    end

    subgraph SandboxedExecution["Kernel-Contained Execution (gVisor Micro-Sandbox)"]
        Sandbox["Bounded Executor (seccomp / isolated netns)"]
        ExternalWorld["External APIs / DB / Git Filesystem"]
    end

    LLM -->|1. Proposed Action Token| Harness
    Harness -->|2. Intercept Proposed Action via Socket| Gate
    Gate -->|3. Query Capabilities, Goal Contract & Budget| Spine
    Gate -->|4a. DENY (Violation)| Harness
    Gate -->|4b. ALLOW (Issue Bound Execution Permit)| Sandbox
    Sandbox -->|5. Execute Contained Tool| ExternalWorld
    ExternalWorld -->|6. Raw Environment Return| Sandbox
    Sandbox -->|7. Verified Effect Receipt + Outcome Evidence| Gate
    Gate -->|8. Append Immutable Event + Reconcile| Spine
    Spine -->|9. Materialized Context View| Harness
    Spine -.->|10. Candidate Episodes| Admission
    Admission -.->|11. Promoted Procedural Skill| Spine
```

Target end-to-end action path (conceptual; each transition preserves or narrows authority per Invariant 8):

```text
Principal → Delegation → Goal / Policy Context → Proposed Action → Canonical Action
→ Authorization Witness → Tool Identity → Endpoint Resolution → Network Policy
→ Credential Binding → Execution Permit → Bounded Executor → External Effect
→ Effect Receipt → Outcome Evidence
```

---

## 3. Physical Engine Detailed Specifications

### 3.1 Engine 1: Causal & Continuity State Spine (Canonical State, Identity & Adaptation Lineage Substrate)
*   **Responsibility:** Acts as the immutable source of truth for all agent transitions, causal parent-child dependencies, external-effect receipts, checkpoint references, continuity records, and *adaptation provenance*.
*   **Physical Storage:** Backed by PostgreSQL 16 (production) or SQLite in WAL mode (edge/local). Does **not** invent a novel database; utilizes standard ACID transactions with optimistic concurrency control.
*   **Canonical record targets (V4 design targets — not implemented claims):** persistent `agent_lineage_id`; identity version; model binding; harness binding; runtime/host binding; Goal Contract lineage; delegated authority chain; verified skill lineage; validation suite version; canonical action hash; execution permit; effect receipt; observed outcome evidence; migration checkpoint; pending commitments. Design targets are separated from empirically validated mechanisms: each record type is validated (or rejected) by its corresponding RQ gate before any production claim.
*   **Event Structure (extended example):**
    ```json
    {
      "event_id": "evt_0192a812",
      "parent_event_id": "evt_0192a7f0",
      "trajectory_id": "traj_swe_341",
      "agent_id": "worker_agent_04",
      "agent_lineage_id": "aln_9f31c4",
      "identity_version": 7,
      "model_binding": "tier1-frozen-m7",
      "harness_binding": "hv_3",
      "goal_contract_version": "gc_012",
      "step_depth": 18,
      "event_type": "EFFECT_COMMITTED",
      "timestamp_utc": "2026-09-03T19:20:00.104Z",
      "adaptation_lineage": {
          "active_skill_id": "sk_parser_v2",
          "procedural_family": "pf_parse_repair",
          "validator_version": "rv_11"
      },
      "authorization_witness": "wit_55aa01",
      "execution_permit": "permit_single_use_ttl2000",
      "payload_hash": "sha256:4f83b165..."
    }
    ```
*   **Migration support (RQ7):** quiesce–checkpoint–validate–bind–rehydrate–resume semantics are recorded as first-class checkpoint events so a Model A→B / Harness A→B / Host A→B / Runtime A→B move preserves attributable lineage and continuation authority. Target is mechanical operational continuity, not behavioral invariance.
*   **Hermetic Replay vs. Causal Auditability:**
    - *Hermetic Replay:* For sealed environments, the Spine deterministically restores filesystem and database state to checkpoint $C_k$, injecting recorded tool outputs up to step $k$.
    - *Open-World Causal Audit:* For unmockable open-web APIs, the Spine provides high-fidelity forensic divergence tracking, identifying the exact step where environment state diverged.

### 3.2 Engine 2: Deterministic Effect Gate / End-to-End Authority & Consequence Integrity Pipeline
*   **Responsibility:** Serves as the active reference monitor across the full instruction-to-effect path, connecting agent actions strictly to the Trust Substrate (identity, delegated authority, Goal Contract, IAM policies) and reconciling realized effects against authorization witnesses. Researches the preservation or explicit narrowing of authority semantics across each transition (Invariant 8).
*   **Deployment Topology:** Runs out-of-process as a standalone Rust or Go daemon communicating via Unix domain sockets. This guarantees that if the Python agent harness is compromised via prompt injection or memory corruption, the attacker cannot tamper with the Effect Gate's memory.
*   **TOCTOU Safeguard:** All capability grants are issued as single-use leases with a maximum TTL $\le 2000\text{ms}$. The lease is atomically verified and burned at the exact millisecond of tool invocation.
*   **Tool Network Authority Broker (V4 — GIBBRN systems design response, not established industry practice):** The cognitive agent determines *I need capability X*. The control plane determines which authenticated endpoint may satisfy X, from which network zone, with which credential, under which scope, for how long, and under which resource/parameter constraints. Explicitly separated: semantic tool capability; tool identity; endpoint identity; network authority; credential scope; execution authority. Motivated by CVE-2026-85666, where caller-supplied MCP `server_url` selection became server-side network reachability: semantic permission to use a tool must never implicitly confer infrastructure authority to reach an arbitrary endpoint.
*   **Defense Against Parameter Smuggling:** Tool authorization is strictly coupled with **OS-level kernel containment**:
    - Every mutating tool executes inside an ephemeral **gVisor (runsc) micro-container** via the bounded executor.
    - Strict Linux seccomp filters block raw socket creation and prevent access to sensitive host directories, neutralizing parameter-level data exfiltration.
*   **Consequence reconciliation:** the bounded executor returns an effect receipt plus outcome evidence; the pipeline reconciles realized effect against the execution permit and authorization witness (Invariant 9). Delivery, enforcement outcome, and observed effect are distinct recorded facts.

### 3.3 Engine 3: Procedural Skill Compilation & Verified Adaptation Engine
*   **Responsibility:** Governs the transition of transient trajectory successes into permanent, reusable procedural knowledge ($\mathcal{S}_{\text{ops}}$) and portable runtime strategies — now via procedural-family abstraction (SkillGLoW precedent, arXiv:2609.02217) under PROCTOR-style evaluator discipline (arXiv:2609.02246).
*   **V4 target pipeline:**
    ```text
    Raw episodes
            → outcome attribution
                    → procedural clustering
                            → procedural-family abstraction
                                    → removal of instance-specific details
                                            → candidate reusable procedure
                                                    → deterministic checks
                                                            → semantic evaluator (ADVISORY ONLY)
                                                                    → independent held-out evaluation
                                                                            → regression suite
                                                                                    → commit / reject / quarantine
                                                                                            → runtime specialization
    ```
*   **Disciplined scope:** verifier-rich initial scope is preserved. No expansion into arbitrary natural-language self-modification.
*   **Commit semantics:** semantic evaluation may provide evidence but does not hold unilateral promotion authority. Acceptance checks outrank the evaluator; frozen holdouts and canary cases constrain gaming; the proposing component cannot apply its own approved mutations.
*   **Admission Lifecycle (V4):**
    ```text
    Raw Trajectory Episodes
                     |
                     v
    Outcome Attribution + Procedural Clustering
                     |
                     v
    Candidate Procedural Family (de-instantiated)
                     |
                     v
    Commit to Git Staging Branch (Status: QUARANTINE)
                     |
                     v
    Deterministic Checks + Advisory Semantic Review
                     |
                     v
    Independent Held-Out Evaluation + Regression in gVisor
                     |
             +--------+--------+
             | Passes          | Regresses or Times Out
             v                 v
    Signed & Promoted to   Discarded / Quarantined
      Active Substrate       (Zero Production Impact)
      (with lineage bindings)
    ```

---

## 4. Latency Budget and Performance Profile

Table 4.1 outlines the target latency budget for the Deterministic Effect Gate during synchronous tool interception.

### Table 4.1: Effect Gate Latency Budget — ENGINEERING DESIGN TARGETS

> **Note:** All latency figures in this table are ENGINEERING DESIGN TARGETS established prior to experimental validation. These are design goals informed by known Unix domain socket IPC latencies (<1ms typical) and gVisor warm-pool spawn latencies (1–15ms range in production configurations). Actual measured performance will be reported in Gate M3 deliverables. The V4 pipeline stages (endpoint resolution, permit binding, receipt reconciliation) are amortized inside the dispatch and commit steps; if pilot measurement shows the pipeline exceeds the synchronous budget, reconciliation moves to a bounded-async commit path disclosed at pre-registration — the security boundary (pre-execution gating) never moves async.

| Pipeline Step | Mechanism | Target Latency Budget |
| :--- | :--- | :--- |
| **1. Socket Ingestion** | Unix Domain Socket IPC from Agent Harness | $< 1.5\text{ms}$ |
| **2. Schema Validation** | Fast Pydantic / Rust Serde JSON AST validation | $< 2.0\text{ms}$ |
| **3. Capability & Lease Check** | In-memory bitmask query against active token set | $< 1.0\text{ms}$ |
| **4. Budget & Risk Balance Query** | In-memory atomic CAS counter verification | $< 1.5\text{ms}$ |
| **5. Sandbox Dispatch** | gVisor microVM spawn / reuse from warm pool | $< 8.0\text{ms}$ |
| **TOTAL SYNCHRONOUS OVERHEAD** | Pre-Execution Interception Phase | **$\le 14.0\text{ms}$** |
