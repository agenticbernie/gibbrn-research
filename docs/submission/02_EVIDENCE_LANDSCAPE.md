# 02 — Evidence Landscape and Systems State of the Art (Submission)

**Project Name:** GIBBRN  
**Document Track:** Empirical Literature & Systems Landscape  
**Date:** September 2026 | **Verification Pass:** V3 Delta Pending Verification  
**Audience:** Distributed Systems Researchers, AI Security Architects, 1517 Fund  
**Evidence Standard:** All externally checkable claims are supported by cited primary sources. Citations should be independently verified. Epistemic classifications: Established Evidence | Emerging Evidence | GIBBRN Inference | Design Hypothesis | Engineering Target.

---

## 1. Executive Synthesis: The Tripartite Layering of Autonomous Systems

A foundational systems insight emerging from 2024–2026 artificial intelligence research is the physical and computational decoupling of the agent execution stack into three distinct layers (substrates):

```text
+-----------------------------------------------------------------------------------+
| LAYER 1: ADAPTIVE COGNITION (Mutable)                                             |
| Properties: Probabilistic, evolving. Changes skills, memories, and harness policy.|
| Function: Heuristic reasoning, semantic translation, candidate action proposal.   |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| LAYER 2: EXECUTION SUBSTRATE (Framework / Runtime)                                |
| Properties: Event loop, durable state, recovery, and isolation.                   |
| Function: Formats prompts, invokes local APIs, manages transient active cache.    |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| LAYER 3: TRUST SUBSTRATE & INTEGRITY CONTROL (gibbrn Proposed Wedge)              |
| Properties: Canonical, deterministic, append-only, out-of-process, enforced.      |
| Function: Capability gates, identity, provenance tracking, sandbox containment.   |
+-----------------------------------------------------------------------------------+
```

The public systems and product literature reviewed for this dossier is substantially richer in foundation-model capabilities and orchestration/runtime developer tooling than in framework-neutral agent-state integrity controls, leaving long-horizon autonomous systems vulnerable to epistemic drift, privilege laundering, and compounding failure cascades.

---

## 2. Empirical Research Findings Shaping this Dossier

### 2.1 Continual Learning via Skill-Space [UNVERIFIED — CITATION NOT CONFIRMED / SINGLE-STUDY CLAIM WITHHELD FROM BRIEF]
A dossier draft cited a "MASkills framework (arXiv:2609.02094, 2026)" for procedural skill-space optimization. A September 2026 search did not confirm this arXiv ID or title (related but distinct skill-optimization papers exist, e.g. Skill-MAS, SkillMOO, MIND-Skill, ABSTRAL — none matching the cited ID). Until the exact source is confirmed by the founder:
- This claim is **not** used as evidence in the executive brief (`10_1517_TECHNICAL_BRIEF.md`).
- Engine 3 motivation rests instead on the verified HarnessDev portability deficit (§2.2), MINJA poisoning (§2.7), and self-reflection limits (§2.6).
- *Founder action required:* provide the correct citation or remove the MASkills reference.

### 2.2 Harness Co-adaptation and Portability Deficits (HarnessDev) [SUPPORTED — SINGLE BENCHMARK, SEPT 2026]
Self-improving harnesses exist but transfer unreliably. HarnessDev (Wu et al., arXiv:2609.01437, Sept 2, 2026) shifts evaluation from task outputs to runnable harness infrastructure across 6 creator LLMs, 4 domains, and 5 downstream benchmarks (2,207 unique downstream instances; held-out tasks withheld from development). Reported findings: generated harnesses remain substantially behind mature human-engineered references on code and on search/research, while matching or exceeding selected references on writing and ML experimentation; evolution gains on visible feedback shrink on held-out tasks (largest held-out improvement +4.44 points, Opus 4.8) and exhibit executor dependence (gains often require running with the same model that created the harness). This establishes *harness generalization* as a distinct, unsolved systems problem and directly motivates RQ5/ATR. *Limits:* single benchmark release; held-out suite cannot cover all real-world diversity; score noise can mislead automated evolution (authors' own caveat).

### 2.3 Agent Identity as Enterprise Infrastructure [EMERGING EVIDENCE]
Agent identity is crossing from academic safety discussions into deployed enterprise security infrastructure. The introduction of the CrowdStrike Agentic Identity Provider (Sept 2026) and legislative efforts like the Stop Rogue AI Act signal a convergence between agent security and IAM. Autonomous agents evidence suggests production agents may increasingly be assigned distinct authenticated identities, scoped delegation, continuous authorization, and action provenance—trust anchors that the cognitive system cannot unilaterally control.

### 2.4 Exploratory Future Validity: 3D-Aware World Action Models [UNVERIFIED — WITHHELD FROM BRIEF]
A dossier draft cited "Spatially Aware World Action Model via Geometric Latent Diffusion (arXiv:2609.02531)" for geometry-aware action prediction. A September 2026 search did not confirm this arXiv ID or title. The general direction (action-conditioned world models) is plausible but **no specific paper is claimed here**. This exploratory track makes no evidential demand on the 24-month program. *Founder action required:* provide the correct citation or remove the reference.

### 2.5 Harness Architecture Sensitivity [ESTABLISHED SENSITIVITY; CAUSAL ATTRIBUTION PRE-EXPERIMENTAL]
Evaluated across different harness configurations, SWE-bench resolution rates vary substantially across the literature — differences on the order of tens of percentage points have been observed between architectural approaches applied to the same benchmark with similar models (Yang et al., NeurIPS 2024 [SWE-agent]; Xia et al., 2024 [Agentless]). These comparisons are not fully controlled experiments; scaffolding, prompt design, and model selection co-vary. The magnitude of observed differences motivates gibbrn's investigation of harness-level state semantics as a significant independent variable. No single "27.4 percentage point holding model constant" effect is claimed.

### 2.6 In-Context Self-Reflection is Non-Monotonic (`SUPPORTED`)

*   **Initial Literature:** Early agent papers (e.g., Reflexion, Shinn et al., NeurIPS 2023 [6]) hypothesized that verbal self-reflection—allowing a model to inspect its mistakes and write natural language advice—guaranteed monotonic performance improvement.
*   **Empirical Contradictions:** Subsequent rigorous studies directly refuted universal monotonicity:
    - **Jie Huang et al. (ICLR 2024)** [7] demonstrated that without external ground-truth verifiers, large language models do not reliably self-correct reasoning and often degrade their own outputs through ungrounded second-guessing.
    - **Valmeekam et al. (NeurIPS 2023)** [8] demonstrated that LLMs struggle with autonomous plan validation in domain-independent planning problems without external symbolic validators.
*   **Systems Implication for gibbrn (`GIBBRN INFERENCE` $\to$ `DESIGN HYPOTHESIS`):** This motivates testing external, ground-truth validation (e.g., deterministic test suites, compilers, type checkers) as an objective gate for durable operational memory, rather than relying solely on model self-reflection.

---

### 2.7 Persistent Memory Poisoning (OWASP ASI06 / MINJA) (`SUPPORTED / DEMONSTRATED IN EVALUATED SETTINGS`)

*   **The Security Threat:** The OWASP GenAI Security Project officially identified **Memory Poisoning** as a critical vulnerability class (**ASI06**) in autonomous agent deployments, in the Official Release v1.0, December 2025 [9].
*   **Attack Mechanism (MINJA):** S. Dong et al. (NeurIPS 2025, arXiv:2503.03704) [10] demonstrated query-only memory injection. Reported averages: ~98.2% malicious-record injection rate and ~76.8% attack success in eliciting malicious reasoning, averaged across evaluated agents and victim-target pairs (EHR/medical, e-commerce, QA settings). Rates vary by configuration; no single ">85% success" figure is claimed as universal. See primary paper Tables for per-setting breakdowns.
*   **Temporal Decoupling:** Unlike transient prompt injection—which terminates when the context window is cleared—memory poisoning plants backdoors in persistent vector or relational stores that trigger weeks later during unrelated privileged tasks.
*   **Systems Implication for gibbrn (`GIBBRN INFERENCE` $\to$ `DESIGN HYPOTHESIS`):** gibbrn therefore treats memory reads as untrusted inputs and proposes gating mutating tool dispatches through an independent, deterministic reference monitor outside the model's context.

---

### 2.8 Error Cascades and Trajectory Survival (`EMERGING EVIDENCE`)

*   **Cascading / State-Dependent Error Propagation:** Zhu et al. (arXiv:2509.25370, Sept 2025) [11] analyzed failure trajectories across GAIA, WebShop, and ALFWorld, introducing the AgentErrorTaxonomy, the AgentErrorBench annotated failure-trajectory dataset, and the AgentDebug debugging framework. The paper reports collecting 500+ failed trajectories for taxonomy development; the exact curated benchmark evaluation subset size should be confirmed against the paper/codebase (ulab-uiuc/AgentDebug) and pre-registered at Gate M6 — this dossier does not fix a single "200" figure as established fact.
*   **Mathematical Modeling:** Trajectory completion over dependency depth $k$ violates memoryless independent trial assumptions ($P \ne p^k$) due to error autocorrelation. The research program models trajectory reliability using **discrete survival analysis** to account for step-dependent conditional hazard rates:
    $$S(k) = \prod_{i=1}^k (1 - h(i))$$
*   **Systems Implication for gibbrn (`RESEARCH HYPOTHESIS`):** The program tests whether external state checkpoints and causal rollback can bound the empirical failure hazard rate $h(k)$ and extend autonomous operating horizons.

---

## 3. Systematic Competitive Landscape

Table 2.1 analyzes the eight primary commercial and architectural substitutes to gibbrn, highlighting what they solve and where the gibbrn wedge sits.

### Table 2.1: Competitive Substitute Matrix

| System / Platform | Primary Architectural Category | Durable Execution | State Persistence Model | Authority & Privilege Enforcement | Causal Provenance | Verified Adaptation | Rollback & Recovery | Primary Limitation Addressed by gibbrn |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Temporal / Cadence** | Durable Workflow Engine | **Native (Gold Standard)** | Workflow event log | Host IAM / RBAC | Activity history | None | Workflow history replay | Durability via deterministic workflow code + non-deterministic activities (Event History memoization). Supports LLM-driven dynamic branching at runtime; does not by itself validate whether an LLM-proposed side effect reflects laundered in-context authority. |
| **DBOS (dbos.dev)** | Database-Centric OS | **Native (PostgreSQL)** | Relational tables | Database roles / SQL | Transaction log | None | Time-travel debugging | Focuses on database-level execution speed. Public documentation reviewed did not identify native support for agent-specific semantic state models or out-of-process capability reducers. |
| **LangGraph (Checkpointers)**| Agent Graph Framework | Built-in (Savepoints) | Unvalidated state dict | Edge conditions | Trace spans | None | Human-in-the-loop rewind | LangGraph's native checkpoint/state abstractions manage workflow graph transitions but do not themselves constitute an external authorization reference monitor. |
| **Mem0 (mem0.ai) / Letta** | Agent Memory Layer | None | Vector / Graph RAG | None | User metadata | Naive summary | None | Focuses on personalization. Public documentation does not describe external regression validation; vulnerable to MINJA memory poisoning. |
| **Zep (getzep.com)** | Temporal Knowledge Graph | None | Temporal graph RAG | None | Temporal edge dates | None | None | Optimized for chat entity extraction. Does not gate tool execution or manage spending quotas. |
| **Portkey (portkey.ai)** | AI Gateway | Basic (Retries/Queues) | Cached responses | Virtual keys / Budgets | Request log | None | Fallback routing | Primarily a network gateway for LLM calls. Does not intercept local filesystem mutations, shell calls, or sandboxed tools. |
| **Lakera Guard / Promptfoo** | AI Security & Red-Teaming | None | None | Probabilistic prompt scan | Telemetry spans | None | None | Operates at the natural-language prompt/response inspection layer rather than enforcing deterministic kernel sandboxing or state constraints. |
| **SWE-agent / OpenHands** | Coding Agent Runtimes | Session-scoped | Working Git repo | Docker container | Bash execution logs | None | Git reset | Single-session execution runtime. Public documentation reviewed did not identify native support for cross-trajectory memory validation or cross-session capability reducers. |
| **GIBBRN (Proposed)** | **Agent State Integrity Layer** | Delegated (Postgres/DBOS) | **4-Tier Typed State Schema** | **Deterministic Authority Reducer** | **Causal State Spine** | **Regression-Gated Sandbox Admission** | **Bounded Causal Replay** | **Unified control plane separating mutable cognition from canonical authority and verified experience.** |

---

## 4. Comprehensive Evidence Matrix

Table 2.2 documents the empirical standing of every foundational proposition underlying this dossier.

### Table 2.2: Dossier Evidence Matrix

| Claim / Phenomenon | Source Literature | Evidence Status | Replicated / Confirmed | gibbrn Architectural Impact |
| :--- | :--- | :--- | :--- | :--- |
| Continual learning in procedural skill-space | *Citation withheld pending verification (see §2.1)* | **UNVERIFIED** | — | Engine 3 motivation does not depend on this claim. |
| Self-evolved harnesses show executor dependence and limited held-out transfer | HarnessDev (Wu et al., arXiv:2609.01437, Sept 2026) [16] | **SUPPORTED (single benchmark)** | 6 creators; 2,207 downstream instances; held-out evaluation withheld from development | Introduces RQ5 (Harness Generalization) and ATR metric. |
| Agent identity, scoped delegation, and IAM convergence | CrowdStrike Agentic Identity Provider (Press Release, Sept 2, 2026; Fal.Con 2026), Stop Rogue AI Act (Axios, Sept 3, 2026 — secondary report; bill text not independently verified) [17], [18] | **EMERGING INFRASTRUCTURE (product launch + press report)** | Vendor announcement; legislative status unconfirmed | Enforces Invariant 6 (Independent Trust Anchor) for IAM isolation. Product capabilities described are vendor claims, not independent test results. |
| Geometry-aware spatial world-action models | *Citation withheld pending verification (see §2.4)* | **UNVERIFIED** | — | Post-M24 exploratory track only; no evidential demand. |
| Runtime harness scaffolding is a significant variable on code tasks (exact magnitude uncontrolled across papers) | Yang et al. (NeurIPS 2024) [4], Xia et al. (2024) [5] | **ESTABLISHED SENSITIVITY; CAUSAL ATTRIBUTION PRE-EXPERIMENTAL** | Observed across SWE-bench Lite evaluations; comparative controls not fully isolated | Prioritizes runtime state control over model fine-tuning. |
| In-context self-reflection is non-monotonic without external grounding | Jie Huang et al. (ICLR 2024) [7], Valmeekam et al. (NeurIPS 2023) [8] | **SUPPORTED** | Confirmed across planning and reasoning benchmarks | Mandates external test-suite validators for experience admission. |
| Memory injection attacks (MINJA) compromise agent memory in evaluated configurations | S. Dong et al. (NeurIPS 2025) [10], OWASP ASI06 [9] | **SUPPORTED / DEMONSTRATED IN EVALUATED SETTINGS (injection ~98.2% avg; attack ~76.8% avg; configuration-dependent)** | Evaluated frontier-model agent configurations in paper | Decouples memory reads from capability authorization. |
| Trajectory failures cascade via state-dependent error propagation | Zhu et al. (arXiv:2509.25370, Sept 2025) [11] | **EMERGING EVIDENCE** | 500+ trajectories collected for taxonomy; curated benchmark subset size to be confirmed and pre-registered | Adopts discrete survival analysis and checkpoint rollback. |
| Endogenous authority laundering occurs when permissions are in prompt | OWASP [9]; handcrafted goal-hijacking / prompt-leaking demonstrations [12] | **SUPPORTED (attack primitive) / GIBBRN INFERENCE (authority-laundering framing)** | Prompt injection per se confirmed (Perez & Ribeiro, 2022); permission-rewriting inside agent prompt context is the gibbrn interpretation under test (RQ3) | Mandates testing deterministic out-of-context authority reducers. |
| Event ordering and transactional recovery primitives | Lamport (1978) [13], Bernstein et al. (1987) [14] | **ESTABLISHED SYSTEMS FOUNDATIONS** | Classic distributed systems standards | Foundational guarantees for state sequencing and durability. |
| Agent failure attribution via an event-sourced Causal State Spine | gibbrn systems design hypothesis | **GIBBRN DESIGN HYPOTHESIS** | Pre-experimental (Target of Core RQ2 at Gate M6) | Evaluates whether causal DAG parent chaining achieves $\ge 80\%$ root-cause attribution. |
| Hermetic replay fails on open-web mutable APIs | Systems engineering red-team analysis | **ESTABLISHED** | Known distributed systems limitation | Separates hermetic replay from open-world causal audit. |
| Universal state projection across multiple agent frameworks | gibbrn design hypothesis | **SPECULATIVE** | Unproven (Exploratory track) | High-risk assumption; deferred beyond core M1–M15 gates. |

---

## References

*   [1] OpenAI, "Learning to Reason with LLMs," OpenAI Technical Announcement (Blog Post), Sept. 2024.
*   [2] LangChain Team, "LangGraph Documentation," LangChain, Inc., https://langchain-ai.github.io/langgraph/, accessed September 2026.
*   [3] C. Packer et al., "MemGPT: Towards LLMs as Operating Systems," *arXiv preprint arXiv:2310.08560*, 2023.
*   [4] J. Yang, C. E. Jimenez, A. Wettig, K. Lieret, S. Yao, K. Narasimhan, and O. Press, "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, vol. 38, 2024. arXiv:2405.15793.
*   [5] C. S. Xia, Y. Ding, L. Zhang, and T. Zhang, "Agentless: Demystifying LLM-based Software Engineering Agents," *arXiv preprint arXiv:2407.01489*, 2024.
*   [6] N. Shinn, F. Cassano, E. Berman, A. Gopinath, K. Narasimhan, and S. Yao, "Reflexion: Language Agents with Verbal Reinforcement Learning," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, vol. 36, 2023.
*   [7] J. Huang, X. Chen, S. Mishra, H. S. Zheng, A. W. Yu, X. Song, and D. Zhou, "Large Language Models Cannot Self-Correct Reasoning Yet," in *Proc. Int. Conf. Learn. Represent. (ICLR)*, 2024.
*   [8] K. Valmeekam, M. Marquez, S. Sreedharan, and S. Kambhampati, "On the Planning Abilities of Large Language Models: A Critical Investigation," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, vol. 36, 2023.
*   [9] OWASP GenAI Security Project, "OWASP Top 10 for Agentic AI Applications," Official Release v1.0, December 2025. Category ASI06: Memory & Context Poisoning.
*   [10] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, 2025. arXiv:2503.03704. [Submitted March 2025; accepted NeurIPS 2025.]
*   [11] K. Zhu, Z. Liu, B. Li, M. Tian, Y. Yang, J. Zhang, et al., "Where LLM Agents Fail and How They Can Learn From Failures," *arXiv preprint arXiv:2509.25370*, Sept 2025. Introduces AgentErrorTaxonomy, AgentErrorBench (annotated failure trajectories across ALFWorld, GAIA, WebShop), and AgentDebug (ulab-uiuc/AgentDebug). Curated evaluation subset size to be confirmed against paper/codebase and pre-registered at Gate M6.
*   [12] F. Perez and I. Ribeiro, "Ignore Previous Prompt: Attack Techniques For Language Models," *arXiv preprint arXiv:2211.09527*, Nov 2022 (ML Safety Workshop, NeurIPS 2022). Demonstrates goal hijacking and prompt leaking on GPT-3 via handcrafted inputs (PromptInject). Supports the narrow claim that crafted prompts can hijack model goals and leak prompt content; the "authority laundering" framing for agent permission state remains a GIBBRN inference, not a finding of this paper. *(Correction Sept 2026: earlier dossier versions cited arXiv:2305.14874, which is an unrelated paper — "From Words to Wires." A prior verification ledger incorrectly confirmed the wrong ID; see correction note in `docs/verification/FINAL_VERIFY_01_CITATION_LEDGER.md`. Not every "primary citations verified" label in older ledgers was re-checked line-by-line; current citation status is per-reference in this section.)*
*   [13] L. Lamport, "Time, Clocks, and the Ordering of Events in a Distributed System," *Commun. ACM*, vol. 21, no. 7, pp. 558–565, 1978.
*   [14] P. A. Bernstein, V. Hadzilacos, and N. Goodman, *Concurrency Control and Recovery in Database Systems*. Addison-Wesley, 1987.
*   [15] *Withheld pending verification* — MASkills citation removed from evidence. See §2.1. Do not cite arXiv:2609.02094 until confirmed by founder.
*   [16] Y. Wu et al., "HarnessDev: Can LLMs Create and Evolve Their Own Agent Harness?," *arXiv preprint arXiv:2609.01437*, Sept 2026. Benchmark: 6 creator LLMs, 4 domains, 5 downstream benchmarks (2,207 instances); held-out evaluation withheld from development loop.
*   [17] CrowdStrike Holdings, Inc., "Introducing CrowdStrike Agentic Identity Provider," Press Release, Sept 2, 2026 (Fal.Con 2026). Vendor product announcement; capabilities as vendor claims.
*   [18] Axios, "House bill targets rogue AI agents security," Sept 3, 2026. Secondary press report; bill text and status not independently verified.
*   [19] *Withheld pending verification* — geometry-aware world-action-model citation removed. See §2.4.
