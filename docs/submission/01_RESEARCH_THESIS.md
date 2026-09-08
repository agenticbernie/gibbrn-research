# 01 — Problem Definition, Research Thesis, and Initial Technical Wedge (Submission)

**Project Name:** GIBBRN  
**Document Track:** Core Research Thesis & Problem Formulation  
**Date:** September 2026 | **Dossier Version:** 4.1 (36-Month Systems Research & Prototype Program)  
**Audience:** Distributed Systems Researchers, AI Security Architects, 1517 Fund  
**Evidence Standard:** Epistemic demarcation required for all claims. Established | Emerging Evidence | Early / Weak Signal | GIBBRN Inference | Design Hypothesis | Engineering Target

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

The September 2026 evidence delta (`02_EVIDENCE_LANDSCAPE.md` §3) extends this failure profile along the continuity axis: agents that change models, runtimes, skills, objectives, tools, or collaborators can additionally suffer **identity discontinuity** (which operational entity is this?), **objective drift** (what does success now mean?), **authority discontinuity** (did delegation survive the transformation?), **consequence mismatch** (did the realized effect match the authorized action?), and **coordination-state loss** (did the team forget how it works together?). Each is a distinct, falsifiable research target — not an established inevitability.

---

## 2. Updated Project Positioning: Research Thesis vs. Initial Wedge

To maintain disciplined systems boundaries, this dossier formally bifurcates the project into its **broad 36-month research thesis** and its **concrete initial technical wedge**:

### 2.1 The Broad Research Thesis: Continuity and Integrity for Long-Lived Adaptive Agents
> **GIBBRN investigates continuity and integrity for long-lived adaptive agents.**

> **GIBBRN investigates how long-lived adaptive agents can change models, runtimes, memory representations, skills, tools, collaborators, and execution environments while preserving canonical identity, authority, provenance, validated competence, objective integrity, and end-to-end consequence integrity.**

*North-Star Principle (retained):*
> **Agents can change. Their integrity must persist.**

*North-Star Research Question (V4):*
> **How can a long-lived autonomous system change its cognition, models, memory, skills, tools, runtime, environment, and collaborators without losing its identity, intended objective, validated competence, delegated authority, or the integrity of the consequences it produces?**

*Subordinate foundational question (retained from V3, now RQ1):*
> **Which agent state may safely remain probabilistic and model-maintained, and which state must remain canonical, deterministic, provenance-preserving, validated, versioned, and externally enforced?**

The V4 wording is a research hypothesis/program, not an established guarantee. The program succeeds empirically or is narrowed/killed at its major gates — it does not promise safe autonomy.

### 2.2 The Initial Technical Wedge: Deterministic Authority and Consequence Integrity
While the long-term research investigates full continuity, the immediate engineering wedge remains focused on a razor-sharp enterprise problem:

> **gibbrn is researching how autonomous agents can change their cognitive reasoning without silently changing what they are allowed to do in the external world — and whether the realized external effect matches what was authorized.**

The initial wedge treats foundation model outputs strictly as **untrusted action proposals**, passing every mutating request through an external, deterministic reference monitor and kernel sandbox before any external side effect can occur, and reconciling the realized effect against the authorization witness afterward (End-to-End Authority & Consequence Integrity Pipeline; see `04_ARCHITECTURE.md`).

### 2.3 The Three-Year Progression

```
YEAR 1 (M1–M12) — ACT SAFELY:   Can one adaptive agent act safely?
YEAR 2 (M13–M24) — CHANGE SAFELY: Can that agent change safely?
YEAR 3 (M25–M36) — PERSIST TOGETHER: Can persistent agents operate together
                                and remain governable over time? (conditional)
```

Year 3 activates only if earlier scientific gates justify continued expansion. Failure at any major gate narrows or stops the program rather than expanding it.

---

## 3. The Strongest Counter-Thesis: Why gibbrn Might NOT Need to Exist

An authentic scientific proposal must confront the strongest argument against its own existence.

### The "Deterministic Pipeline + Frontier Model" Counter-Case:
> *Enterprises will never deploy open-ended, self-directed autonomous agents for consequential production workflows. Instead, production systems will converge on deterministic, hard-coded DAGs (e.g., the Agentless paradigm [10], pre-wired Temporal workflows used as fixed DAGs, or microservices) where foundation models are called only as narrow, stateless extraction functions.*

*Clarification on Temporal:* Temporal's documented model separates deterministic workflow orchestration code from non-deterministic activities (LLM calls, tool executions recorded in Event History), so Temporal *can* execute LLM-driven dynamic branching at runtime (Temporal, "Of course you can build dynamic AI agents," Nov 2025; OpenAI Codex and Replit Agent cited as production users). gibbrn does not claim Temporal lacks dynamic branching. The counter-case concerns *pre-wired static DAGs operated as fixed pipelines* — whether implemented on Temporal, Step Functions, or hand-rolled code — versus tasks that require runtime exploratory branching. What Temporal's durability model does not by itself provide, per public documentation reviewed, is agent-specific semantic validation of whether an LLM-proposed side effect reflects laundered in-context authority.

The September 2026 τ^τ-Bench result (Shi et al., arXiv:2609.04611) sharpens — but does not settle — this counter-case from the opposite direction: even frontier coding agents currently struggle to *construct* production agent systems end-to-end (strongest configuration 23.9% vs. 82.2% expert reference across 53 tasks). Coding competence is not system-design competence. This counsels against assuming autonomous architecture design will quickly obsolete managed-autonomy infrastructure — while equally counseling against assuming it never will. The counter-case remains the program's falsification test.

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
- Minimal authority laundering risk    - Deterministic effect gate   - Severe authority laundering risk
  within fixed scopes*                   - Causal state checkpoints    - Uncontained compounding crashes
- Brittle in changing environments     - Causal state checkpoints    - Uncontained compounding crashes
```

*Static pipelines reduce — but do not eliminate — authority risk: misconfigured IAM scopes, overly broad tool permissions, or human error in DAG wiring can still authorize unintended effects. The reduction holds only within fixed, pre-approved scopes and does not generalize to open-ended branching.

**The Falsification Test:** If empirical research demonstrates that real-world software engineering, DevOps, and multi-system IT tasks can be solved with equal or higher reliability by static pipelines without dynamic branching, **the gibbrn thesis is falsified, and the company should not exist.**

---

## 4. Falsifiable Core Research Objective (36-Month)

The 36-month R&D program is designed to validate or falsify the following formal proposition:

$$\mathcal{H}_1: \text{On tasks requiring dynamic exploratory branching and adaptation, a deterministic authority and state-integrity layer}$$
$$\text{measurably extends empirical trajectory survival depth and adaptation portability, while maintaining near-zero unauthorized effects,}$$
$$\text{preserving mechanical operational continuity across model/runtime migration and objective integrity under adaptive optimization,}$$
$$\text{without modifying underlying foundation model weights.}$$

$$\mathcal{H}_0: \text{External state integrity constraints provide no statistically significant improvement in long-horizon}$$
$$\text{task survival over unmanaged adaptive loops, or impose latency and execution friction that negates reliability gains.}$$

The migration and objective-integrity clauses are tested in Year 2 (RQ7–RQ8); the multi-agent clauses (RQ9–RQ12) are conditional Year-3 research with independent kill criteria. No clause is claimed as established.

---

## 5. Explicit Non-Goals (What gibbrn Is NOT)

To maintain disciplined focus, gibbrn explicitly rejects the following scope:

1.  **NOT a Foundation Model:** gibbrn does not pre-train, post-train, or fine-tune models. It operates with frozen, off-the-shelf APIs and open weights. (Aspire-style weight-level self-evolution is studied as *evaluation subject matter* for objective integrity in RQ8, not as a gibbrn training capability.)
2.  **NOT an AGI or Recursive Self-Improvement System:** gibbrn rejects unconstrained cognitive self-modification loops.
3.  **NOT an Agent Framework Replacement:** gibbrn does not replace LangGraph, AutoGen, CrewAI, or OpenHands. It sits alongside or underneath them as an out-of-process control plane.
4.  **NOT a Distributed Workflow Engine:** gibbrn does not build a new Temporal, Cadence, or DBOS. It delegates workflow scheduling and activity retries to established systems.
5.  **NOT a Vector Database:** gibbrn does not compete with Pinecone, Qdrant, or Chroma. Semantic vector indexing is an orthogonal retrieval tool.
6.  **NOT an Enterprise IAM Replacement:** gibbrn does not replace Okta or AWS IAM. It enforces transient, per-step capability scopes and ephemeral execution leases.
7.  **NOT a Generic Prompt Filter:** gibbrn does not rely on heuristic regex or probabilistic LLM-as-a-judge classifiers to detect attacks; it uses deterministic schema and kernel-level capability containment. (Semantic evaluators may supply *evidence*; they hold no unilateral commit authority.)
8.  **NOT a Machine-Society Platform:** gibbrn does not build autonomous machine societies, political institutions, or general machine culture. Shared-state governance (RQ11) studies membership, provenance, sanctions, and change rules for persistent multi-agent deployments — narrow systems governance, not a society thesis.
9.  **NOT an AGI Operating System; NOT a Foundation Model; NOT a Generic Agent Framework.** (Restated for diligence clarity per V4 company thesis.)

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
*   [9] K. Zhu, Z. Liu, B. Li, M. Tian, Y. Yang, J. Zhang, et al., "Where LLM Agents Fail and How They Can Learn From Failures," *arXiv preprint arXiv:2509.25370*, 2025. Benchmark dataset: AgentErrorBench (annotated failure trajectories across ALFWorld, GAIA, and WebShop; ulab-uiuc/AgentDebug).
*   [10] C. S. Xia et al., "Agentless: Demystifying LLM-based Software Engineering," *arXiv preprint arXiv:2407.01489*, 2024.
