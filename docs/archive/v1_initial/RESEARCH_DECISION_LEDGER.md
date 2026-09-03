# Research Decision Ledger (Living Systems Governance)

**Project Name:** GIBBRN  
**Document Track:** Historical Architecture Decision Records (ADRs)  
**Maintenance Rule:** Never delete or overwrite prior hypotheses. Every architectural pivot, pruning, or elevation must be preserved with empirical rationale.  
**Allowed Verdicts:** `KEEP` | `MODIFY` | `DEFER` | `KILL`  

---

## Decision Record Index

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

---

### AD-001: Broad "Adaptive Agent Runtime" vs. "State Integrity Layer"
*   **Date:** September 1, 2026
*   **Question:** Should gibbrn be positioned as an end-to-end execution runtime for autonomous agents?
*   **Evidence Examined:** Developer adoption trends of LangGraph, CrewAI, AutoGen, and Temporal.
*   **Supporting Evidence:** High demand for persistent execution in agent workflows.
*   **Contradictory Evidence:** Market is heavily saturated with runtime frameworks; developers resist replacing orchestration stacks. Workflow orchestration (retries, queues) is already solved by Temporal/Cadence. The true unaddressed point of failure is state corruption and authority leakage.
*   **Evidence Strength:** `ESTABLISHED`
*   **Decision:** **MODIFY**
*   **Confidence:** 95%
*   **What Changed:** Re-anchored project from a general runtime to an **Agent State Integrity Layer** that sits underneath or alongside existing runtimes.
*   **Next Experiment:** Benchmark integration overhead as an adapter inside LangGraph (RQ8).

---

### AD-002: Deployment-Time Model Weight Fine-Tuning
*   **Date:** September 1, 2026
*   **Question:** Should gibbrn include runtime LoRA fine-tuning to update model weights as tasks complete?
*   **Evidence Examined:** Continual learning literature, catastrophic forgetting in parameter updates.
*   **Supporting Evidence:** Direct parameter adaptation allows models to absorb low-level syntax patterns.
*   **Contradictory Evidence:** Deployment-time weight modification introduces severe instability, non-deterministic regression on general capabilities, high GPU compute costs, and complex weight-serving logistics.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **DEFER**
*   **Confidence:** 90%
*   **What Changed:** Weight adaptation is placed outside the 18-month core scope. Operational skills will be stored externally in Git/CAS and injected via structured context.
*   **Next Experiment:** RQ7 comparing external skill retrieval vs. fine-tuned baselines.

---

### AD-003: Bespoke Distributed Database & Consensus Protocol
*   **Date:** September 2, 2026
*   **Question:** Should gibbrn build a novel distributed consensus database or custom multi-agent transaction manager?
*   **Evidence Examined:** Transactional requirements of multi-agent systems; database systems literature.
*   **Supporting Evidence:** Agents require transactional safety across concurrent writes.
*   **Contradictory Evidence:** Building distributed databases takes a decade of engineering (e.g., CockroachDB, Spanner). Standard primitives (PostgreSQL WAL, optimistic concurrency control, Git CAS, Redis leases) fully satisfy agent state requirements at current throughputs.
*   **Evidence Strength:** `ESTABLISHED`
*   **Decision:** **KILL**
*   **Confidence:** 99%
*   **What Changed:** We explicitly reuse PostgreSQL, SQLite WAL, and Git. gibbrn innovates on agent-state semantics, not disk storage.
*   **Next Experiment:** Test SQLite WAL throughput during multi-step tool execution (Gate M3).

---

### AD-004: In-Context Verbal Self-Reflection for Memory Promotion
*   **Date:** September 2, 2026
*   **Question:** Can an agent's self-generated reflection on task success be used as the admission criteria for long-term memory?
*   **Evidence Examined:** Reflexion (Shinn et al.), empirical follow-ups (M. et al., 2025).
*   **Supporting Evidence:** Improves single-shot benchmark scores on simple math and text games.
*   **Contradictory Evidence:** Reflection is non-monotonic, prone to confirmation bias, easily hallucinates false causal rules, and accelerates epistemic drift over multi-step tasks.
*   **Evidence Strength:** `CONTRADICTED`
*   **Decision:** **KILL**
*   **Confidence:** 95%
*   **What Changed:** Pure model self-reflection is rejected as an admission mechanism. Promotion to Operational State requires external deterministic or test-backed verification.
*   **Next Experiment:** RQ4 comparing Reflexion memory against sandbox-validated skill admission.

---

### AD-005: Four-Tier Typed State Decomposition Taxonomy
*   **Date:** September 2, 2026
*   **Question:** Should agent state be formally decomposed into Cognitive, Operational, Authoritative, and Runtime/Safety classes?
*   **Evidence Examined:** Failure modes in LangGraph/AutoGen state dictionaries; security analysis of prompt injection.
*   **Supporting Evidence:** Flat state dictionaries allow prompt injections to overwrite authorization and tool state. Separating concerns isolates hallucinations.
*   **Contradictory Evidence:** Adds schema conversion overhead between framework state and gibbrn state.
*   **Evidence Strength:** `DESIGN HYPOTHESIS`
*   **Decision:** **KEEP**
*   **Confidence:** 85%
*   **What Changed:** Formalized Invariants 1–5 in `03_AGENT_STATE_MODEL_AND_INVARIANTS.md`.
*   **Next Experiment:** RQ1 testing state corruption rates on SWE-bench Lite.

---

### AD-006: Merkle-Causal Flight Recorder with Bounded Replay
*   **Date:** September 3, 2026
*   **Question:** Can event-sourced Merkle DAGs enable deterministic failure attribution and bounded recovery in stochastic agent loops?
*   **Evidence Examined:** Distributed systems event-sourcing; AgentErrorBench trajectory analysis.
*   **Supporting Evidence:** Traditional tracing logs the "what" but lacks cryptographic dependency links, making automated root-cause localization impossible.
*   **Contradictory Evidence:** External tools with non-idempotent side effects cannot be re-executed naively.
*   **Evidence Strength:** `EMERGING`
*   **Decision:** **KEEP**
*   **Confidence:** 80%
*   **What Changed:** Adopted **Bounded Causal Replay**: recorded tool receipts are replayed up to step $k$; live LLM inference is only re-engaged for novel downstream steps.
*   **Next Experiment:** RQ2 measuring causal reconstruction accuracy on 150 failure traces (Gate M6).

---

### AD-007: Deterministic Authority Reducer & Pre-Execution Effect Gate
*   **Date:** September 3, 2026
*   **Question:** Should tool authorizations be computed by a deterministic reducer outside the LLM context?
*   **Evidence Examined:** OWASP Top 10 for Agentic Applications (2026); MINJA attack vectors.
*   **Supporting Evidence:** Prompt-based permissions are trivially bypassed via prompt injection or model hallucination (authority laundering).
*   **Contradictory Evidence:** Dynamic tool calls with complex parameters are hard to evaluate with static rules.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **KEEP**
*   **Confidence:** 95%
*   **What Changed:** Built pre-execution interceptor architecture; models can only propose actions, never authorize them.
*   **Next Experiment:** RQ3 red-teaming with 100 prompt injection attacks (Gate M9).

---

### AD-008: Automated Micro-Sandbox Regression Suite for Experience Admission
*   **Date:** September 3, 2026
*   **Question:** Should newly discovered operational heuristics pass isolated sandbox testing before being promoted to durable memory?
*   **Evidence Examined:** Catastrophic forgetting benchmarks; memory poisoning propagation.
*   **Supporting Evidence:** Prevents flawed workarounds and poisoned heuristics from becoming permanent system behavior.
*   **Contradictory Evidence:** Regression testing introduces token and latency overhead.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **KEEP**
*   **Confidence:** 85%
*   **What Changed:** Built Git-backed quarantine branch and automated test runner pipeline into Subsystem 3.
*   **Next Experiment:** RQ4 measuring false-promotion rates under adversarial poisoning (Gate M12).

---

### AD-009: Lifetime-Scoped Persistent Risk Ledger Across Trajectories
*   **Date:** September 3, 2026
*   **Question:** Should safety checks persist across session boundaries rather than resetting on every task?
*   **Evidence Examined:** Distributed micro-exfiltration attack models; cumulative resource exhaustion.
*   **Supporting Evidence:** Session-scoped guardrails are blind to slow-burn attacks distributed across 100 sessions.
*   **Contradictory Evidence:** Risk counters might accumulate false positives and unnecessarily block benign long-running agents.
*   **Evidence Strength:** `EMERGING`
*   **Decision:** **KEEP**
*   **Confidence:** 80%
*   **What Changed:** Created Persistent Risk Ledger tracking lifetime spend, velocity, and anomaly counters.
*   **Next Experiment:** RQ5 testing detection of multi-session threshold-slicing attacks (Gate M15).

---

### AD-010: LLM-as-a-Judge for Root Privilege Evaluation
*   **Date:** September 3, 2026
*   **Question:** Can a secondary supervisory LLM act as the root authorization gate for high-risk tool calls?
*   **Evidence Examined:** Dual LLM security evaluations; jailbreak transferability studies.
*   **Supporting Evidence:** Flexible natural language evaluation of complex parameters.
*   **Contradictory Evidence:** Supervisory LLMs share the same fundamental failure modes as worker models; they are susceptible to indirect prompt injection, have high latency ($>800\text{ms}$), and add substantial token cost.
*   **Evidence Strength:** `CONTRADICTED`
*   **Decision:** **KILL**
*   **Confidence:** 95%
*   **What Changed:** Root authority evaluation must be strictly deterministic (regex, AST, type schemas, cryptographic tokens). LLM evaluation is demoted to advisory-only status.
*   **Next Experiment:** Benchmark Effect Gate latency with zero LLM-in-the-loop (Gate M9).

---

### AD-011: Framework-Neutral State Projection Adapter Layer
*   **Date:** September 3, 2026
*   **Question:** Should gibbrn maintain a canonical internal state and project it into LangGraph, AutoGen, and native formats via lightweight adapters?
*   **Evidence Examined:** Cross-framework interoperability challenges in Python; CQRS architectural pattern.
*   **Supporting Evidence:** Protects gibbrn from framework churn; allows enterprises to switch orchestrators without losing state history.
*   **Contradictory Evidence:** Maintaining multiple adapter projections introduces serialization maintenance burden.
*   **Evidence Strength:** `SPECULATIVE`
*   **Decision:** **KEEP**
*   **Confidence:** 75%
*   **What Changed:** Engineered CQRS projection model in Subsystem 1.
*   **Next Experiment:** RQ8 evaluating cross-runtime portability across LangGraph and SWE-agent (Gate M18).
