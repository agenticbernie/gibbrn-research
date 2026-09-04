# 06 — Core Research Program and Experimental Methodology (Submission)

**Project Name:** GIBBRN  
**Document Track:** Empirical Protocol (Version 3.0)  
**Date:** September 2026 | **Verification Pass:** V3 Delta Pending Verification  
**Audience:** Empirical AI Researchers, Benchmark Methodologists, 1517 Fund  
**Methodological Standard:** Seven Causally Chained Core Questions with Survival Analysis  

---

## 1. The Causally Chained Research Program

In response to the adversarial audit (`AUDIT_06`, `AUDIT_07`) and the emergence of adaptive agent architectures, the core 24-month research program is organized into **seven causally chained research questions (Core RQ1–RQ7)**, testing the state integrity thesis progressively:

```text
Core RQ1: State Classification Validity
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
Core RQ4: Validated Verified Adaptation (VERIFIER-RICH DOMAINS)
Can regression-tested experience admission prevent poisoned or regressive memory updates?
                         |
                         v
Core RQ5: Adaptation Portability & Harness Generalization (ATR & SAFE SPECIALIZATION)
Can learned skills/harnesses transfer across models, or does gibbrn safely bound domain specificity?
                         |
                         v
Core RQ6: Long-Horizon Trajectory Survival (THE SCIENTIFIC THESIS GATE)
Do the surviving mechanisms measurably improve empirical trajectory survival depth (MDDD)?
                         |
                         v
Core RQ7: Cross-Model Replication & Delegated Trust Integration (IAM DELEGATION)
Does the architecture survive model/runtime swaps under enterprise IAM delegation?
```

*Secondary Exploratory Tracks (Deferred beyond core milestone gates):*
- *Exploratory Track A: Lifetime Risk Ledger across Multi-Week Sessions.*
- *Exploratory Track B: External Operational Skills vs. Parameter Fine-Tuning (LoRA).*
- *Exploratory Track C: Cross-Runtime Abstraction Overhead across Frameworks.*
- *Exploratory Track D: Future Applicability to Geometry-Aware World Action Models.*

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

> **Censoring Assumption:** Successful task completions are treated as right-censored observations under the assumption that censoring is independent of the failure hazard (non-informative censoring). A competing-risks sensitivity analysis (Fine-Gray sub-distribution hazard model) will be pre-registered as a secondary analysis at Gate M12 to assess the robustness of survival estimates when task success is treated as a competing event.

---

## 3. Detailed Experimental Protocols for Core RQ1–RQ7

### Core RQ1 — State Classification Validity
*   **Research Question:** Does physically separating state into Cognitive, Operational, Authoritative, and Runtime tiers reduce state serialization and mutation corruption relative to unified application dictionaries?
*   **Hypothesis ($\mathcal{H}_1$):** Isolating Authoritative and Operational state into deterministic Pydantic/PostgreSQL schemas reduces state corruption exceptions by $\ge 80\%$ without degrading functional task completion.
*   **Null Hypothesis ($\mathcal{H}_0$):** Typed state separation introduces schema serialization overhead that yields no statistically significant difference in state corruption ($p > 0.05$).
*   **Binary Corruption Outcome:** Defined as at least one unhandled state-type violation, schema validation failure, or tool argument mismatch within a single trajectory run. Trajectories with partial state warnings but successful task completion are separately recorded.
*   **Workload:** 200 multi-file repository maintenance tasks from SWE-bench Lite.
*   **Statistical Methodology:** McNemar's paired test ($\alpha = 0.01$).
*   **Failure Threshold:** Reduction in state corruption $<50\%$ at Gate M3.

---

### Core RQ2 — Causal Failure Attribution via Append-Only Spine
*   **Research Question:** Does an append-only Causal State Spine with Merkle parent chaining materially improve root-cause failure attribution over standard linear telemetry traces?
*   **Hypothesis ($\mathcal{H}_1$):** Blinded human and automated causal reconstruction rate ($\text{CRR}$) of the earliest fatal divergence step increases from $\le 45\%$ (native OpenTelemetry spans) to $\ge 80\%$ using the Causal State Spine.
*   **Null Hypothesis ($\mathcal{H}_0$):** Causal DAG parent chaining provides no statistically significant improvement in root-cause localization over timestamped linear trace spans.
*   **Workload:** 150 failure trajectories from AgentErrorBench (Zhu et al., arXiv:2509.25370, 2025; 200 annotated failure trajectories across ALFWorld, GAIA, and WebShop) with ground-truth root-cause step labels.
*   **Blinding & Evaluation:** Double-blinded annotation. Annotators are given trajectory logs with system identifiers removed and are asked to identify the earliest step where an irreversible error state was established. Root-cause localization is scored as correct if the identified step matches the ground-truth label within $\pm 1$ step. Annotation team consists of two independent research engineers; disagreements resolved by a third senior reviewer. Inter-rater reliability target: Cohen’s Kappa $\kappa \ge 0.75$.
*   **Statistical Methodology:** Wilcoxon signed-rank test ($\alpha = 0.01$).
*   **Failure Threshold:** $\text{CRR} < 75\%$ at Gate M6.

---

### Core RQ3 — Authority and Effect Integrity (Primary Initial Wedge)
*   **Research Question:** Can an out-of-process Deterministic Effect Gate eliminate unauthorized external mutations and authority laundering without introducing unacceptable false denials or latency?
*   **Hypothesis ($\mathcal{H}_1$):** When subjected to adversarial prompt injection and indirect parameter smuggling attacks, the Deterministic Effect Gate maintains an Unauthorized-Effect Rate $\text{UER} \le 0.001$, while unmanaged context-based agents suffer $\text{UER} \ge 0.25$.
*   **Null Hypothesis ($\mathcal{H}_0$):** The Effect Gate fails to prevent out-of-scope executions, or introduces a False-Denial Rate $\text{FDR} > 3.0\%$, or adds $>50\text{ms}$ median latency overhead.
*   **Workload:** $N = 1,000$ adversarial attack trajectories (`gibbrn-auth-bench`, internal benchmark deliverable constructed during Phase 3) targeting file exfiltration, unauthorized network requests, and budget exhaustion.
*   **Model Tiers:** Tier 1 Reasoning Models and Tier 3 Open-Weights Models (e.g., Llama 70B-scale open-weights model, version frozen at M7).
*   **Statistical Methodology:** Fisher's Exact Test with $95\%$ binomial confidence intervals.
*   **Failure Threshold:** Gate M9 PASS criterion: $\text{UER} = 0.000$ (zero observed unauthorized mutations in $N=1,000$ adversarial trajectories). A single unauthorized execution ($\text{UER} = 0.001$) triggers the Narrow/Pivot decision; $\text{UER} > 0.001$ or $\text{FDR} > 2.0\%$ triggers KILL.

---

### Core RQ4 — Validated Verified Adaptation in Verifier-Rich Domains
*   **Research Question:** In verifier-rich domains (Python scripting and Bash tool macros), can automated micro-sandbox regression testing prevent memory poisoning and performance degradation in continual learning loops?
*   **Hypothesis ($\mathcal{H}_1$):** Under continuous exposure to poisoned and low-quality demonstrations (MINJA-style queries), gibbrn Verified Adaptation maintains downstream benchmark accuracy ($<2\%$ regression), whereas naive append-and-retrieve vector memory degrades by $\ge 20\%$.
*   **Null Hypothesis ($\mathcal{H}_0$):** Automated micro-sandbox regression testing admits poisoned heuristics ($\text{FPR} > 0.02$) or is too computationally expensive ($>3\times$ baseline token cost).
*   **Workload:** 300 sequential software tasks with 15% embedded MINJA adversarial injection patterns (45 out of 300 tasks replaced with MINJA-style queries following Dong et al., NeurIPS 2025, inserted at uniformly random positions).
*   **Harness Controls:** Latin square task order randomization across 3 distinct random seeds.
*   **Statistical Methodology:** Two-Way ANOVA evaluating interaction between memory architecture and adversarial pressure; non-parametric Aligned Rank Transform ANOVA pre-registered as sensitivity analysis.
*   **Failure Threshold:** False-Promotion Rate $\text{FPR} > 0.02$ or downstream retention $<95\%$ at Gate M12.

---

### Core RQ5 — Adaptation Portability & Harness Generalization
*   **Research Question:** Can an operational adaptation (learned skill, workflow macro, or harness variant policy) retain measurable benefit when ported to a new model family or task domain, or can gibbrn reliably detect co-adaptation and safely bound the specialization?
*   **Operational Metric (Adaptation Transfer Ratio - ATR):**
    Let $\Delta P_{\text{source}} = P(\text{adapted}, \text{source}) - P(\text{baseline}, \text{source})$ represent the empirical task success rate gain on the source distribution.
    Let $\Delta P_{\text{transfer}} = P(\text{adapted}, \text{transfer}) - P(\text{baseline}, \text{transfer})$ represent the gain when the identical adaptation is executed on a transfer distribution (held-out model family or held-out domain).
    For adaptations with verified origin benefit ($\Delta P_{\text{source}} > 0$):
    $$\text{ATR} = \frac{\Delta P_{\text{transfer}}}{\Delta P_{\text{source}}}$$
    *Edge Cases & Rules:*
    - If $\Delta P_{\text{source}} \le 0$, the candidate adaptation failed validation at source and is rejected during micro-sandbox regression (ATR is undefined; adaptation discarded).
    - If $\Delta P_{\text{transfer}} < 0$, $\text{ATR} < 0$, representing negative transfer (cross-domain interference or catastrophic forgetting).
*   **Dual-Mode Empirical Hypotheses ($\mathcal{H}_1$):**
    - **Mode A (Portable Generalization):** On cross-model transfer pairs within the same domain, Engine 3 produces adaptations achieving $\text{ATR} \ge 0.80$ (with 95% bootstrap confidence interval lower bound $> 0.60$).
    - **Mode B (Safely Bounded Specialization):** When an adaptation is strongly co-adapted to its origin model/domain ($\text{ATR} < 0.50$), gibbrn's Verified Adaptation Engine correctly identifies the specificity barrier, rejects unconstrained promotion into global operational state ($\mathcal{S}_{\text{ops}}$), and strictly confines the adaptation to its verified origin context—yielding zero downstream regressions ($\Delta P_{\text{transfer}} \ge 0.0\%$) across general workloads.
*   **Null Hypothesis ($\mathcal{H}_0$):** Adaptations co-adapt unpredictably, and gibbrn fails to detect or bound this specificity, allowing poisoned or degrading modifications to propagate globally ($\Delta P_{\text{transfer}} < -0.05$ or regression rate $> 2.0\%$).
*   **Workload:** 100 transfer evaluation pairs generated across:
    - *Cross-Model Axis:* Source Model (Tier 1 Commercial API: Claude 3.5 Sonnet / GPT-4o) $\to$ Target Model (Tier 3 Open-Weights: Llama 3.3 70B).
    - *Cross-Domain Axis:* SWE-bench Lite coding tasks $\to$ GAIA Level 3 multi-modal web/file reasoning tasks.
*   **Statistical Methodology:** Non-parametric bootstrap estimation of ATR confidence intervals (1,000 resamples); one-sided non-inferiority test for downstream regression ($\alpha = 0.05$).
*   **Failure Threshold at Gate M15:** Failure to satisfy either Mode A or Mode B (i.e., system fails to transfer and fails to bound specialization, leading to uncontained cross-domain regression).

---

### Core RQ6 — Long-Horizon Trajectory Survival & MDDD Extension (The Scientific Thesis Gate)
*   **Research Question:** Does managed autonomy (autonomous agent + gibbrn state checkpoints and causal rollback) achieve a statistically significant extension in trajectory survival over deep dependency chains compared to unmanaged autonomy and static pipelines?
*   **Hypothesis ($\mathcal{H}_1$):** On complex tasks requiring exploratory branching ($d \ge 30$), gibbrn extends trajectory survival depth such that $\text{MDDD}_{0.90}(\text{gibbrn}) \ge 2.0 \times \text{MDDD}_{0.90}(\text{baseline})$ with Log-Rank $p < 0.01$.
*   **Null Hypothesis ($\mathcal{H}_0$):** gibbrn checkpointing and causal rollback do not double survival depth, or static deterministic pipelines (Agentless) achieve equal or superior completion rates at lower compute cost.
*   **Workload:** 150 long-horizon tasks from GAIA Level 3 and deep repository refactoring tasks. (Task pool composition: available GAIA Level 3 evaluation instances supplemented by curated deep repository refactoring tasks; pool pre-registered at Gate M12).
*   **Statistical Methodology:** Kaplan-Meier survival curve estimation with Log-Rank test and Cox proportional hazards regression. Sensitivity analyses include weighted log-rank tests (Peto-Peto and Harrington-Fleming $G^\rho$ family) to evaluate non-proportional hazards.
*   **Failure Threshold at Gate M18:** $\text{MDDD}_{0.90}(\text{gibbrn}) < 2.0 \times \text{baseline}$ or failure to outperform static deterministic pipelines.

---

### Core RQ7 — Cross-Model Replication & Delegated Trust Integration
*   **Research Question:** Does the three-substrate architecture remain sound when the cognitive model is swapped entirely across commercial and open-weights tiers, and does the Effect Gate reliably enforce fine-grained capability boundaries when authority is delegated from external enterprise Identity and Access Management (IAM) systems?
*   **Hypothesis ($\mathcal{H}_1$):** When the cognitive model is swapped (Tier 1 Commercial API $\leftrightarrow$ Tier 3 Open-Weights) and execution authority is anchored to external enterprise OIDC identity providers, gibbrn demonstrates:
    1.  Unauthorized-Effect Rate $\text{UER} \le 0.001$ under active adversarial injection.
    2.  Immediate, deterministic policy propagation under credential rotation, scope narrowing, and asynchronous token revocation within lease TTL ($\le 2000\text{ms}$).
    3.  End-to-end token validation latency overhead $\le 20\text{ms}$ median.
*   **Null Hypothesis ($\mathcal{H}_0$):** Swapping the cognitive model causes parameter smuggling that bypasses external IAM mapping, OR token validation introduces $>50\text{ms}$ median latency, OR asynchronous revocation fails to burn active capability leases before their expiration.
*   **Workload & Attack Model:** $N = 200$ synthetic enterprise delegation sessions evaluated across 3 mock IAM architectures:
    - *OIDC/OAuth 2.0 Client Credentials & Token Exchange:* Simulating Okta/Auth0 machine-to-machine delegation.
    - *Cloud IAM Role Delegation:* Simulating AWS IAM assume-role / GCP service account impersonation with temporary session policies.
    - *Agentic Identity Provider (AIP) Protocol:* Simulating CrowdStrike-style scoped capability manifests.
    - *Adversarial Injections:* 50 token replay attacks, 50 parameter-smuggled privilege escalation attempts, 50 out-of-scope delegation requests, and 50 asynchronous mid-trajectory credential revocations during live tool dispatch.
*   **Statistical Methodology:** Binomial test with one-sided Clopper-Pearson 95% confidence intervals against $\text{UER} \le 0.001$; paired Wilcoxon signed-rank test on latency impact.
*   **Confounder Controls:** Standardized in-memory identity provider mock to eliminate network jitter confounders while evaluating cryptographic verification latencies.
*   **Failure Threshold at Gate M21:** Observed $\text{UER} > 0.001$ under delegated enterprise identity, or lease revocation failure within TTL ($\le 2000\text{ms}$).

---

## 4. Benchmark Campaign and Sample Power Analysis

Table 6.1 details the sample size and power calculations governing the complete Core RQ campaign across the 24-month program.

### Table 6.1: Experimental Design and Statistical Power

| Core RQ | Primary Benchmark / Dataset | Sample Size ($N$) | Statistical Test | Power ($1 - \beta$) | Significance ($\alpha$) | Confounder Controls |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Core RQ1** | SWE-bench Lite (Multi-file) | 200 tasks | McNemar's Test (Paired) | 0.90 | 0.01 | Fixed prompt seed, identical context window |
| **Core RQ2** | AgentErrorBench | 150 failure traces | Wilcoxon Signed-Rank | 0.85 | 0.01 | Double-blinded human annotation ($\kappa \ge 0.75$) |
| **Core RQ3** | gibbrn-auth-bench Red-Team | 1,000 attacks | Fisher's Exact Test | 0.95 | 0.001 | Dynamic injection string randomization |
| **Core RQ4** | Continual SWE-bench + MINJA | 300 sequential tasks | Two-Way ANOVA | 0.90 | 0.05 | Latin square task order permutation |
| **Core RQ5** | Transfer Distribution Matrix | 100 pairs | ATR Ratio Bootstrap Estimation | 0.85 | 0.05 | Controlled hold-out models / task domains |
| **Core RQ6** | GAIA Level 3 & Deep SWE-bench | 150 deep tasks | Log-Rank Survival Test | 0.90 | 0.01 | Right-censoring at maximum step cutoffs |
| **Core RQ7** | IAM Integration Suite | 200 sessions | Binomial Exceedance Test | 0.95 | 0.001 | In-memory IDP mock, cryptographic key rotation |

> **Note on Statistical Power:** Power values in Table 6.1 are design-time estimates based on expected effect sizes. Formal simulation-based power curves will be generated and archived as part of pre-registration protocols.

---

## 5. Pre-Registration Commitment

Experimental protocols for each Core RQ will be pre-registered on OSF.io or a comparable open-science registry prior to data collection at each milestone phase. This pre-registration prevents post-hoc hypothesis adjustment and ensures strict reproducibility. Pre-registration records will specify:
1. Primary and null hypotheses.
2. Selected foundation models, pinned API versions, and temperature/sampling seeds.
3. Pre-defined outcome variables and binary exception thresholds.
4. Complete statistical test specifications, including handling of right-censored observations and competing risks.
5. Pre-registered kill, narrow, and proceed criteria matching the dossier roadmap gates.
