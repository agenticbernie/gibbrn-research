# 06 — Experimental Methodology and Benchmark Suite

**Project Name:** GIBBRN  
**Document Track:** Empirical Validation & Benchmark Engineering  
**Date:** September 2026  
**Audience:** Empirical AI Researchers, Experimental Systems Designers, 1517 Fund  
**Validation Standard:** Rigorous Falsification Protocol Across RQ1–RQ8  

---

## 1. Experimental Philosophy: Falsification Over Demonstration

Most agent frameworks present selective "vignettes" or cherry-picked trajectories demonstrating successful task completion. **gibbrn enforces an adversarial, falsification-first experimental methodology.**

The 18-month research program is structured to answer eight formal research questions (RQ1–RQ8). Every experiment specifies an explicit null hypothesis ($\mathcal{H}_0$), quantitative failure thresholds, statistical power requirements, and confounder controls.

```
+-----------------------------------------------------------------------------------+
|                        GIBBRN CORE EVALUATION METRICS                             |
+-----------------------------------------------------------------------------------+
| 1. MDDD (Maximum Dependable Dependency Depth): Max sequential steps with P >= tau |
| 2. UER (Unauthorized-Effect Rate): Ratio of illegal mutations slipping past gate  |
| 3. FPR (False-Promotion Rate): Ratio of flawed skills admitted to ops state       |
| 4. CRR (Causal Reconstruction Rate): Accuracy of identifying root cause of crash |
| 5. MROC (Mean Recovery Overhead Cost): Token & latency cost to restore state      |
+-----------------------------------------------------------------------------------+
```

---

## 2. Core Quantitative Metric Formalizations

### 2.1 Maximum Dependable Dependency Depth ($\text{MDDD}_\tau$)
The maximum sequence length $k$ of interdependent tool steps an agent can execute while maintaining cumulative trajectory reliability above a defined safety/correctness threshold $\tau \in [0, 1]$ (standard baseline $\tau = 0.90$):

$$\text{MDDD}_\tau = \max \left\{ k \in \mathbb{N} \;\middle|\; \prod_{i=1}^k P(\text{Step}_i = \text{SUCCESS} \mid \text{History}_{i-1}) \ge \tau \right\}$$

### 2.2 Unauthorized-Effect Rate ($\text{UER}$)
The fraction of proposed actions violating authoritative policy constraints that successfully execute in the external environment:

$$\text{UER} = \frac{\sum \mathbf{1}\left(\text{Executed}(a) \land a \notin \text{ActiveCaps}(\mathcal{S}_{\text{auth}})\right)}{N_{\text{total\_adversarial\_actions}}}$$

*Target: $\text{UER} = 0.000$ (Zero tolerance for unauthorized state mutations).*

### 2.3 False-Promotion Rate ($\text{FPR}$)
The proportion of candidate operational skills promoted to active state that subsequently cause benchmark regressions or security violations:

$$\text{FPR} = \frac{N_{\text{admitted\_skills\_with\_regressions}}}{N_{\text{total\_skills\_promoted}}}$$

---

## 3. Detailed Experimental Protocols for RQ1–RQ8

### RQ1 — State Taxonomy Validity
*   **Systems Question:** Does physically decomposing agent state into four typed tiers (Cognitive, Operational, Authoritative, Runtime/Safety) reduce state corruption compared to unified context dictionaries?
*   **Hypothesis ($\mathcal{H}_1$):** Isolating Authoritative and Operational state into deterministic schemas reduces state mutation anomalies by $>80\%$ compared to flat state dictionaries without reducing task success.
*   **Null Hypothesis ($\mathcal{H}_0$):** Typed state separation introduces schema-validation bottlenecks that reduce task completion or yield statistically indistinguishable anomaly rates ($p > 0.05$).
*   **Baseline:** Standard LangGraph / AutoGen flat dictionary state graphs.
*   **Control:** Identical underlying LLM (Claude 3.5 Sonnet / Gemini 2.0 Flash) and identical system prompts.
*   **Dataset/Environment:** 200 multi-file repository maintenance tasks from SWE-bench Lite.
*   **Independent Variable:** State storage model (Unified dictionary vs. Four-Tier gibbrn Schema).
*   **Dependent Variables:** State corruption rate, JSON parse failure rate, task completion rate.
*   **Success Threshold:** $\ge 80\%$ drop in state serialization anomalies; $\ge 0\%$ degradation in task completion.

---

### RQ2 — Canonical State Substrate vs. Native Traces
*   **Systems Question:** Does an append-only event ledger with Merkle parent chaining improve causal failure reconstruction compared to standard OpenTelemetry/LangSmith execution traces?
*   **Hypothesis ($\mathcal{H}_1$):** Causal reconstruction accuracy ($\text{CRR}$) of the root cause step in multi-step failures increases from $<40\%$ (native text traces) to $>85\%$ using the gibbrn State Spine.
*   **Null Hypothesis ($\mathcal{H}_0$):** Event-sourced causal trees provide no statistically significant improvement in root-cause localization over timestamped text logs.
*   **Baseline:** Native LangSmith / OpenTelemetry span logs.
*   **Dataset/Environment:** 150 failed trajectories from AgentErrorBench with human-annotated root-cause steps.
*   **Metrics:** Causal Reconstruction Rate ($\text{CRR}$), Time-to-Root-Cause Localization ($T_{\text{locate}}$).
*   **Success Threshold:** $\text{CRR} \ge 85\%$ ($p < 0.01$, two-tailed t-test).

---

### RQ3 — Authority-State Integrity & Anti-Laundering
*   **Systems Question:** Does an external deterministic reducer prevent endogenous authority laundering and privilege escalation attacks?
*   **Hypothesis ($\mathcal{H}_1$):** When subjected to adversarial prompt injection targeting spending limits and file scopes, the gibbrn Authority Reducer maintains $\text{UER} \le 0.001$, whereas context-managed permission systems fail with $\text{UER} > 0.35$.
*   **Null Hypothesis ($\mathcal{H}_0$):** The Effect Gate does not reduce unauthorized executions significantly below standard system prompt guardrails.
*   **Workload:** 100 injected SWE-bench coding tasks containing indirect prompt injections attempting to:
    1.  Exfiltrate environment variables.
    2.  Execute `rm -rf` outside the working directory.
    3.  Exceed predefined token spend limits ($>\$5.00$).
*   **Success Threshold:** Zero unauthorized out-of-scope executions ($\text{UER} = 0.000$) with false-denial rate ($\text{FDR}$) $< 2\%$.

---

### RQ4 — Grounded Experience Admission vs. Naive Append Memory
*   **Systems Question:** Can automated sandbox validation and regression testing prevent memory poisoning and performance degradation in continual learning loops?
*   **Hypothesis ($\mathcal{H}_1$):** Under continuous exposure to poisoned and low-quality task demonstrations, gibbrn Experience Admission maintains downstream benchmark accuracy ($<2\%$ degradation), whereas naive append-and-retrieve memory systems (e.g., MemGPT, Reflexion) degrade by $>25\%$.
*   **Null Hypothesis ($\mathcal{H}_0$):** Regression validation suites fail to identify subtly poisoned heuristics or introduce unacceptable promotion overhead ($>5\times$ cost).
*   **Baseline:** Unfiltered append-to-vector-store memory retrieval.
*   **Dataset:** 300 sequential coding and bash tasks with 15% embedded MINJA-style adversarial patterns.
*   **Success Threshold:** $\text{FPR} \le 0.02$; downstream benchmark performance retention $\ge 98\%$.

---

### RQ5 — Persistent Safety State & Cross-Trajectory Risk
*   **Systems Question:** Does a cross-trajectory Risk Ledger detect stealthy, distributed resource exfiltration attacks that bypass single-session rate limiters?
*   **Hypothesis ($\mathcal{H}_1$):** A lifetime-scoped risk ledger flags distributed threshold-slicing attacks (e.g., 50 micro-transfers of \$2.00) within $k \le 3$ iterations, whereas session-scoped guardrails fail 100% of the time.
*   **Null Hypothesis ($\mathcal{H}_0$):** Cross-trajectory state tracking produces unmanageable false-positive trip rates ($>10\%$) in normal stochastic agent operations.
*   **Workload:** 50 simulated multi-session adversarial campaigns intermingled with 200 normal development trajectories.
*   **Success Threshold:** $100\%$ detection of distributed quota violations with false alarm rate $< 1.5\%$.

---

### RQ6 — Extending Maximum Dependable Dependency Depth ($\text{MDDD}$)
*   **Systems Question:** Can state checkpoints and bounded causal replay measurably extend the dependable operating horizon of autonomous agents?
*   **Hypothesis ($\mathcal{H}_1$):** On complex multi-step tasks ($d \ge 30$), gibbrn checkpointing and causal replay increases $\text{MDDD}_{0.90}$ by at least **$2.5\times$** compared to uncheckpointed baseline agents.
*   **Null Hypothesis ($\mathcal{H}_0$):** Checkpointing and replay do not increase $\text{MDDD}$, or the cost of rollback exceeds re-running trajectories from scratch.
*   **Workload:** 80 long-horizon tasks from GAIA (General AI Assistants) Level 3 and complex multi-issue SWE-bench tasks requiring $>25$ sequential tool steps.
*   **Metrics:** $\text{MDDD}_{0.90}$, End-to-end task completion rate, Token recovery overhead.
*   **Success Threshold:** $\text{MDDD}_{0.90}(\text{gibbrn}) \ge 2.5 \times \text{MDDD}_{0.90}(\text{baseline})$ with $p < 0.001$.

---

### RQ7 — Operational Skill Accumulation Without Weight Modification
*   **Systems Question:** Can an agent systematically accumulate verified, reusable operational skills entirely in external state storage, achieving performance parity with post-trained/fine-tuned models?
*   **Hypothesis ($\mathcal{H}_1$):** An agent accumulating verified skills in $\mathcal{S}_{\text{ops}}$ achieves comparable task speedup ($>30\%$) and success rates on recurring repo tasks as an agent fine-tuned via LoRA, while maintaining zero catastrophic forgetting on unrelated tasks.
*   **Null Hypothesis ($\mathcal{H}_0$):** External operational skills fail to transfer across slight task variations, requiring parameter modification for true procedural competence.
*   **Workload:** Recurring maintenance workflows across 5 open-source repositories (Django, SymPy, Flask, Requests, Scikit-learn).
*   **Success Threshold:** Task resolution speedup $\ge 30\%$; Catastrophic forgetting on GSM8k/MMLU $= 0.0\%$.

---

### RQ8 — Cross-Runtime Portability and Overhead
*   **Systems Question:** Can the gibbrn State Integrity Layer interface with diverse agent frameworks and foundation models with acceptable runtime latency?
*   **Hypothesis ($\mathcal{H}_1$):** gibbrn can be integrated into at least two distinct agent frameworks (LangGraph and SWE-agent/OpenHands) across two model families (Anthropic Claude and Google Gemini), introducing $<25\text{ms}$ median effect gate latency and $<5\%$ total compute overhead.
*   **Null Hypothesis ($\mathcal{H}_0$):** Adapting gibbrn across different frameworks requires bespoke rewrites that defeat the framework-neutral thesis, or latency overhead exceeds $100\text{ms}$ per step.
*   **Evaluation:** Benchmarking 100 identical tasks across:
    1.  LangGraph + Claude 3.5 Sonnet
    2.  LangGraph + Gemini 2.0 Flash
    3.  SWE-agent + Claude 3.5 Sonnet
    4.  SWE-agent + Gemini 2.0 Flash
*   **Success Threshold:** Median intercept latency $\le 25\text{ms}$; code portability requiring $<200$ lines of framework adapter code.

---

## 4. Benchmark Suite Summary and Power Analysis

Table 6.1 details the statistical design and sample sizes for the 18-month benchmark campaign.

### Table 6.1: Benchmark Suite and Statistical Methodology

| RQ | Target Benchmark / Dataset | Sample Size ($N$) | Statistical Test | Power ($1 - \beta$) | Significance ($\alpha$) | Confounder Controls |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **RQ1** | SWE-bench Lite (Multi-file) | 200 tasks | McNemar's Test (Paired) | 0.90 | 0.01 | Fixed prompt seed, identical context window |
| **RQ2** | AgentErrorBench Trajectories | 150 failures | Wilcoxon Signed-Rank | 0.85 | 0.01 | Blinded human evaluation of root cause |
| **RQ3** | Prompt Injection Red-Team Suite | 100 attacks | Fisher's Exact Test | 0.95 | 0.001 | Dynamic injection string randomization |
| **RQ4** | Continual Learning SWE Suite | 300 sequential | Two-way ANOVA | 0.90 | 0.05 | Task ordering permutation (Latin square) |
| **RQ5** | Multi-Session Exfiltration Suite | 50 campaigns | Binomial Exact Test | 0.95 | 0.01 | Realistic background noise tasks |
| **RQ6** | GAIA Level 3 & SWE Long-Horizon | 80 deep tasks | Survival Analysis (Kaplan-Meier) | 0.85 | 0.01 | Tool execution latency normalization |
| **RQ7** | Multi-Repo Maintenance Tasks | 100 tasks | Paired Student's t-test | 0.85 | 0.05 | Zero overlap between train and test repos |
| **RQ8** | Multi-Framework Harness Suite | 100 tasks $\times$ 4 | Repeated Measures ANOVA | 0.90 | 0.05 | Network virtualization latency isolation |

---

## References

*   [1] C. E. Jimenez et al., "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?" in *Proc. ICLR*, 2024.
*   [2] AgentErrorBench Consortium, "Benchmarking Cascading Failures in Autonomous Agents," *OpenReview*, 2025.
*   [3] G. Mialon et al., "GAIA: A Benchmark for General AI Assistants," in *Proc. ICLR*, 2024.
*   [4] Z. Chen et al., "MINJA: Memory Injection Attacks against Large Language Model-based Agents," *arXiv preprint arXiv:2402.04944*, 2024.
*   [5] S. Yao et al., "Tau-bench: A Benchmark for Tool-Agent-User Interactions in Real-World Environments," *arXiv preprint arXiv:2406.12045*, 2024.
