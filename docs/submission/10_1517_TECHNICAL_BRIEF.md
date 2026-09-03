# 10 — 1517 Fund Investor Technical Brief (Submission)

**Project Name:** GIBBRN  
**Document Track:** Executive Investor Diligence & Systems Brief  
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Target:** 1517 Fund Investment Committee  
**Standard:** 12 Direct Diligence Responses (Post-Adversarial Diligence)  

---

### 1. What is gibbrn?
**gibbrn investigates Agent State Integrity for long-lived autonomous agents.** Technically, it is a proposed framework-neutral persistent control plane designed to preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous systems operate, accumulate experience, and change over time.

---

### 2. What changed after the latest research cycle and adversarial audit?
1.  **Separation of Thesis from Initial Wedge:** Broad "Agent Operating System" claims were abandoned in favor of a sharp, high-value wedge: the **Deterministic Effect Gate**.
2.  **Subsystem Consolidation (5 $\to$ 3 Engines):** Merged redundant components into three physical engines: the *Causal State Spine*, the *Deterministic Effect Gate*, and the *Experience Admission Engine*.
3.  **Mathematical Reformulation:** Replaced the naive geometric error compounding formula ($P = p^d$) with formal **discrete survival analysis hazard rate modeling** ($S(k) = \prod (1 - h(i))$).
4.  **Academic Remediation:** Audited and corrected citations; primary citations verified against source repositories. Key corrections include: Dong et al. (MINJA) classified as NeurIPS 2025 (not 2024); AgentErrorBench attribution corrected to Zhu et al. (2025).
5.  **Capital Ask Clarification:** Established approximately **\$285,000** as the primary pre-seed ask for an 18-month founder-led systems research program, including budget capacity for part-time research engineering support.

---

### 3. What is the narrow initial technical wedge?
**Deterministic Authority and Effect Integrity.** 
We are researching how an autonomous agent can change its probabilistic cognitive reasoning without silently changing what it is authorized to do in the external world. The wedge is an out-of-process reference monitor that intercepts proposed tool mutations, validating them against external cryptographic capabilities and containing execution inside ephemeral gVisor micro-sandboxes.

---

### 4. What empirical evidence supports the problem?
*   **Harness Architecture Sensitivity:** Yang et al. (NeurIPS 2024; SWE-agent) and Xia et al. (2024; Agentless) demonstrate that different agentic scaffolding architectures yield substantially different resolution rates on the same coding benchmark — differences on the order of tens of percentage points have been observed across the SWE-bench literature. These comparisons are not fully controlled experiments (scaffolding, prompting, and model selection co-vary), but the scale of sensitivity motivates gibbrn's investigation of harness-level state design as a significant variable.
*   **Reflection Instability:** Jie Huang et al. (ICLR 2024) and Valmeekam et al. (NeurIPS 2023) demonstrate that model self-reflection is non-monotonic and prone to ungrounded confirmation bias without external symbolic verification.
*   **Memory Poisoning:** S. Dong et al. (NeurIPS 2025; arXiv:2503.03704) demonstrate that MINJA memory injection attacks achieve $>85\%$ success across evaluated configurations (EHR, e-commerce, and QA agent settings), enabling query-only persistence of malicious instructions across sessions without requiring direct memory access.

---

### 5. What remains unproven?
1.  Whether external checkpointing and rollback can achieve a statistically significant doubling of trajectory survival depth ($\text{MDDD}_{0.90} \ge 2.0\times$) on non-deterministic tasks.
2.  Whether automated regression testing for candidate skills can run fast enough ($<60\text{s}$) and cheap enough ($<3\times$ task cost) to be viable in continuous operation.
3.  Whether enterprise developers will adopt an out-of-process control daemon over ad-hoc in-process scripts.

---

### 6. Why might existing stacks be insufficient?
*   **Temporal / DBOS:** Temporal's documented durability model guarantees workflow replay and activity retries for deterministic code, but does not provide agent-specific semantic validation of why a model proposed a given side effect or whether its in-context authority was laundered.
*   **Mem0 / Letta:** Focus on semantic similarity retrieval; public documentation reviewed does not describe native support for regression testing, sandboxed validation, or provenance isolation before memory promotion, leaving direct vectors for MINJA-style memory poisoning.
*   **Lakera Guard / Guardrails:** Rely on probabilistic natural-language classifiers to scan prompts and outputs, operating at the text inspection layer rather than enforcing deterministic kernel sandboxing or state constraints.

---

### 7. Why might existing stacks actually be sufficient (The Counter-Case)?
If enterprise computing rejects open-ended autonomous agent loops entirely and converges on **rigid, deterministic DAGs (the Agentless paradigm)** where models are called only for narrow, single-step extractions, static pipelines will suffice. gibbrn exists to test whether there is a valuable task territory requiring dynamic exploratory branching that static pipelines cannot solve.

---

### 8. What exactly will be tested over 18 months?
Five causally chained research questions across 13,200 benchmark trajectories:
*   *Core RQ1 (State Classification):* Testing whether 4-tier typed schemas reduce state corruption by $\ge 80\%$ on SWE-bench Lite.
*   *Core RQ2 (Causal Reconstruction):* Testing whether Merkle DAG event trees achieve $\ge 80\%$ root-cause failure attribution on AgentErrorBench (Zhu et al., arXiv:2509.25370, 2025).
*   *Core RQ3 (Authority Integrity):* Testing whether the Deterministic Effect Gate maintains $\text{UER} \le 0.001$ across 1,000 prompt injection attacks.
*   *Core RQ4 (Experience Admission):* Testing whether micro-sandbox regression testing maintains $\ge 98\%$ retention under MINJA poisoning.
*   *Core RQ5 (Trajectory Survival):* Testing whether checkpoint rollback doubles $\text{MDDD}_{0.90}$ over unmanaged baselines on GAIA Level 3.

---

### 9. What are the six research checkpoint gates?
*   **Gate M3 (Foundations):** Interception overhead $\le 30\text{ms}$; state exceptions reduced by $\ge 80\%$.
*   **Gate M6 (Causal Spine):** Causal failure attribution rate $\text{CRR} \ge 80\%$.
*   **Gate M9 (Effect Gate - Main Wedge):** Unauthorized-Effect Rate $\text{UER} \le 0.001$; false denials $\le 2.0\%$; latency $\le 15\text{ms}$.
*   **Gate M12 (Experience Admission):** False-Promotion Rate $\text{FPR} \le 0.02$; downstream retention $\ge 98\%$.
*   **Gate M15 (Survival - Company Thesis Gate):** $\text{MDDD}_{0.90} \ge 2.0\times$ baseline ($p < 0.01$ Log-Rank test).
*   **Gate M18 (Final Thesis Gate):** Cross-model replication, target of up to 2 external pilot evaluations (contingent on partner availability and workflow match), and formal proceed/pivot/stop verdict.

---

### 10. What does the requested capital buy?
**USD 285,000 over 18 months** (Budget Assumption as of September 2026) funds:
*   Full-time founder subsistence for the Principal Systems Researcher (\$90k).
*   Budget allocation for a part-time Research Systems Engineer / contractor (contingent on funding, \$54k).
*   13,200 benchmark trajectories across frontier models (\$48k API compute; sensitive to token rate shifts).
*   Dedicated bare-metal gVisor cloud microVM clusters (\$28.8k).
*   External adversarial red-teaming bounties (\$15k).
*   Tooling, legal formation, trademark, and conference dissemination (\$21.2k).
*   A 10% contingency reserve (\$28k) buffering against token price shocks.

---

### 11. What result kills the thesis?
*   **At M3:** If synchronous proxy interception adds $>50\text{ms}$ latency.
*   **At M9:** If capability tokens and kernel sandboxing fail to stop unauthorized mutating effects ($\text{UER} > 0.001$).
*   **At M15:** If checkpoint rollback fails to double $\text{MDDD}_{0.90}$ with $p < 0.01$.

If Gate M15 fails, **we will stop pursuing the broad company thesis and either wind down the program or pursue only a narrower direction if supported by evidence and investor governance.** We will not pivot to a generic AI wrapper.

---

### 12. What result would justify a subsequent seed round?
A subsequent institutional Seed round would become defensible if gibbrn demonstrates that on tasks requiring exploratory branching:
1.  gibbrn-managed agents achieve a pre-registered, practically meaningful improvement in survival depth and task completion over unmanaged baselines (Gate M15 target: $\text{MDDD}_{0.90} \ge 2.0\times$ baseline, $p < 0.01$).
2.  The Effect Gate maintains an observed $\text{UER} = 0$ across $N=1,000$ red-team attacks (zero unauthorized mutating executions observed; one-sided 95% Clopper-Pearson upper bound $< 0.003$).
3.  External deployment evaluations confirm integration with $<20\text{ms}$ latency overhead and measurable failure-recovery savings.

---

> **Agents can change. Their integrity must persist.**
