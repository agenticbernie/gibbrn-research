# 02 — Evidence Landscape and Systems State of the Art (Submission)

**Project Name:** GIBBRN  
**Document Track:** Empirical Literature & Systems Landscape  
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Audience:** Distributed Systems Researchers, AI Security Architects, 1517 Fund  
**Evidence Standard:** All externally checkable claims are supported by cited primary sources. Citations should be independently verified. Epistemic classifications: Established Evidence | Emerging Evidence | GIBBRN Inference | Design Hypothesis | Engineering Target.

---

## 1. Executive Synthesis: The Tripartite Layering of Autonomous Systems

A foundational systems insight emerging from 2024–2026 artificial intelligence research is the physical and computational decoupling of the agent execution stack into three distinct layers:

```
+-----------------------------------------------------------------------------------+
| LAYER 1: COGNITIVE PROCESSOR (Foundation Model)                                  |
| Properties: Probabilistic, autoregressive token generation, stateless weights.    |
| Function: Heuristic reasoning, semantic translation, candidate action proposal.   |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| LAYER 2: COMPUTATIONAL HARNESS (Framework / Execution Runtime)                    |
| Properties: Event loop, tool dispatcher, context window memory manager.           |
| Function: Formats prompts, invokes local APIs, manages transient active cache.    |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| LAYER 3: STATE INTEGRITY & CONTROL PLANE (gibbrn Proposed Wedge)                  |
| Properties: Canonical, deterministic, append-only, out-of-process, enforced.      |
| Function: Capability gates, provenance tracking, sandbox containment, checkpoints.|
+-----------------------------------------------------------------------------------+
```

The public systems and product literature reviewed for this dossier is substantially richer in foundation-model capabilities and orchestration/runtime developer tooling than in framework-neutral agent-state integrity controls, leaving long-horizon autonomous systems vulnerable to epistemic drift, privilege laundering, and compounding Markovian failure cascades.

---

## 2. Empirical Research Findings Shaping this Dossier

### 2.1 Harness Architecture Sensitivity (Observed Across Literature; Causal Attribution Pre-Experimental) [GIBBRN label]

*   **Literature Observation:** Research across SWE-bench evaluations (Yang et al., NeurIPS 2024 [4]; Xia et al., 2024 [5]) demonstrates that different agentic scaffolding architectures yield substantially different resolution rates on the same coding benchmark with similar models — differences on the order of tens of percentage points have been observed in the literature (e.g., Agentless achieving 32% resolve on SWE-bench Lite with GPT-4o [5]; SWE-agent achieving a different resolution profile with a custom agent-computer interface [4]).

    These comparisons are not fully controlled experiments — scaffolding design, prompt engineering, and model selection co-vary across papers. The magnitude of observed performance sensitivity motivates gibbrn's investigation of harness-level state semantics as a significant variable. The "harness architecture sensitivity" label is a GIBBRN characterization of this cross-paper pattern.

*   **The Agentless Finding (`SUPPORTED`):** Xia et al. [5] demonstrated that a three-phase pipeline (localization → repair → patch validation) matched or outperformed fully autonomous agent loops. The autonomous loops failed primarily due to **unconstrained state thrashing and context pollution**: once an agent executed a flawed bash command or introduced a syntax error, the error was summarized into context, biasing all subsequent decisions.

*   **Systems Implication for gibbrn (`GIBBRN INFERENCE` $\to$ `DESIGN HYPOTHESIS`):** Evidence indicates that unconstrained autonomous execution loops can experience severe state degradation under error conditions. This motivates testing whether external state isolation, causal checkpointing, and deterministic rollback can measurably improve trajectory reliability compared to unmanaged loops.

---

### 2.2 In-Context Self-Reflection is Non-Monotonic (`SUPPORTED`)

*   **Initial Literature:** Early agent papers (e.g., Reflexion, Shinn et al., NeurIPS 2023 [6]) hypothesized that verbal self-reflection—allowing a model to inspect its mistakes and write natural language advice—guaranteed monotonic performance improvement.
*   **Empirical Contradictions:** Subsequent rigorous studies directly refuted universal monotonicity:
    - **Jie Huang et al. (ICLR 2024)** [7] demonstrated that without external ground-truth verifiers, large language models do not reliably self-correct reasoning and often degrade their own outputs through ungrounded second-guessing.
    - **Valmeekam et al. (NeurIPS 2023)** [8] demonstrated that LLMs struggle with autonomous plan validation in domain-independent planning problems without external symbolic validators.
*   **Systems Implication for gibbrn:** Self-reflection cannot serve as the admission gate for durable operational memory. Experience promotion must require external, ground-truth validation (e.g., deterministic test suites, compilers, type checkers).

---

### 2.3 Persistent Memory Poisoning (OWASP ASI06 / MINJA) (`ESTABLISHED`)

*   **The Security Threat:** The OWASP GenAI Security Project officially identified **Memory Poisoning** as a critical vulnerability class (**ASI06**) in autonomous agent deployments, in the Official Release v1.0, December 2025 [9].
*   **Attack Mechanism (MINJA):** S. Dong et al. (NeurIPS 2025, arXiv:2503.03704) [10] demonstrated that attackers can inject persistent, delayed payloads into an agent's long-term retrieval memory via query-only interaction with >85% success across evaluated configurations (medical/EHR, e-commerce, and QA agent settings).
*   **Temporal Decoupling:** Unlike transient prompt injection—which terminates when the context window is cleared—memory poisoning plants backdoors in persistent vector or relational stores that trigger weeks later during unrelated privileged tasks.
*   **Systems Implication for gibbrn:** Memory reads cannot be directly piped into privileged tool calls. All tool dispatches must be verified by an independent, deterministic capability gate outside the model's context.

---

### 2.4 Error Cascades and Trajectory Survival (`EMERGING EVIDENCE`)

*   **Markovian Error Compounding:** Zhu et al. (AgentErrorBench, 2025) [11] analyzed failure trajectories across GAIA, WebShop, and ALFWorld in a dataset of 200 annotated failure cases, showing that multi-step failures are dominated by cascading errors where early, unrecovered minor deviations corrupt environment state.
*   **Mathematical Modeling:** Trajectory completion over dependency depth $k$ cannot be modeled as independent Bernoulli trials ($P \ne p^k$). It must be analyzed via **discrete survival analysis** where early errors spike the conditional hazard rate of fatal failure:
    $$S(k) = \prod_{i=1}^k (1 - h(i))$$
*   **Systems Implication for gibbrn:** Extending autonomous operating horizons requires bounding the hazard rate $h(k)$ via external state checkpoints and causal rollback.

---

## 3. Systematic Competitive Landscape

Table 2.1 analyzes the eight primary commercial and architectural substitutes to gibbrn, highlighting what they solve and where the gibbrn wedge sits.

### Table 2.1: Competitive Substitute Matrix

| System / Platform | Primary Architectural Category | Durable Execution | State Persistence Model | Authority & Privilege Enforcement | Causal Provenance | Experience Admission | Rollback & Recovery | Primary Limitation Addressed by gibbrn |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Temporal / Cadence** | Durable Workflow Engine | **Native (Gold Standard)** | Workflow event log | Host IAM / RBAC | Activity history | None | Workflow history replay | Assumes deterministic host code. Temporal's documented durability model does not provide agent-specific semantic validation of why a model proposed an effect. |
| **DBOS (dbos.dev)** | Database-Centric OS | **Native (PostgreSQL)** | Relational tables | Database roles / SQL | Transaction log | None | Time-travel debugging | Focuses on database-level execution speed. Lacks agent semantic state models and capability reducers. |
| **LangGraph (Checkpointers)**| Agent Graph Framework | Built-in (Savepoints) | Unvalidated state dict | Edge conditions | Trace spans | None | Human-in-the-loop rewind | LangGraph's native checkpoint/state abstractions manage workflow graph transitions but do not themselves constitute an external authorization reference monitor. |
| **Mem0 (mem0.ai) / Letta** | Agent Memory Layer | None | Vector / Graph RAG | None | User metadata | Naive summary | None | Focuses on personalization. Public documentation does not describe external regression validation; vulnerable to MINJA memory poisoning. |
| **Zep (getzep.com)** | Temporal Knowledge Graph | None | Temporal graph RAG | None | Temporal edge dates | None | None | Optimized for chat entity extraction. Does not gate tool execution or manage spending quotas. |
| **Portkey (portkey.ai)** | AI Gateway | Basic (Retries/Queues) | Cached responses | Virtual keys / Budgets | Request log | None | Fallback routing | Primarily a network gateway for LLM calls. Does not intercept local filesystem mutations, shell calls, or sandboxed tools. |
| **Lakera Guard / Promptfoo** | AI Security & Red-Teaming | None | None | Probabilistic prompt scan | Telemetry spans | None | None | Operates at the natural-language prompt/response inspection layer rather than enforcing deterministic kernel sandboxing or state constraints. |
| **SWE-agent / OpenHands** | Coding Agent Runtimes | Session-scoped | Working Git repo | Docker container | Bash execution logs | None | Git reset | Single-session execution runtime. Lacks cross-trajectory memory validation and cross-session authority reducers. |
| **GIBBRN (Proposed)** | **Agent State Integrity Layer** | Delegated (Postgres/DBOS) | **4-Tier Typed State Schema** | **Deterministic Authority Reducer** | **Causal State Spine** | **Regression-Gated Sandbox Admission** | **Bounded Causal Replay** | **Unified control plane separating mutable cognition from canonical authority and verified experience.** |

---

## 4. Comprehensive Evidence Matrix

Table 2.2 documents the empirical standing of every foundational proposition underlying this dossier.

### Table 2.2: Dossier Evidence Matrix

| Claim / Phenomenon | Source Literature | Evidence Status | Replicated / Confirmed | gibbrn Architectural Impact |
| :--- | :--- | :--- | :--- | :--- |
| Runtime harness scaffolding is a significant variable on code tasks (exact magnitude uncontrolled across papers) | Yang et al. (NeurIPS 2024) [4], Xia et al. (2024) [5] | **ESTABLISHED SENSITIVITY; CAUSAL ATTRIBUTION PRE-EXPERIMENTAL** | Observed across SWE-bench Lite evaluations; comparative controls not fully isolated | Prioritizes runtime state control over model fine-tuning. |
| In-context self-reflection is non-monotonic without external grounding | Jie Huang et al. (ICLR 2024) [7], Valmeekam et al. (NeurIPS 2023) [8] | **SUPPORTED** | Confirmed across planning and reasoning benchmarks | Mandates external test-suite validators for experience admission. |
| Memory injection attacks (MINJA) persistently compromise agent memory | S. Dong et al. (NeurIPS 2025) [10], OWASP ASI06 [9] | **ESTABLISHED** | Confirmed against evaluated frontier model configurations | Decouples memory reads from capability authorization. |
| Trajectory failures cascade via Markovian error propagation | Zhu et al. (AgentErrorBench 2025) [11] | **EMERGING EVIDENCE** | 200 annotated trajectories across ALFWorld/GAIA/WebShop | Adopts discrete survival analysis and checkpoint rollback. |
| Endogenous authority laundering occurs when permissions are in prompt | OWASP [9], Security research preprints [12] | **SUPPORTED** | Confirmed in prompt injection studies | Mandates deterministic out-of-context authority reducers. |
| Event-sourced causal tracking enables failure attribution | Lamport (1978) [13], Bernstein et al. (1987) [14] | **ESTABLISHED** | Classic distributed systems standard | Adopts append-only event ledger for Causal State Spine. |
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
*   [11] Zhu et al., "Where LLM Agents Fail and How They Can Learn From Failures: A Trajectory Failure Taxonomy and Benchmark," Research Report & Benchmark Suite (AgentDebug / AgentErrorBench; 200 annotated failure trajectories across ALFWorld, GAIA, and WebShop), 2025.
*   [12] F. Perez and I. Ribeiro, "Ignore Previous Prompt: Attack Techniques For Language Models," *arXiv preprint arXiv:2305.14874*, 2023.
*   [13] L. Lamport, "Time, Clocks, and the Ordering of Events in a Distributed System," *Commun. ACM*, vol. 21, no. 7, pp. 558–565, 1978.
*   [14] P. A. Bernstein, V. Hadzilacos, and N. Goodman, *Concurrency Control and Recovery in Database Systems*. Addison-Wesley, 1987.
