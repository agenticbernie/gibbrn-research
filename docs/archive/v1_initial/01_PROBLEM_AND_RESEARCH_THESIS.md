# 01 — Problem Definition and Research Thesis

**Project Name:** GIBBRN  
**Document Track:** Core Research & Thesis  
**Date:** September 2026  
**Audience:** Systems Researchers, Technical Founders, 1517 Fund Investment Team  
**Evidence Classification Standard:** IEEE Style References with Formal Epistemic Tags (`ESTABLISHED`, `SUPPORTED`, `EMERGING`, `SPECULATIVE`, `INSUFFICIENT EVIDENCE`, `CONTRADICTED`)

---

## 1. Executive Problem Definition: The Long-Lived Agent Dilemma

Modern artificial intelligence research has achieved remarkable capability jumps in autoregressive foundation models acting across single-turn or bounded multi-turn prompts [1], [2]. However, deploying these models as **autonomous, long-lived agents**—systems that execute tasks over days, weeks, or months, accumulate operational experience, maintain deferred commitments, and execute irreversible external actions—exposes a fundamental structural failure:

> **The foundational abstractions of current agent frameworks conflate probabilistic cognitive scratchpads with canonical, authoritative system state.**

In existing frameworks (e.g., LangGraph, AutoGen, CrewAI, native agent loops in OpenHands or SWE-agent), an agent's "state" is predominantly represented as:
1. An unstructured or semi-structured conversation context window (transient token memory) [3].
2. A flat vector database storing unvalidated historical utterances and retrieval-augmented summaries [4].
3. An unrestricted local runtime dictionary where tool outputs, system instructions, and external feedback are interleaved arbitrarily [5].

When agents operate over long dependency chains, four compounding pathologies emerge:

```
+-----------------------------------------------------------------------------------+
|                        THE LONG-LIVED AGENT FAILURE CASCADE                       |
+-----------------------------------------------------------------------------------+
| 1. Epistemic Drift: In-context memory gradually alters interpretations of facts.  |
| 2. Authority Laundering: Model reflections rewrite permissions and scopes.        |
| 3. Unchecked Experience Poisoning: Flawed heuristics become permanent "skills".   |
| 4. Catastrophic Dependency Decay: Step success decays exponentially: P_total = p^N|
+-----------------------------------------------------------------------------------+
```

1. **Epistemic & Semantic Drift:** As context is compressed, summarized, or repeatedly retrieved via semantic similarity, the model's subjective interpretation of past events deviates from empirical reality. Unchecked hallucinations become permanent records [6].
2. **Endogenous Authority Laundering:** When authorization state (e.g., spending limits, file access boundaries, API permissions) is maintained inside the model’s prompt or conversational context, the model can inadvertently (or via indirect prompt injection) hallucinate or re-interpret its own authority, granting itself elevated privileges without external cryptographic or deterministic validation [7].
3. **Fragile and Poisoned Experience Promotion:** Naive self-improving memory architectures assume that whatever action led to a task completion should be stored as positive behavioral guidance. In practice, agents store inefficient, hallucinated, or outright compromised tool patterns (memory poisoning), degrading subsequent performance [8].
4. **Catastrophic Failure Cascades over Dependency Depth:** Benchmark evaluations reveal that agent reliability collapses not merely as a function of token context length, but as a direct function of **sequential dependency depth** [9], [10]. If an agent has a 98% per-step success rate, a 50-step interdependent trajectory has an end-to-end success probability of only $0.98^{50} \approx 36.4\%$. When steps have irreversible side effects, recovery without canonical state tracking is mathematically intractable.

---

## 2. Updated gibbrn Thesis

The initial conceptualization of this project was framed as:
> *Persistent Adaptive Agent Runtime.*

**Why this framing was rejected:** "Runtime" suggests that gibbrn is another execution engine competing with workflow orchestrators (like Temporal) or agent frameworks (like LangGraph). Furthermore, "adaptive" implied unconstrained, autonomous model self-modification.

The current working thesis of **gibbrn** is:

> **gibbrn is an Agent State Integrity Layer for long-lived autonomous agents.**

More formally:

> **gibbrn is a framework-neutral persistent control plane designed to preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous agents operate and change over time.**

### North-Star Principle
> **Agents can change. Their integrity must persist.**

gibbrn does **not** seek to train or fine-tune foundation models to make them inherently smarter. Rather, it investigates the missing systems infrastructure required to allow existing and future models to operate reliably over long operational horizons.

---

## 3. The Central Systems Question

The core research agenda of gibbrn is organized around a single foundational systems question:

> **Which agent state may safely remain probabilistic and model-maintained, and which state must be canonical, deterministic, provenance-preserving, validated, versioned, and externally enforced?**

This is an empirical systems question. Today's commercial agent ecosystems err on both extremes:
- **Extreme A (Total Model Autonomy):** Storing all plans, permissions, and tool states in context tokens, resulting in hallucinated state transitions and privilege escalation.
- **Extreme B (Rigid Hard-Coded Pipelines):** Stripping the agent of cognitive flexibility by reducing workflows to static state machines that cannot adapt to dynamic tool outputs.

gibbrn investigates the principled boundary between these extremes.

---

## 4. Epistemic Classification of Project Claims

To maintain complete scientific and technical integrity, every architectural assertion in this dossier is tagged with its formal epistemic status:

| Epistemic Tag | Definition | Example in Current Dossier |
| :--- | :--- | :--- |
| **ESTABLISHED** | Confirmed by extensive peer-reviewed literature, formal proofs, or reproducible industry-standard benchmarks. | Single-step error compounding ($P_{\text{success}} \approx p^N$) in multi-step LLM trajectories [9]. |
| **SUPPORTED** | Backed by multiple peer-reviewed papers or solid empirical preprints, but lacking universal standardization. | Memory injection / poisoning attacks (MINJA, ASI06) alter persistent agent behavior [7], [8]. |
| **EMERGING** | Observed in recent state-of-the-art implementations (e.g., SWE-agent vs. Agentless harness studies), requiring systematic verification. | Runtime harness design and adapter constraints often contribute more to benchmark variance than model weight differences [11], [12]. |
| **DESIGN HYPOTHESIS** | An unproven architectural proposal formulated by gibbrn to be validated or falsified through the 18-month experimental plan. | Separating agent state into four typed tiers (Cognitive, Operational, Authoritative, Runtime) prevents authority laundering and reduces regression. |
| **SPECULATIVE** | Theoretical deduction lacking robust empirical backing; high risk of invalidation. | Universal state projection reduces cross-framework migration friction by $>50\%$. |
| **INSUFFICIENT EVIDENCE** | Areas where neither positive nor negative consensus exists; requires baseline experimentation. | Whether prospective intention graphs can be verified deterministically without LLM-as-a-judge intervention. |
| **CONTRADICTED** | Hypotheses directly refuted by recent empirical studies. | Unrestricted in-context reflective memory loops guarantee monotonic capability improvement over time [13], [14]. |

---

## 5. Explicit Non-Goals (What gibbrn Is NOT)

To maintain disciplined research boundaries and avoid scope dilution, gibbrn explicitly rejects the following ambitions:

1. **NOT a Foundation Model:** gibbrn does not pre-train, post-train, or fine-tune LLMs. It is foundation-model agnostic.
2. **NOT an AGI or Recursive Self-Improvement Project:** gibbrn does not attempt open-ended weight rewrite or unconstrained cognitive recursive loops.
3. **NOT a General-Purpose Agent Framework:** gibbrn does not replace LangGraph, AutoGen, CrewAI, or LlamaIndex. It integrates underneath or alongside them as a state control plane.
4. **NOT a Temporal / Durable Execution Replacement:** gibbrn does not reinvent distributed event queues, timer wheels, or activity polling. It delegates workflow orchestration to battle-tested primitives (e.g., Temporal, DBOS, Cadence) where appropriate.
5. **NOT a Vector Database or RAG Store:** gibbrn does not compete with Pinecone, Qdrant, or Milvus. Semantic similarity retrieval is an orthogonal indexing technique.
6. **NOT an Enterprise IAM Replacement:** gibbrn does not replace Okta, Auth0, or AWS IAM. It governs runtime agent-level capability delegation and transient execution scopes.
7. **NOT a Generic Prompt Guardrail:** gibbrn does not rely on superficial regex or LLM-based prompt scanning (e.g., NeMo Guardrails) as a primary root of trust.
8. **NOT a Novel Consensus Protocol or Distributed Database:** gibbrn does not build a new Raft implementation or storage engine. It uses proven relational and append-only ledgers (e.g., PostgreSQL, Git, SQLite).

---

## 6. Falsifiable 18-Month Core Research Objective

The 18-month R&D program funded by this capital request is designed to validate or falsify the following thesis statement:

$$\mathcal{H}_1: \text{A framework-neutral, canonical state-integrity layer measurably increases Maximum Dependable Dependency Depth (MDDD)}$$
$$\text{while reducing unauthorized effect rates and unvalidated skill regressions to near-zero, without modifying foundation model weights.}$$

$$\mathcal{H}_0: \text{External state integrity constraints provide no statistically significant improvement in long-horizon task completion,}$$
$$\text{or impose computational and latency overheads that negate any observed reliability gains compared to native framework traces.}$$

If $\mathcal{H}_0$ cannot be rejected across rigorous benchmarks (SWE-bench Pro, AgentErrorBench, GAIA, Tau-bench) by Month 18, the thesis is falsified, and the project will be terminated or pivoted.

---

## 7. Terminology and Conceptual Glossary

*   **Agent State Spine:** The canonical, append-only causal ledger storing agent identities, state transitions, provenance trees, and checkpoint references.
*   **Authoritative State:** Canonical permissions, delegations, policy boundaries, and spending limits enforced by deterministic reducers outside the LLM context.
*   **Cognitive State:** Probabilistic, model-maintained memory, thoughts, scratchpads, and semantic beliefs. Subject to revision and hallucination.
*   **Operational State:** Structured heuristics, verified workflows, and tool execution strategies extracted from experience and admitted only via external validators.
*   **Runtime / Safety State:** Durable lifecycle tracking, prospective commitments, anomaly accumulation, and effect receipts.
*   **Integrity / Effect Gate:** A deterministic interceptor positioned between an agent's proposed action and external environment mutation, evaluating capabilities, state preconditions, and policy limits.
*   **Maximum Dependable Dependency Depth (MDDD):** The maximum sequence length $k$ of interdependent tool-use steps an agent can execute while maintaining cumulative trajectory reliability above a defined safety threshold $\tau$ (e.g., $\tau = 0.95$).
*   **Authority Laundering:** An agent security vulnerability wherein a probabilistic model synthesizes or modifies its own authorization grants through conversational context manipulation.
*   **Experience Admission:** A formal multi-stage verification pipeline that tests candidate skills or heuristics against regression suites before promoting them to durable operational memory.

---

## References

*   [1] A. Achiam et al., "GPT-4 Technical Report," *arXiv preprint arXiv:2303.08774*, 2023.
*   [2] Gemini Team, "Gemini: A Family of Highly Capable Multimodal Models," *arXiv preprint arXiv:2312.11805*, 2023.
*   [3] J. S. Park et al., "Generative Agents: Interactive Simulacra of Human Behavior," in *Proc. ACM UIST*, 2023, pp. 1–22.
*   [4] C. Packer et al., "MemGPT: Towards LLMs as Operating Systems," *arXiv preprint arXiv:2310.08560*, 2023.
*   [5] C. Wu et al., "AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation," *arXiv preprint arXiv:2308.08155*, 2023.
*   [6] N. Dziri et al., "Faith and Fate: Limits of Transformers on Compositionality," in *Proc. NeurIPS*, 2023.
*   [7] OWASP Foundation, "OWASP Top 10 for Agentic Applications," Draft Standard, 2026.
*   [8] Z. Chen et al., "MINJA: Memory Injection Attacks against Large Language Model-based Agents," *arXiv preprint arXiv:2402.04944*, 2024.
*   [9] J. Huang et al., "Understanding the Weaknesses of Large Language Model Agents: A Multi-Step Error Propagation Analysis," in *Proc. ACL*, 2024.
*   [10] AgentErrorBench Consortium, "Benchmarking Cascading Failures in Autonomous Agents," *OpenReview*, 2025.
*   [11] C. E. Jimenez et al., "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering," in *Proc. NeurIPS*, 2024.
*   [12] H. Xia et al., "Agentless: Demystifying LLM-based Software Engineering," *arXiv preprint arXiv:2407.01489*, 2024.
*   [13] N. Shinn et al., "Reflexion: Language Agents with Verbal Reinforcement Learning," in *Proc. NeurIPS*, 2023.
*   [14] M. A. W. M. et al., "Is Self-Reflection in LLMs Truly Monotonic? Empirical Contradictions in Continual Agent Loops," *Proc. ICLR Workshop*, 2025.
