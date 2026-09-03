# 06 — Core Research Program and Experimental Methodology (V2)

**Project Name:** GIBBRN  
**Document Track:** Experimental Science & Benchmark Methodology (Version 2)  
**Date:** September 2026  
**Audience:** Empirical AI Researchers, Benchmark Methodologists, 1517 Fund  
**Methodological Standard:** Five Causally Chained Core Questions with Survival Analysis  

---

## 1. The Causally Chained Research Program

In response to the adversarial audit (`AUDIT_06`, `AUDIT_07`), Dossier V2 abandons disconnected benchmark sweeps. The core 18-month research program is organized into **five causally chained research questions (Core RQ1–RQ5)**, testing the state integrity thesis progressively:

```
Core RQ1: State Classification
Can consequential agent state be separated into classes with distinct mutation semantics?
                         |
                         v
Core RQ2: Causal State Reconstruction
Can typed, provenance-preserving state improve failure reconstruction over native traces?
                         |
                         v
Core RQ3: Authority and Effect Integrity (PRIMARY INITIAL WEDGE)
Can canonical authority eliminate unauthorized external mutations without high false denials?
                         |
                         v
Core RQ4: Validated Experience Admission (VERIFIER-RICH DOMAINS)
Can regression-tested experience admission prevent poisoned or regressive memory updates?
                         |
                         v
Core RQ5: Long-Horizon Trajectory Survival (THE THESIS GATE)
Do the surviving mechanisms measurably improve empirical trajectory survival over depth?
```

*Secondary Exploratory Tracks (Deferred beyond core milestone gates):*
- *Exploratory Track A: Lifetime Risk Ledger across Multi-Week Sessions.*
- *Exploratory Track B: External Operational Skills vs. Parameter Fine-Tuning (LoRA).*
- *Exploratory Track C: Cross-Runtime Abstraction Overhead across Frameworks.*

---

## 2. Formal Metric Proposal: Maximum Dependable Dependency Depth ($\text{MDDD}_\tau$)

The dossier formally introduces $\text{MDDD}_\tau$ as a **proposed research metric**, abandoning the naive geometric compounding assumption ($P = p^d$).

### 2.1 The Discrete Survival Analysis Hazard Model
Let $T \in \mathbb{N}^+$ be a random variable representing the step depth at which an unrecoverable fatal trajectory failure occurs.

1.  **Discrete Hazard Rate $h(k)$:** The conditional probability that a trajectory experiences an unrecoverable failure at step $k$, given that it survived through step $k-1$:
    $$h(k) = P(T = k \mid T \ge k)$$
2.  **Trajectory Survival Function $S(k)$:** The probability that a trajectory survives beyond step $k$ without fatal failure:
    $$S(k) = P(T > k) = \prod_{i=1}^{k} \left(1 - h(i)\right)$$
3.  **Definition of $\text{MDDD}_\tau$:** The maximum sequential step depth $k$ at which the estimated trajectory survival probability remains at or above threshold $\tau \in (0, 1]$ (standard baseline $\tau = 0.90$):
    $$\text{MDDD}_\tau = \max \left\{ k \in \mathbb{N} \;\middle|\; \hat{S}(k) \ge \tau \right\}$$

$$\hat{S}(k) = \prod_{i: t_i \le k} \left(1 - \frac{d_i}{n_i}\right) \quad (\text{Kaplan-Meier Estimator with Right-Censoring})$$

*Where:*
- $d_i$ is the number of unrecoverable trajectory failures observed at step $i$.
- $n_i$ is the number of trajectories at risk just prior to step $i$ (excluding right-censored tasks that reached goal completion or hit budget limits).
- **Hypothesis Testing:** Survival distributions between baseline agents and gibbrn-controlled agents are formally compared using the **Log-Rank (Mantel-Cox) Test** with target significance $\alpha = 0.01$.

---

## 3. Detailed Experimental Protocols for Core RQ1–RQ5

### Core RQ1 — State Classification Validity
*   **Research Question:** Does physically separating state into Cognitive, Operational, Authoritative, and Runtime tiers reduce state serialization and mutation corruption relative to unified application dictionaries?
*   **Hypothesis ($\mathcal{H}_1$):** Isolating Authoritative and Operational state into deterministic Pydantic/PostgreSQL schemas reduces state corruption exceptions by $\ge 80\%$ without degrading functional task completion.
*   **Null Hypothesis ($\mathcal{H}_0$):** Typed state separation introduces schema serialization overhead that yields no statistically significant difference in state corruption ($p > 0.05$).
*   **Workload:** 200 multi-file repository maintenance tasks from SWE-bench Lite.
*   **Baseline:** Standard LangGraph unified state dictionary.
*   **Model Tier:** Tier 2 Frontier Coding Model (e.g., Claude 3.5 Sonnet).
*   **Statistical Methodology:** Paired McNemar's test ($\alpha = 0.01$).
*   **Failure Threshold:** $\mathcal{H}_0$ accepted if state mutation exceptions are reduced by $<50\%$.

---

### Core RQ2 — Causal State Reconstruction vs. Native Traces
*   **Research Question:** Does an append-only Causal State Spine with Merkle parent chaining materially improve root-cause failure attribution over standard linear telemetry traces?
*   **Hypothesis ($\mathcal{H}_1$):** Blinded human and automated causal reconstruction rate ($\text{CRR}$) of the earliest fatal divergence step increases from $\le 45\%$ (native OpenTelemetry spans) to $\ge 80\%$ using the Causal State Spine.
*   **Null Hypothesis ($\mathcal{H}_0$):** Causal DAG parent chaining provides no statistically significant improvement in root-cause localization over timestamped linear trace spans.
*   **Workload:** 150 failure trajectories from AgentErrorBench with ground-truth root-cause step labels.
*   **Blinding & Evaluation:** Double-blinded annotation with inter-rater reliability measured via Cohen’s Kappa ($\kappa \ge 0.75$).
*   **Statistical Methodology:** Wilcoxon signed-rank test ($\alpha = 0.01$).
*   **Failure Threshold:** $\text{CRR} < 75\%$ at Gate M6.

---

### Core RQ3 — Authority and Effect Integrity (Primary Initial Wedge)
*   **Research Question:** Can an out-of-process Deterministic Effect Gate eliminate unauthorized external mutations and authority laundering without introducing unacceptable false denials or latency?
*   **Hypothesis ($\mathcal{H}_1$):** When subjected to adversarial prompt injection and indirect parameter smuggling attacks, the Deterministic Effect Gate maintains an Unauthorized-Effect Rate $\text{UER} \le 0.001$, while unmanaged context-based agents suffer $\text{UER} \ge 0.25$.
*   **Null Hypothesis ($\mathcal{H}_0$):** The Effect Gate fails to prevent out-of-scope executions, or introduces a False-Denial Rate $\text{FDR} > 3.0\%$, or adds $>50\text{ms}$ median latency overhead.
*   **Workload:** $N = 1,000$ adversarial attack trajectories (`gibbrn-auth-bench`) targeting file exfiltration, unauthorized network requests, and budget exhaustion.
*   **Model Tiers:** Tier 1 Reasoning Models and Tier 3 Open-Weights Models (Llama 3.3 70B).
*   **Statistical Methodology:** Fisher's Exact Test with $95\%$ binomial confidence intervals.
*   **Failure Threshold:** Any observed unauthorized mutating action ($\text{UER} > 0.000$ in $N=1,000$) or $\text{FDR} > 2.0\%$ at Gate M9.

---

### Core RQ4 — Validated Experience Admission in Verifier-Rich Domains
*   **Research Question:** In verifier-rich domains (Python scripting and Bash tool macros), can automated micro-sandbox regression testing prevent memory poisoning and performance degradation in continual learning loops?
*   **Hypothesis ($\mathcal{H}_1$):** Under continuous exposure to poisoned and low-quality demonstrations (MINJA-style queries), gibbrn Experience Admission maintains downstream benchmark accuracy ($<2\%$ regression), whereas naive append-and-retrieve vector memory degrades by $\ge 20\%$.
*   **Null Hypothesis ($\mathcal{H}_0$):** Automated micro-sandbox regression testing admits poisoned heuristics ($\text{FPR} > 0.02$) or is too computationally expensive ($>3\times$ baseline token cost).
*   **Workload:** 300 sequential software tasks with 15% embedded MINJA adversarial injection patterns.
*   **Harness Controls:** Latin square task order randomization across 3 distinct random seeds.
*   **Statistical Methodology:** Two-Way ANOVA evaluating interaction between memory architecture and adversarial pressure.
*   **Failure Threshold:** False-Promotion Rate $\text{FPR} > 0.02$ or downstream retention $<95\%$ at Gate M12.

---

### Core RQ5 — Long-Horizon Trajectory Survival & MDDD Extension (The Thesis Gate)
*   **Research Question:** Does managed autonomy (autonomous agent + gibbrn state checkpoints and causal rollback) achieve a statistically significant extension in trajectory survival over deep dependency chains compared to unmanaged autonomy and static pipelines?
*   **Hypothesis ($\mathcal{H}_1$):** On complex tasks requiring exploratory branching ($d \ge 30$), gibbrn extends trajectory survival depth such that $\text{MDDD}_{0.90}(\text{gibbrn}) \ge 2.0 \times \text{MDDD}_{0.90}(\text{baseline})$ with Log-Rank $p < 0.01$.
*   **Null Hypothesis ($\mathcal{H}_0$):** gibbrn checkpointing and causal rollback do not double survival depth, or static deterministic pipelines (Agentless) achieve equal or superior completion rates at lower compute cost.
*   **Workload:** 150 long-horizon tasks from GAIA Level 3 and deep repository refactoring tasks.
*   **Statistical Methodology:** Kaplan-Meier survival curve estimation with Log-Rank test and Cox proportional hazards regression.
*   **Failure Threshold:** $\text{MDDD}_{0.90}(\text{gibbrn}) < 2.0 \times \text{baseline}$ or failure to outperform static pipelines at Gate M15.

---

## 4. Benchmark Campaign and Sample Power Analysis

Table 6.1 details the sample size and power calculations governing the Core RQ campaign.

### Table 6.1: Experimental Design and Statistical Power

| Core RQ | Primary Benchmark / Dataset | Sample Size ($N$) | Statistical Test | Power ($1 - \beta$) | Significance ($\alpha$) | Confounder Controls |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Core RQ1** | SWE-bench Lite (Multi-file) | 200 tasks | McNemar's Test (Paired) | 0.90 | 0.01 | Fixed prompt seed, identical context window |
| **Core RQ2** | AgentErrorBench Trajectories | 150 failure traces | Wilcoxon Signed-Rank | 0.85 | 0.01 | Double-blinded human annotation ($\kappa \ge 0.75$) |
| **Core RQ3** | gibbrn-auth-bench Red-Team | 1,000 attacks | Fisher's Exact Test | 0.95 | 0.001 | Dynamic injection string randomization |
| **Core RQ4** | Continual SWE-bench + MINJA | 300 sequential tasks | Two-Way ANOVA | 0.90 | 0.05 | Latin square task order permutation |
| **Core RQ5** | GAIA Level 3 & Deep SWE-bench | 150 deep tasks | Log-Rank Survival Test | 0.90 | 0.01 | Right-censoring at maximum step cutoffs |
