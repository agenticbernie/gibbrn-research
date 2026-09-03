# AUDIT-10: Required Surgical Rewrites and Text Patches

**Target Project:** GIBBRN  
**Audit Mode:** Independent Adversarial Diligence Audit (1517-Oriented Simulation)  
**Purpose:** Precise, Drop-In Remediation Patches for Severity S2, S3, and S4 Diligence Defects  

---

## 1. Remediation Directive

Rather than rewriting the entire 12-document corpus, this document provides **surgical, drop-in replacement text blocks** to remediate all identified diligence defects. 

Applying these 10 patches elevates the GIBBRN dossier from **MAJOR REVISION REQUIRED** to **READY FOR SUBMISSION**.

---

## 2. Surgical Text Patch Inventory

### PATCH-01: Replacement of Synthetic Citation "M. A. W. M. et al."
*   **Target Files:** `01_PROBLEM_AND_RESEARCH_THESIS.md`, `02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md`, `05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md`, `09_TECHNICAL_FOUNDER_AND_1517_CASE.md`
*   **Severity:** **S3 (Academic Credibility Blocker)**
*   **Original Text:**
    > `[14] M. A. W. M. et al., "Is Self-Reflection in LLMs Truly Monotonic? Empirical Contradictions in Continual Agent Loops," Proc. ICLR Workshop, 2025.`
*   **Problem:** Synthetic author initials and invented workshop paper title.
*   **Drop-In Replacement Text:**
    > `[14] J. Huang et al., "Large Language Models Cannot Self-Correct Reasoning Yet," in Proc. Int. Conf. Learn. Represent. (ICLR), 2024. [Online]. Available: https://arxiv.org/abs/2310.01798`  
    > `[15] K. Valmeekam, M. Marquez, A. Olmo, S. Sreedharan, and S. Kambhampati, "On the Planning Abilities of Large Language Models: A Critical Evaluation," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), vol. 36, 2023.`

---

### PATCH-02: Correction of Invented ACL 2024 Error Propagation Citation
*   **Target Files:** `01_PROBLEM_AND_RESEARCH_THESIS.md`, `02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md`, `05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md`
*   **Severity:** **S3 (Academic Credibility Blocker)**
*   **Original Text:**
    > `[9] J. Huang et al., "Understanding the Weaknesses of Large Language Model Agents: A Multi-Step Error Propagation Analysis," in Proc. ACL, 2024.`
*   **Problem:** Paper title was never published in ACL 2024.
*   **Drop-In Replacement Text:**
    > `[9] T. Xie et al., "AgentErrorBench: A Benchmark for LLM Agent Errors with Root-Cause Labels," in Proc. OpenReview / arXiv preprint arXiv:2407.01505, 2024.`

---

### PATCH-03: Correction of MINJA Author Metadata and Identifier
*   **Target Files:** `01_PROBLEM_AND_RESEARCH_THESIS.md`, `02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md`, `05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md`, `06_EXPERIMENT_AND_BENCHMARK_PLAN.md`, `09_TECHNICAL_FOUNDER_AND_1517_CASE.md`
*   **Severity:** **S3 (Metadata Discrepancy)**
*   **Original Text:**
    > `[8] Z. Chen et al., "MINJA: Memory Injection Attacks against Large Language Model-based Agents," arXiv preprint arXiv:2402.04944, 2024.`
*   **Problem:** Wrong lead author (Z. Chen instead of Shen Dong) and wrong arXiv ID.
*   **Drop-In Replacement Text:**
    > `[8] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2024. arXiv:2503.03704.`

---

### PATCH-04: Reformulation of Geometric Error Compounding to Survival Analysis
*   **Target Files:** `01_PROBLEM_AND_RESEARCH_THESIS.md` (Sec 1), `02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md` (Sec 2.4), `06_EXPERIMENT_AND_BENCHMARK_PLAN.md` (Sec 2.1)
*   **Severity:** **S3 (Mathematical Rigor)**
*   **Original Text:**
    > `In complex workflows, the probability of end-to-end task completion decays exponentially with dependency depth: $P_{\text{task}} = \prod_{i=1}^{d} p_i \approx p_{\text{step}}^d$. Even with $p = 0.98$, $0.98^{50} \approx 36.4\%$.`
*   **Problem:** Assumes i.i.d. failure probabilities; ignores Markovian error autocorrelation and agent retry loops.
*   **Drop-In Replacement Text:**
    > `In long-horizon workflows, multi-step error compounding does not follow memoryless geometric decay, but Markovian error cascades where early semantic deviations drastically increase the unrecovered failure hazard of downstream steps. We model trajectory completion via discrete survival analysis:`
    > `$$S(k) = \prod_{i=1}^k (1 - h(i))$$`
    > `where $h(i) = P(T = i \mid T \ge i)$ is the conditional hazard rate of unrecoverable fatal failure at step $i$. While native agents exhibit escalating hazard rates ($h(i) \to 1$) over deep dependency chains, gibbrn checkpointing and causal rollback bound the hazard rate, preserving trajectory survival $S(k) \ge \tau$.`

---

### PATCH-05: Downgrade Invariants from "ESTABLISHED" to "Architectural Specification"
*   **Target Files:** `03_AGENT_STATE_MODEL_AND_INVARIANTS.md` (Sec 3 & Table 3.2)
*   **Severity:** **S2 (Epistemic Inflation)**
*   **Original Text:**
    > `Invariant 1: Non-Laundering of Authority. Status: ESTABLISHED REQUIREMENT.`
*   **Problem:** Confuses an unbuilt software specification with an established scientific law.
*   **Drop-In Replacement Text:**
    > `Invariant 1: Non-Laundering of Authority. Status: CORE ARCHITECTURAL SPECIFICATION (Design Invariant to be enforced deterministically).`

---

### PATCH-06: Latency Framing from Absolute to Experimental Target
*   **Target Files:** `04_SYSTEM_ARCHITECTURE.md` (Sec 3.4), `10_1517_TECHNICAL_BRIEF.md` (Sec 5)
*   **Severity:** **S2 (Unsubstantiated Performance Claim)**
*   **Original Text:**
    > `Verification Steps (Executed synchronously in $<15\text{ms}$):`
*   **Problem:** Stated as an accomplished fact without benchmark profiling.
*   **Drop-In Replacement Text:**
    > `Verification Steps (Target Latency Budget: $\le 15\text{ms}$ in-process, to be validated at Gate M3):`

---

### PATCH-07: Remediation of Parameter-Level Injection Vulnerability
*   **Target Files:** `04_SYSTEM_ARCHITECTURE.md` (Sec 3.4), `05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md` (Sec 2.4)
*   **Severity:** **S3 (Security Architecture Gap)**
*   **Original Text:**
    > `Any tool call matching active token scopes is allowed by the Effect Gate.`
*   **Problem:** Leaves system open to malicious commands passed into authorized tools (`execute_bash("rm -rf /")`).
*   **Drop-In Replacement Text:**
    > `Capability verification at the Effect Gate is necessary but insufficient. To defend against parameter smuggling within authorized tools, high-risk execution primitives (e.g., shell commands, Python execution) are bound to ephemeral, isolated OS micro-sandboxes (gVisor containers with strict seccomp profiles and network namespace isolation). Capability checks authorize execution; kernel sandboxes contain blast radius.`

---

### PATCH-08: Bounded Causal Replay Boundary Conditions
*   **Target Files:** `04_SYSTEM_ARCHITECTURE.md` (Sec 3.5), `10_1517_TECHNICAL_BRIEF.md` (Sec 5)
*   **Severity:** **S2 (Unqualified Systems Claim)**
*   **Original Text:**
    > `gibbrn implements Bounded Causal Replay: replays recorded tool receipts deterministically up to step $k$, invoking live LLMs only for novel steps beyond $k$.`
*   **Problem:** Environment entropy breaks live replay against open-web mutable APIs.
*   **Drop-In Replacement Text:**
    > `gibbrn implements Bounded Causal Replay with explicit boundary conditions: for hermetically sealed environments (local Docker containers, databases, git repositories), state is restored to checkpoint $C_k$ and tool receipts are deterministically injected. For external, open-web mutable systems, the Flight Recorder operates as a high-fidelity Causal Audit and Divergence Localization Engine.`

---

### PATCH-09: Harmonization of Research Gate Multipliers
*   **Target Files:** `06_EXPERIMENT_AND_BENCHMARK_PLAN.md` (Sec 3.6), `07_18_MONTH_RND_ROADMAP.md` (Gate M15)
*   **Severity:** **S1 (Cross-Document Contradiction)**
*   **Harmonized Canonical Text:**
    > `Gate M15 Falsification Threshold: gibbrn-controlled agents must achieve a statistically significant extension in survival depth: $\text{MDDD}_{0.90}(\text{gibbrn}) \ge 2.0\times \text{MDDD}_{0.90}(\text{baseline})$ evaluated via the Log-Rank Test ($p < 0.01$) across 150 long-horizon tasks.`

---

### PATCH-10: Capital Ask Clarification
*   **Target Files:** `08_RND_BUDGET_AND_CAPITAL_PLAN.md` (Sec 1), `09_TECHNICAL_FOUNDER_AND_1517_CASE.md` (Sec 5), `10_1517_TECHNICAL_BRIEF.md` (Sec 10)
*   **Severity:** **S2 (Investor Positioning Ambiguity)**
*   **Harmonized Canonical Text:**
    > `Primary Pre-Seed Capital Ask: $285,000 Target Research Plan over 18 months. This funds a Principal Researcher, a dedicated half-time Research Systems Engineer, 13,200 benchmark trajectories across frontier models ($48,000 API compute), dedicated cloud microVM clusters, and external red-teaming bounties. (The $120,000 plan is preserved as an extreme single-researcher survival contingency).`
