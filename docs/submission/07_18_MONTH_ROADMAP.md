# 07 — 18-Month Checkpoint-Gated R&D Roadmap (Submission)

**Project Name:** GIBBRN  
**Document Track:** Research Milestones & Governance Gates (Version 2)  
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Audience:** Technical Founders, Deep-Tech Investors, 1517 Fund  
**Governance Framework:** Six Empirical Checkpoint Gates (Proceed / Narrow / Pivot / Kill)  

---

## 1. Roadmap Architecture: Empirical Falsification Over Feature Sprints

Dossier V2 restructures the 18-month timeline to align strictly with the five causally chained research questions. Every three-month phase terminates in a binding **Checkpoint Gate** with explicit quantitative failure criteria.

```
+---------------------------------------------------------------------------------------------------------+
|                                    18-MONTH CHECKPOINT SCHEDULE                                         |
+---------------------------------------------------------------------------------------------------------+
| PHASE 1: M01 - M03 | Foundations & Interceptor Harness      | GATE M3: Intercept overhead <= 30ms       |
| PHASE 2: M04 - M06 | Causal State Spine & Provenance        | GATE M6: Root-cause attribution >= 80%    |
| PHASE 3: M07 - M09 | Deterministic Effect Gate (MAIN WEDGE) | GATE M9: UER <= 0.001, FDR <= 2.0%        |
| PHASE 4: M10 - M12 | Verifier-Rich Experience Admission     | GATE M12: False-promotion <= 2.0%         |
| PHASE 5: M13 - M15 | Long-Horizon Trajectory Survival       | GATE M15: MDDD >= 2.0x (Log-Rank p < 0.01)|
| PHASE 6: M16 - M18 | Replication, Staging & Final Verdict   | GATE M18: Formal Proceed / Pivot / Stop   |
+---------------------------------------------------------------------------------------------------------+
```

---

## 2. Detailed Milestone Specifications

### Months 01–03: Foundations, State Semantics, and Minimal Interceptor
*   **Primary Uncertainty Reduced:** Can consequential agent actions and state transitions be intercepted synchronously with useful semantics and tolerable latency?
*   **Key Engineering Deliverables:**
    - `gibbrn-schema-v0`: JSONSchema and Pydantic implementations of the Four-Class State Taxonomy.
    - Out-of-process Unix domain socket interceptor proxy for LangGraph and native Python loops.
    - Reproducible testbed runner with local container virtualization.
*   **Experiment Executed:** Core RQ1 (200 SWE-bench Lite tasks).
*   **Gate M3 Criteria:**
    - *Success Threshold:* Median interception overhead $\le 30\text{ms}$; state serialization exceptions reduced by $\ge 80\%$ vs. flat state dicts.
    - *Action if Failed:* **KILL / STOP.** If interception adds $>100\text{ms}$ or fundamentally breaks agent execution loops, the out-of-process proxy architecture is unviable.

---

### Months 04–06: Causal State Spine & Failure Attribution
*   **Primary Uncertainty Reduced:** Does structured, append-only causal state tracking materially outperform standard linear telemetry traces in locating the root cause of trajectory failures?
*   **Key Engineering Deliverables:**
    - Causal State Spine v1 (Engine 1) backed by PostgreSQL/SQLite WAL with SHA-256 Merkle DAG chaining.
    - Automated divergence localization algorithm for failed trajectories.
    - Bounded replay runner for hermetic container environments.
*   **Experiment Executed:** Core RQ2 (150 AgentErrorBench failure traces).
*   **Gate M6 Criteria:**
    - *Success Threshold:* Causal Reconstruction Rate $\text{CRR} \ge 80\%$ on blinded human/automated root-cause localization (achieving at least a $2\times$ gain over OpenTelemetry spans).
    - *Action if Failed:* **NARROW THESIS.** If replay proves fragile due to environment entropy, narrow the Spine strictly to forensic audit logging and proceed directly to the Effect Gate.

---

### Months 07–09: The Deterministic Effect Gate (Primary Technical Wedge)
*   **Primary Uncertainty Reduced:** Can an out-of-context deterministic reference monitor eliminate unauthorized external mutations and authority laundering without making agents unusable?
*   **Key Engineering Deliverables:**
    - Deterministic Effect Gate (Engine 2) running as an out-of-process daemon in Rust/Go.
    - Ephemeral single-use capability leases (TTL $\le 2000\text{ms}$) mitigating TOCTOU race conditions.
    - Integrated gVisor micro-sandbox containment for mutating shell/python tools.
*   **Experiment Executed:** Core RQ3 ($N = 1,000$ adversarial attacks in `gibbrn-auth-bench`).
*   **Gate M9 Criteria:**
    - *Success Threshold:* Unauthorized-Effect Rate $\text{UER} \le 0.001$ (0 breaches in 1,000 tests); False-Denial Rate $\text{FDR} \le 2.0\%$; median gate latency $\le 15\text{ms}$.
    - *Action if Failed:* **PIVOT.** If prompt injections bypass deterministic capability schemas, pivot from open tool execution to constrained Domain-Specific Languages (DSLs) or human-in-the-loop escalation.

---

### Months 10–12: Verifier-Rich Experience Admission
*   **Primary Uncertainty Reduced:** In verifier-rich domains, can automated micro-sandbox regression testing prevent memory poisoning without excessive token spend?
*   **Key Engineering Deliverables:**
    - Experience Admission Engine (Engine 3) managing Git quarantine staging branches.
    - Headless micro-sandbox test runner evaluating candidate Python/Bash macros against 20 frozen tasks.
    - Causal revocation protocol (rolling back operational skills that correlate with runtime crashes).
*   **Experiment Executed:** Core RQ4 (300 continual tasks with 15% MINJA adversarial poisoning).
*   **Gate M12 Criteria:**
    - *Success Threshold:* False-Promotion Rate $\text{FPR} \le 0.02$; downstream benchmark accuracy retention $\ge 98\%$ under poisoning pressure.
    - *Action if Failed:* **DEFER AUTONOMOUS ADMISSION.** If automated regression testing is economically unviable ($>3\times$ task token cost), defer fully autonomous skill promotion and introduce developer-assisted sign-off.

---

### Months 13–15: Long-Horizon Trajectory Survival (The Company-Level Thesis Gate)
*   **Primary Uncertainty Reduced:** Does managed dynamic autonomy (autonomous agent + gibbrn state checkpoints) achieve superior reliability on exploratory tasks compared to unmanaged autonomy and static pipelines?
*   **Key Engineering Deliverables:**
    - Integrated control plane combining Engine 1 (Spine) and Engine 2 (Effect Gate).
    - Dynamic checkpointing and causal rollback engine.
*   **Experiment Executed:** Core RQ5 (150 deep exploratory tasks from GAIA Level 3 and deep refactoring benchmarks).
*   **Gate M15 Criteria:**
    - *Success Threshold:* gibbrn extends trajectory survival depth such that $\text{MDDD}_{0.90}(\text{gibbrn}) \ge 2.0 \times \text{baseline}$ evaluated via the Log-Rank Test ($p < 0.01$). Must also demonstrate tasks where dynamic managed autonomy resolves problems that static pipelines (Agentless) cannot express.
    - *Action if Failed:* **KILL PROJECT / RETURN CAPITAL.** If state integrity and checkpoint rollback fail to double dependable survival depth, the central systems premise of the company is invalidated.

---

### Months 16–18: Replication, Cross-Model Staging, and Final Thesis Verdict
*   **Primary Objective:** Replicate findings across independent model families, validate open-source research artifacts, stage pilot trials with two design partners, and determine final commercialization.
*   **Key Engineering Deliverables:**
    - Replication across Anthropic and Google Tier 2 frontier model families (specific model versions to be frozen at Gate M16 for reproducibility). Open-source replication will use a Tier 3 open-weights model (Llama-family 70B-scale, version frozen at M16).
    - Packaged open-source research prototype + comprehensive Research Report & ADRs.
    - Instrumented pilot deployments with two external engineering teams.
*   **Gate M18 Final Decision:**
    - **PROCEED TO SEED ROUND:** If Gate M15 passes, pilots validate reduced crash costs, and cross-model replication succeeds.
    - **PIVOT TO NARROW SECURITY GATE:** If only the Effect Gate delivers defensible commercial value.
    - **STOP / DISSOLVE:** If foundation model provider updates render external state control obsolete.

---

## 3. Risk Matrix and Binding Kill Conditions

Table 7.1 establishes the formal conditions under which the research program will be narrowed or shut down.

### Table 7.1: Program Risk Matrix & Kill Triggers

| Risk Vector | Failure Trigger | Evaluation Point | Mandatory Governance Action |
| :--- | :--- | :--- | :--- |
| **R1: Interception Overhead** | Proxy adds $>50\text{ms}$ median latency to tool calls. | **Gate M3** | **KILL** sidecar architecture; attempt pure in-memory wrapper or terminate. |
| **R2: Replay Fragility** | External environment drift breaks $>50\%$ of replays in hermetic containers. | **Gate M6** | **KILL** live replay; restrict Engine 1 strictly to forensic audit logging. |
| **R3: Parameter Smuggling** | Injected payloads bypass Effect Gate via authorized tools without containment. | **Gate M9** | **PIVOT** to strict kernel sandbox isolation or abort unrestricted tool execution. |
| **R4: Admission Economics** | Regression testing consumes $>3\times$ original task cost with $>5\%$ false promotion. | **Gate M12** | **DEFER** autonomous admission; mandate human sign-off for memory updates. |
| **R5: Survival Failure** | Checkpoint rollback fails to double $\text{MDDD}_{0.90}$ over unmanaged baseline ($p \ge 0.01$). | **Gate M15** | **KILL COMPANY ENTIRELY**; return remaining capital to investors. |
