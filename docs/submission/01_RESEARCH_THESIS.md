# 01 — Problem Definition, Research Thesis, and Initial Technical Wedge (Submission)

**Project Name:** GIBBRN  
**Document Track:** Core Research Thesis & Problem Formulation  
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Audience:** Distributed Systems Researchers, AI Security Architects, 1517 Fund  
**Evidence Standard:** Epistemic demarcation required for all claims. Established | Emerging | GIBBRN Inference | Design Hypothesis | Engineering Target  

---

## 1. The Core Systems Problem: The Reliability Collapse of Long-Lived Agents

Modern foundation models exhibit remarkable reasoning capabilities across bounded, single-turn prompts or short conversational sessions [1], [2]. However, when developers compose these models into **autonomous, long-lived agents**—software systems intended to execute multi-step workflows, interact with mutating external systems, accumulate operational experience, and maintain deferred commitments over days or weeks—the software architecture suffers a structural failure:

> **Current agent frameworks conflate transient, probabilistic cognitive scratchpads with canonical, authoritative system state.**

In existing frameworks (e.g., LangGraph, AutoGen, CrewAI, OpenHands), an agent's state is predominantly maintained as an unstructured or semi-structured conversation context window [3], a hierarchical memory system storing unverified textual summaries [4], or an unvalidated application-level dictionary where tool outputs and system instructions interleave arbitrarily [5].

When deployed across long dependency chains, four compounding failure modes emerge:

```
+-----------------------------------------------------------------------------------+
|                        THE LONG-LIVED AGENT FAILURE PROFILE                       |
+-----------------------------------------------------------------------------------+
| 1. Epistemic Drift: Repeated context compression alters the factual record.       |
| 2. Authority Laundering: Model reflections rewrite permissions and scopes.        |
| 3. Memory & Skill Poisoning: Flawed heuristics become permanent behaviors.        |
| 4. Cascading State Errors: Early mistakes cause escalating downstream hazards. |
+-----------------------------------------------------------------------------------+
```

1.  **Epistemic Drift:** As context windows fill and are repeatedly summarized or retrieved via semantic similarity, subtle negative constraints and empirical execution facts drift. The model begins reasoning over its own imprecise memories rather than ground truth [6]. *(GIBBRN Inference from Dziri et al.'s compositionality findings)*
2.  **Endogenous Authority Laundering:** When authorization state (e.g., spending limits, file access boundaries, API permissions) is maintained inside prompt context, the model can inadvertently (or via indirect prompt injection) hallucinate that its authority has been elevated, granting itself out-of-scope capabilities without external cryptographic or deterministic validation [7].
3.  **Memory & Skill Poisoning:** When agents use naive reflection to store "lessons learned" in persistent retrieval stores, flawed, insecure, or adversarial heuristics (e.g., OWASP ASI06 / MINJA memory injection attacks) are committed to long-term memory, subverting future executions weeks or months later [7], [8].
4.  **Cascading State-Dependent Errors:** Trajectory failures do not follow memoryless coin flips; early errors alter the environment state and escalate the failure hazard of subsequent steps. Without external, canonical state checkpoints and rollback, long-horizon completion rates collapse [9]. *(Emerging Evidence; Zhu et al., arXiv:2509.25370, 2025)*

---

## 2. Updated Project Positioning: Research Thesis vs. Initial Wedge

To maintain disciplined systems boundaries, this dossier formally bifurcates the project into its **broad 18-month research thesis** and its **concrete initial technical wedge**:

### 2.1 The Broad Research Thesis: Agent State Integrity
> **gibbrn investigates whether a framework-neutral control layer can preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous agents operate and change over time.**

*North-Star Principle:*
> **Agents can change. Their integrity must persist.**

*Central Research Question:*
> **Which agent state may safely remain probabilistic and model-maintained, and which state must remain canonical, deterministic, provenance-preserving, validated, versioned, and externally enforced?**

### 2.2 The Initial Technical Wedge: Deterministic Authority and Effect Integrity
While the long-term research investigates full state integrity, the immediate 18-month engineering wedge is focused on a razor-sharp enterprise problem:

> **gibbrn is researching how autonomous agents can change their cognitive reasoning without silently changing what they are allowed to do in the external world.**

The initial wedge treats foundation model outputs strictly as **untrusted action proposals**, passing every mutating request through an external, deterministic reference monitor and kernel sandbox before any external side effect can occur.

---

## 3. The Strongest Counter-Thesis: Why gibbrn Might NOT Need to Exist

An authentic scientific proposal must confront the strongest argument against its own existence.

### The "Deterministic Pipeline + Frontier Model" Counter-Case:
> *Enterprises will never deploy open-ended, self-directed autonomous agents for consequential production workflows. Instead, production systems will converge on deterministic, hard-coded DAGs (e.g., the Agentless paradigm [10], Temporal workflows, or microservices) where foundation models are called only as narrow, stateless extraction functions.*

In that world:
- Agents never execute open-ended 50-step exploratory tool loops.
- Agents never dynamically write their own permissions.
- Agents never accumulate autonomous memories.
- Standard IAM, database transactions, and deterministic code eliminate the need for an independent Agent State Integrity Layer.

### The Testable Falsification Proposition:
gibbrn exists to test whether there is a viable, high-value systems territory between rigid pipelines and unmanaged chaos:

$$\text{Static Deterministic DAGs} \quad \subset \quad \mathbf{gibbrn\;(Managed\;Dynamic\;Autonomy)} \quad \subset \quad \text{Unmanaged Autonomous Loops}$$

```
Rigid Pipelines (Agentless / Temporal)   Managed Autonomy (gibbrn)      Unmanaged Loops (LangGraph / AutoGen)
---------------------------------------+-----------------------------+---------------------------------------
- Cannot handle novel branching        - Dynamic reasoning allowed   - Dynamic reasoning allowed
- Zero authority laundering risk       - Deterministic effect gate   - Severe authority laundering risk
- Brittle in changing environments     - Causal state checkpoints    - Uncontained compounding crashes
```

**The Falsification Test:** If empirical research demonstrates that real-world software engineering, DevOps, and multi-system IT tasks can be solved with equal or higher reliability by static pipelines without dynamic branching, **the gibbrn thesis is falsified, and the company should not exist.**

---

## 4. Falsifiable 24-Month Core Research Objective

The 24-month R&D program funded by this capital request is designed to validate or falsify the following formal proposition:

$$\mathcal{H}_1: \text{On tasks requiring dynamic exploratory branching and adaptation, a deterministic authority and state-integrity layer}$$
$$\text{measurably extends empirical trajectory survival depth and adaptation portability, while maintaining near-zero unauthorized effects,}$$
$$\text{without modifying underlying foundation model weights.}$$

$$\mathcal{H}_0: \text{External state integrity constraints provide no statistically significant improvement in long-horizon}$$
$$\text{task survival over unmanaged adaptive loops, or impose latency and execution friction that negates reliability gains.}$$

---

## 5. Explicit Non-Goals (What gibbrn Is NOT)

To maintain disciplined focus, gibbrn explicitly rejects the following scope:

1.  **NOT a Foundation Model:** gibbrn does not pre-train, post-train, or fine-tune models. It operates with frozen, off-the-shelf APIs and open weights.
2.  **NOT an AGI or Recursive Self-Improvement System:** gibbrn rejects unconstrained cognitive self-modification loops.
3.  **NOT an Agent Framework Replacement:** gibbrn does not replace LangGraph, AutoGen, CrewAI, or OpenHands. It sits alongside or underneath them as an out-of-process control plane.
4.  **NOT a Distributed Workflow Engine:** gibbrn does not build a new Temporal, Cadence, or DBOS. It delegates workflow scheduling and activity retries to established systems.
5.  **NOT a Vector Database:** gibbrn does not compete with Pinecone, Qdrant, or Chroma. Semantic vector indexing is an orthogonal retrieval tool.
6.  **NOT an Enterprise IAM Replacement:** gibbrn does not replace Okta or AWS IAM. It enforces transient, per-step capability scopes and ephemeral execution leases.
7.  **NOT a Generic Prompt Filter:** gibbrn does not rely on heuristic regex or probabilistic LLM-as-a-judge classifiers to detect attacks; it uses deterministic schema and kernel-level capability containment.

---

## References

*   [1] A. Achiam et al., "GPT-4 Technical Report," *arXiv preprint arXiv:2303.08774*, 2023.
*   [2] Gemini Team, "Gemini: A Family of Highly Capable Multimodal Models," *arXiv preprint arXiv:2312.11805*, 2023.
*   [3] J. S. Park et al., "Generative Agents: Interactive Simulacra of Human Behavior," in *Proc. ACM UIST*, 2023, pp. 1–22.
*   [4] C. Packer et al., "MemGPT: Towards LLMs as Operating Systems," *arXiv preprint arXiv:2310.08560*, 2023.
*   [5] C. Wu et al., "AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation," *arXiv preprint arXiv:2308.08155*, 2023.
*   [6] N. Dziri et al., "Faith and Fate: Limits of Transformers on Compositionality," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, vol. 36, 2023.
*   [7] OWASP GenAI Security Project, "OWASP Top 10 for Agentic AI Applications," Official Release v1.0, December 2025. Category ASI06: Memory & Context Poisoning.
*   [8] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, 2025. arXiv:2503.03704. [Submitted March 2025; accepted NeurIPS 2025.]
*   [9] K. Zhu, Z. Liu, B. Li, M. Tian, Y. Yang, J. Zhang, et al., "Where LLM Agents Fail and How They Can Learn From Failures," *arXiv preprint arXiv:2509.25370*, 2025. Benchmark dataset: AgentErrorBench (200 annotated failure trajectories across ALFWorld, GAIA, and WebShop; ulab-uiuc/AgentDebug).
*   [10] C. S. Xia et al., "Agentless: Demystifying LLM-based Software Engineering," *arXiv preprint arXiv:2407.01489*, 2024.
