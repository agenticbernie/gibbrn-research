# AUDIT-06: Experimental Design, Statistical Methodology, and MDDD Reformulation

**Target Project:** GIBBRN  
**Auditing Body:** 1517 Fund Adversarial Diligence Committee  
**Standard:** Empirical Statistical Rigor, Hypothesis Falsifiability, and Survival Analysis  

---

## 1. The Core Methodological Critique: The Fallacy of Geometric Error Compounding

Across the entire GIBBRN dossier (`01`, `02`, `05`, `06`, `09`, `10`), the foundational motivation for the project is justified by the following formula:

$$P_{\text{task}} = \prod_{i=1}^{d} p_i \approx p_{\text{step}}^d \quad \implies \quad 0.98^{50} \approx 36.4\%$$

### The Diligence Finding:
> **This formula is mathematically naive and scientifically invalid when applied to autonomous software agents.**

### Why the Geometric Independence Model Fails:
1.  **Violation of the i.i.d. Assumption (Error Autocorrelation):**
    The geometric model assumes that the probability of success at step $k$ is independent of step $k-1$. In real-world software agents, errors are **strongly autocorrelated**. If an agent introduces a subtle syntax bug at step 3, the probability of failure at step 4 is drastically higher. Trajectories exhibit Markovian state dependency, not memoryless coin flips.
2.  **Ignorance of Agent Recovery Loops:**
    Autonomous agents do not fail irrevocably on a single tool error. Modern harnesses incorporate retry loops, exception handlers, and alternative tool branches. A single step failure does not crash the trajectory; rather, failure is governed by **unrecovered cascading errors**.
3.  **Variable Step Criticality:**
    Not all steps have equal semantic weight. A read-only `ls` command has a near-zero failure hazard, whereas a mutating `git rebase` or database migration has a high irreversibility hazard. Treating all steps as identical Bernoulli trials with uniform probability $p$ distorts empirical modeling.

---

## 2. Rigorous Reformulation: Survival Analysis & The Hazard Model

To withstand academic peer review and technical diligence, gibbrn must abandon the naive $p^d$ formula and adopt formal **Discrete Survival Analysis with Hazard Rate Modeling**.

```
+-----------------------------------------------------------------------------------+
|                        REFORMULATED MDDD SURVIVAL MODEL                           |
+-----------------------------------------------------------------------------------+
| Let T be the random variable denoting the step depth where an unrecoverable       |
| fatal trajectory failure occurs.                                                  |
|                                                                                   |
| Discrete Hazard Function h(k):                                                    |
|   h(k) = P(T = k | T >= k)                                                        |
|   (The conditional probability of fatal failure at step k, given survival to k)   |
|                                                                                   |
| Trajectory Survival Function S(k):                                                |
|   S(k) = P(T > k) = \prod_{i=1}^{k} (1 - h(i))                                    |
|                                                                                   |
| Rigorous Maximum Dependable Dependency Depth (MDDD_tau):                          |
|   MDDD_tau = max { k in N | S_hat(k) >= tau }                                     |
|   where S_hat(k) is estimated via the non-parametric Kaplan-Meier estimator       |
|   accounting for right-censoring at maximum step budget limits.                   |
+-----------------------------------------------------------------------------------+
```

### Empirical Advantage of the Survival Model:
- **Captures Error Cascades:** If the hazard rate $h(k)$ spikes between steps 10 and 20, gibbrn can empirically prove that error cascades concentrate in specific phases, justifying dynamic checkpoint placement.
- **Handles Censoring:** Trajectories that hit the maximum step limit (e.g., $k = 50$) without failing are treated as right-censored data points rather than arbitrary successes or failures.
- **Falsifiable Metric:** $\text{MDDD}_\tau$ becomes an empirical quantile extracted directly from survival curves, allowing rigorous hypothesis testing via the **Log-Rank Test** comparing baseline vs. gibbrn survival distributions.

---

## 3. Review of Research Questions (RQ1–RQ8)

Table 6.1 evaluates the experimental design and statistical power for each proposed research question.

### Table 6.1: Research Question Diligence Evaluation

| Research Question | Stated Hypothesis & Baseline | Sample Size ($N$) | Proposed Statistical Test | Diligence Methodological Assessment & Required Redesign |
| :--- | :--- | :--- | :--- | :--- |
| **RQ1: State Taxonomy** | Flat dict vs. 4-tier typed schema | 200 tasks (SWE Lite) | McNemar's Test (Paired) | **VALID.** Paired design controls for issue difficulty. Need to ensure internal schema serialization errors are logged separately from functional test failures. |
| **RQ2: State Spine vs. Traces** | Merkle DAG vs. OpenTelemetry spans | 150 failure traces (AgentErrorBench) | Wilcoxon Signed-Rank | **HIGH RISK OF EVALUATOR BIAS.** "Root-cause localization" is subjective. Must use blinded, double-annotated evaluation with inter-rater reliability measured via Cohen’s Kappa ($\kappa \ge 0.75$). |
| **RQ3: Authority Reducer** | Prompt guardrails vs. Deterministic gate | 100 prompt injection attacks | Fisher's Exact Test | **STATISTICALLY UNDERPOWERED.** To prove $\text{UER} \le 0.001$ with $95\%$ confidence, a sample size of $N = 100$ is completely inadequate (rule of three requires $N \ge 3,000$ for zero occurrences). Expand sample size to $N \ge 1,000$. |
| **RQ4: Experience Admission** | Append-and-retrieve memory vs. Sandbox validation | 300 sequential tasks with 15% MINJA | Two-Way ANOVA | **STRONG DESIGN.** Latin square permutation of task order is essential to eliminate curriculum learning confounders. |
| **RQ5: Persistent Risk Ledger** | Session-reset guardrails vs. Cross-trajectory ledger | 50 multi-session campaigns | Binomial Exact Test | **ADEQUATE FOR POC.** Sufficient to demonstrate the theoretical blindspot of session-reset rate limiters. |
| **RQ6: MDDD Extension** | Uncheckpointed agent vs. gibbrn state checkpoints | 80 deep tasks (GAIA Level 3) | Survival Analysis (Kaplan-Meier) | **EXCELLENT REFORMULATION.** Replace arbitrary $2.0\times$ metric with Log-Rank test ($p < 0.01$) comparing Kaplan-Meier survival curves. Expand sample size from 80 to 150 tasks. |
| **RQ7: Skill Accumulation** | Parameter LoRA fine-tuning vs. External $\mathcal{S}_{\text{ops}}$ skills | 100 tasks across 5 repositories | Paired Student's t-test | **CONFIRM REPOSITORY ISOLATION.** Zero overlap between evaluation repos and demonstration repos to prevent data contamination. |
| **RQ8: Cross-Runtime Portability**| $2 \times 2$ matrix (LangGraph/SWE-agent $\times$ Claude/Gemini) | 100 tasks $\times$ 4 conditions | Repeated Measures ANOVA | **CLEAN SYSTEMS EXPERIMENT.** Standard systems latency and throughput profiling. Validated. |

---

## 4. Confounder Control Directives

To ensure that experimental results cannot be dismissed as benchmark noise or provider drift, the research harness must enforce the following controls:

1.  **Model Temperature Zero & Seed Pinning:** All generative inference must be pinned to `temperature = 0.0` with explicit random seed initialization where supported by APIs.
2.  **Snapshot Caching of Tool Outputs:** External HTTP and package manager calls (e.g., `pip install`, `npm install`) must run through a local caching proxy to prevent network fluctuations from contaminating step execution times.
3.  **Stratified Task Ordering:** When evaluating continual memory (RQ4), task sequences must be shuffled across multiple seeds to prove that skill retention is invariant to task arrival order.
