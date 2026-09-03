# 10 — 1517 Fund Investor Technical Brief

**Project Name:** GIBBRN  
**Document Track:** Executive Investor Diligence & Systems Brief  
**Date:** September 2026  
**Target:** 1517 Fund Investment Committee  
**Format:** Direct 12-Question Technical Diligence Response  

---

### 1. What is gibbrn?
**gibbrn is an Agent State Integrity Layer for long-lived autonomous agents.** Technically, it is a framework-neutral persistent control plane designed to preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous systems operate, accumulate experience, and change over time.

---

### 2. What changed after the latest research cycle?
Previously, the project was framed broadly as a *Persistent Adaptive Agent Runtime*. The September 2026 research cycle revealed that "runtime" is the wrong abstraction: battle-tested workflow engines (like Temporal) already solve basic process execution, while building another agent framework (competing with LangGraph or AutoGen) creates unnecessary developer friction. 

The thesis was refocused exclusively on **State Integrity**: separating probabilistic cognitive scratchpads from canonical, deterministic, and authoritative system state. We do not build an execution engine; we build the control plane that makes any agent framework enterprise-safe and mathematically dependable.

---

### 3. What is the central technical insight?
**The foundation model must not be a root of trust for its own state, authority, or memory.** 
The modern AI stack is separating into distinct computational layers:
*   *Foundation Model ≈ Cognitive Processor* (probabilistic, non-deterministic, stateless).
*   *Active Context Window ≈ Transient Working Cache* (lossy, prone to hallucination).
*   *gibbrn ≈ Persistent Control Plane & State Spine* (canonical, deterministic, append-only, externally enforced).

By separating **mutable cognition** from **authoritative control state**, we prevent models from hallucinating their own permissions, poisoning their own long-term memory, or compounding minor errors into catastrophic failures.

---

### 4. Why does the problem become worse as agents become more autonomous?
As agents transition from single-turn chat to multi-day, deep-dependency operations ($d \ge 30$ steps):
1.  **Mathematical Compounding Failure:** If an agent has a 97% per-step accuracy, a 30-step trajectory succeeds only $0.97^{30} \approx 40\%$ of the time. Without external checkpoints, single failures cause complete aborts.
2.  **Endogenous Authority Laundering:** Long-running models reflect on their own context, mistakenly reinterpreting natural language constraints as elevated permissions (e.g., hallucinating that a spending limit was raised).
3.  **Temporal Decoupling of Attacks:** Memory poisoning (OWASP ASI06) allows attackers to inject malicious guidance via web scraping today that triggers privileged actions weeks later, completely bypassing session-scoped guardrails.

---

### 5. What is technically novel or potentially novel?
*   **The Four-Tier State Model:** A formal mathematical separation between Cognitive ($\mathcal{S}_{\text{cog}}$), Operational ($\mathcal{S}_{\text{ops}}$), Authoritative ($\mathcal{S}_{\text{auth}}$), and Runtime/Safety ($\mathcal{S}_{\text{safe}}$) state.
*   **The Deterministic Authority Reducer:** Permissions and budgets managed via pure mathematical reducers outside the model prompt, making authority laundering physically impossible.
*   **Grounded Experience Admission:** A multi-stage pipeline where newly discovered skills must pass isolated micro-sandbox regression testing before promotion to permanent memory.
*   **Bounded Causal Replay:** Merkle-DAG event recording that allows deterministic replay of past external tool receipts up to failure step $k$, invoking live LLM inference only for novel steps.

---

### 6. What already exists (and what gibbrn deliberately does NOT build)?
gibbrn **does not** reinvent storage, consensus, or workflow scheduling:
*   *Relational & Append-Only Storage:* Delegated to PostgreSQL and SQLite WAL.
*   *Long-Running Timers & Schedulers:* Delegated to Temporal / DBOS.
*   *Log Telemetry:* Delegated to DuckDB, Parquet, and OpenTelemetry.
*   *Process Sandboxing:* Delegated to Docker, gVisor, and Linux cgroups.
*   *Versioned Artifacts:* Delegated to Git and SHA-256 Content-Addressable Storage.

gibbrn builds **only** the missing agent-state semantics, capability gates, admission pipelines, and causal reconstruction algorithms.

---

### 7. What remains unproven?
1.  Whether external checkpointing and replay can double Maximum Dependable Dependency Depth ($\text{MDDD}$) in practice without excessive token overhead.
2.  Whether automated regression validation of candidate skills can run fast enough ($<60\text{s}$) and cheap enough ($<3\times$ base cost) to be commercially viable.
3.  Whether a single framework-neutral state projection can support LangGraph, SWE-agent, and native Python loops with $<25\text{ms}$ intercept latency.

---

### 8. What exactly will be tested over 18 months?
Eight formal, falsifiable research questions (RQ1–RQ8) across 13,200+ benchmark trajectories on SWE-bench Pro, AgentErrorBench, GAIA, and Tau-bench:
*   *RQ1:* State taxonomy validation against corruption.
*   *RQ2:* Merkle event-sourcing vs. OpenTelemetry tracing for failure attribution.
*   *RQ3:* Authority reducer defense against prompt injection privilege escalation.
*   *RQ4:* Experience admission defense against MINJA memory poisoning.
*   *RQ5:* Lifetime Risk Ledger detection of distributed multi-session exfiltration.
*   *RQ6:* Quantifying $\text{MDDD}$ extension curves via checkpointing.
*   *RQ7:* Operational skill accumulation without parameter fine-tuning.
*   *RQ8:* Cross-runtime portability and latency profiling across Claude and Gemini.

---

### 9. What are the M3 / M6 / M9 / M12 / M15 / M18 Checkpoint Gates?
*   **M3 (Foundations):** Low-latency intercept harness. *Gate:* Intercept overhead $\le 30\text{ms}$.
*   **M6 (Flight Recorder):** Causal reconstruction prototype. *Gate:* Root-cause attribution $\ge 80\%$.
*   **M9 (Authority Gate):** Pre-execution capability interceptor. *Gate:* $\text{UER} \le 0.001$, $\text{FDR} \le 2\%$.
*   **M12 (Skill Admission):** Quarantine & regression engine. *Gate:* False-promotion $\le 2\%$, retention $\ge 98\%$.
*   **M15 (Risk & MDDD):** Long-horizon reliability push. *Gate:* $\text{MDDD}_{0.90} \ge 2.0\times$ baseline.
*   **M18 (Thesis Gate):** Cross-runtime validation & pilot deployments. *Gate:* Decision to Proceed to Seed, Pivot to Security Gate, or Dissolve.

---

### 10. What does USD 100k+ fund?
We present three structured funding options aligned with 1517 Fund's pre-seed investment parameters (\$50k–\$1M):
*   **Minimum Viable Plan (\$120,000):** Solo Principal Researcher subsistence (\$54k), core frontier API compute (\$24k), cloud microVMs (\$14.4k), dev hardware/legal (\$8k), 10% contingency (\$15k). Delivers answered RQs and working LangGraph prototype.
*   **Target Research Plan (\$285,000) [RECOMMENDED]:** Principal Researcher (\$90k) + part-time Systems Engineer (\$54k), extensive multi-model benchmark compute (\$48k), dedicated gVisor sandbox cluster (\$28.8k), external red-teaming bounties (\$15k), travel/IP/contingency (\$49.2k). Delivers full multi-runtime control plane with 2 design-partner pilots.
*   **Expanded Plan (\$480,000):** Two full-time systems researchers, formal CREST security audit, multi-tenant bare-metal clusters, 5 production pilots.

---

### 11. What result would make us abandon the thesis?
We will terminate the project, publish our negative findings, and return unspent capital if:
1.  **At M3:** Interception introduces $>100\text{ms}$ latency drag that cannot be engineered away.
2.  **At M9:** Deterministic gates prove incapable of stopping out-of-scope actions without invoking slow, expensive LLM-as-a-judge evaluators.
3.  **At M15:** Checkpoint rollback and state isolation fail to achieve a statistically significant $2.0\times$ improvement in $\text{MDDD}$.

---

### 12. What would constitute a breakthrough result?
A breakthrough result occurs if gibbrn demonstrates that **an agent utilizing frozen, off-the-shelf foundation models can reliably execute 50+ interdependent, mutating tool steps ($\text{MDDD}_{0.90} \ge 50$) with zero unauthorized state mutations and zero catastrophic skill poisoning.**

This would prove that the primary barrier to long-lived autonomous AI is not model intelligence, but **systems architecture**—establishing gibbrn as the foundational control plane for the autonomous enterprise.

---

> **Agents can change. Their integrity must persist.**
