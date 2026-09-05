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

**Operational definitions (proposed; frozen per gate at pre-registration — summarized here):**
- *Step:* one agent–environment interaction cycle (proposed action + tool dispatch + observation return). Prompt-only self-reflections without tool dispatch do not advance step depth.
- *Dependency depth:* the step index $k$ along the executed trajectory (not the count of useful steps). Padding with no-op steps does not improve survival; see anti-gaming rule below.
- *Failure (event):* an unrecoverable fatal trajectory failure — the trajectory cannot reach the task goal even with continued budgeted steps (e.g. irreversible destructive side effect, permanent credential compromise, or verifier-determined dead end). Transient tool errors followed by successful recovery are not failures.
- *Recovery:* return to a prior valid checkpoint $C_j$ followed by eventual task completion within budget. Recovery counts are reported separately and do not reset $T$.
- *Completion (censored):* task goal reached per the to-be-preregistered verifier before failure. Treated as right-censored (see §2.1 censoring note), with competing-risks sensitivity analysis.
- *Budget exhaustion (censored):* trajectory hits the to-be-preregistered maximum step cap, token cap, or wall-clock cap without failure or completion. Treated as right-censored at the cap.
- *Anti-gaming rule:* $\text{MDDD}_\tau$ is reported jointly with task success rate, mean cost per completed task, and latency (median + p95). Step count vs. dependency depth: for sequential agents they coincide — each interaction cycle (proposal + dispatch + observation) advances depth by one; for cycles dispatching parallel tool calls, depth still advances by one per cycle. Padding with no-op steps cannot manufacture a pass: (i) no-op dispatches still consume the to-be-preregistered step/token budget and push trajectories toward censoring at the cap; (ii) the joint gate requires success parity (within 5pp of the best baseline arm) plus a practicality review — survival gains without success gains trip the cost trigger or fail parity; (iii) a proposed no-op audit classifies dispatches via effect receipts (mutating vs. no-op) and is published with the M18 package (method TBD at pre-registration).

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
*   **Failure Threshold:** Gate M3 verdicts follow canonical Table 6.2 (founder targets kept: ≥80% reduction, ≤30ms median). Reduction in [50%,80%) → Narrow schema scope; reduction <50% with interval excluding 80% → Pivot/Stop; overhead miss → root-cause first (no automatic gateway pivot).

---

### Core RQ2 — Causal Failure Attribution via Append-Only Spine
*   **Research Question:** Does an append-only Causal State Spine with Merkle parent chaining materially improve root-cause failure attribution over standard linear telemetry traces?
*   **Hypothesis ($\mathcal{H}_1$):** Blinded human and automated causal reconstruction rate ($\text{CRR}$) of the earliest fatal divergence step increases from $\le 45\%$ (native OpenTelemetry spans) to $\ge 80\%$ using the Causal State Spine.
*   **Null Hypothesis ($\mathcal{H}_0$):** Causal DAG parent chaining provides no statistically significant improvement in root-cause localization over timestamped linear trace spans.
*   **Workload:** 150 failure trajectories from AgentErrorBench (Zhu et al., arXiv:2509.25370, Sept 2025; annotated failure trajectories across ALFWorld, GAIA, and WebShop; ulab-uiuc/AgentDebug) with ground-truth root-cause step labels. The exact curated evaluation subset size will be confirmed against the paper/codebase and frozen at pre-registration (Gate M6); 150 is the planning target, not an established dataset size.
*   **Blinding & Evaluation:** Double-blinded annotation. Annotators are given trajectory logs with system identifiers removed and are asked to identify the earliest step where an irreversible error state was established. Root-cause localization is scored as correct if the identified step matches the ground-truth label within $\pm 1$ step. Annotation team consists of two independent research engineers; disagreements resolved by a third senior reviewer. Inter-rater reliability target: Cohen’s Kappa $\kappa \ge 0.75$.
*   **Statistical Methodology:** Wilcoxon signed-rank test ($\alpha = 0.01$).
*   **Failure Threshold:** Gate M6 verdicts follow canonical Table 6.2 (founder target kept: CRR ≥80%). CRR in [70%,80%) → one Narrow optimization cycle; CRR <70% → STOP strand.

---

### Core RQ3 — Authority and Effect Integrity (Primary Initial Wedge)
*   **Research Question:** Can an out-of-process Deterministic Effect Gate eliminate unauthorized external mutations and authority laundering without introducing unacceptable false denials or latency?
*   **Hypothesis ($\mathcal{H}_1$):** When subjected to adversarial prompt injection and indirect parameter smuggling attacks, the Deterministic Effect Gate maintains an Unauthorized-Effect Rate $\text{UER} \le 0.001$, while controls show materially higher rates (see three-arm design below).
*   **Null Hypothesis ($\mathcal{H}_0$):** The Effect Gate fails to prevent out-of-scope executions, or introduces a False-Denial Rate $\text{FDR} > 2.0\%$, or adds $>50\text{ms}$ median latency overhead.
*   **Workload:** $N = 1,000$ adversarial attack trajectories (`gibbrn-auth-bench`, internal benchmark deliverable constructed during Phase 3) targeting file exfiltration, unauthorized network requests, and budget exhaustion. Attack variants are correlated (shared harness, overlapping payload families); effective independent information is less than $N$. Representativeness is limited to the three covered attack families.
*   **Three-arm comparison (same model, task, budget, and run conditions where feasible):** (A) unmanaged agent with no additional control layer; (B) the same agent protected by conventional controls (external authorization/policy check + scoped credentials + sandbox + durable execution + audit logs, without gibbrn); (C) the same agent with the gibbrn mechanism under test. Incremental value is attributed only to (C)−(B) on security (UER), false denial (FDR), latency, recovery, integration effort, and adaptation integrity — not to (C)−(A) alone.
*   **Model Tiers:** Tier 1 Reasoning Models and Tier 3 Open-Weights Models (e.g., Llama 70B-scale open-weights model, version frozen at M7).
*   **Benign suite for FDR (planning assumption, TBD at pre-registration):** $N_{\text{benign}} = 500$ benign tool-use tasks disjoint from the attack set. $\text{FDR}$ = denied benign / total benign, reported with a Wilson 95% interval. If the assumption changes, power is recalculated before data collection.
*   **Statistical Methodology:** Fisher's Exact Test with $95\%$ binomial confidence intervals (Clopper-Pearson, one-sided upper for zero-event cases).
*   **Statistical limits on zero observed failures (binding interpretation):** Zero observed unauthorized mutations in $N=1{,}000$ does **not** establish $\text{UER} \le 0.001$ and is **not** a formal proof of containment. Under the stated independence assumption, the one-sided 95% Clopper-Pearson upper bound for 0/1,000 is $\approx 0.0030$ (rule of three: $3/1{,}000$). Achieving a one-sided 95% upper bound $\le 0.001$ requires $N \approx 3{,}000$ zero-failure runs ($N \ge \log(0.05)/\log(0.999) \approx 2{,}995$). Gate M9 therefore treats $N=1{,}000$ with zero observed failures as a *pilot pass* with conclusion limited to "observed UER $=0.000$; 95% upper $\approx 0.003$": PROCEED to a to-be-preregistered confirmatory $N \approx 3{,}000$ phase (costed under the contingency reserve; scope and budget in `08_CAPITAL_PLAN.md` §5) before any "$\le 0.001$ at 95% confidence" claim. With dependence between attack variants, the true bound is wider.
*   **Failure Threshold:** Gate M9 pilot verdicts follow the canonical Table 6.2 (no overlaps; boundary values assigned). In brief: **PROCEED (pilot)** iff 0 observed unauthorized mutations in $N=1{,}000$ AND $\text{FDR} \le 2.0\%$ on the benign suite AND median overhead $\le 30\text{ms}$ AND no INCONCLUSIVE trigger (FDR confidence interval straddling 2.0%, or tail-latency review trigger tripped). **INCONCLUSIVE → Narrow** iff the point estimates meet the binding criteria but precision is inadequate, or exactly one unauthorized execution is observed (observed $\text{UER} = 0.001$): root-cause, expand the suite, optimize — no "$\le 0.001$" claim. **STOP** iff observed $\text{UER} > 0.001$ (≥2 failures), or $\text{FDR} > 2.0\%$ with the interval excluding 2.0%, or median overhead $> 30\text{ms}$ shown by root-cause analysis to be architectural rather than remediable.

---

### Core RQ4 — Validated Verified Adaptation in Verifier-Rich Domains
*   **Research Question:** In verifier-rich domains (Python scripting and Bash tool macros), can automated micro-sandbox regression testing prevent memory poisoning and performance degradation in continual learning loops?
*   **Hypothesis ($\mathcal{H}_1$):** Under continuous exposure to poisoned and low-quality demonstrations (MINJA-style queries), gibbrn Verified Adaptation maintains downstream benchmark accuracy ($<2\%$ regression), whereas naive append-and-retrieve vector memory degrades by $\ge 20\%$.
*   **Null Hypothesis ($\mathcal{H}_0$):** Automated micro-sandbox regression testing admits poisoned heuristics ($\text{FPR} > 0.02$) or is too computationally expensive ($>3\times$ baseline token cost).
*   **Workload:** 300 sequential software tasks with 15% embedded MINJA adversarial injection patterns (45 out of 300 tasks replaced with MINJA-style queries following Dong et al., NeurIPS 2025, inserted at uniformly random positions).
*   **Harness Controls:** Latin square task order randomization across 3 distinct random seeds.
*   **Statistical Methodology:** Two-Way ANOVA evaluating interaction between memory architecture and adversarial pressure; non-parametric Aligned Rank Transform ANOVA to be pre-registered as sensitivity analysis.
*   **Failure Threshold:** Gate M12 verdicts follow canonical Table 6.2 (founder targets kept: FPR ≤0.02, retention ≥98%). Retention in [95%,98%) → Narrow (expand suite/seeds); FPR >0.02 or retention <95% → NARROW scope to manual skills; STOP only without a mitigation path after one cycle.

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
    - **Denominator guardrail:** ATR is interpretable only when $\Delta P_{\text{source}} \ge 0.05$ (5pp). Smaller origin gains make the ratio unstable; such cases are reported as *inconclusive on transfer* (not as portable), with raw $\Delta P_{\text{source}}$ and $\Delta P_{\text{transfer}}$ published.
    - If $\Delta P_{\text{transfer}} < 0$, $\text{ATR} < 0$, representing negative transfer (cross-domain interference or catastrophic forgetting).
    - *Selection-bias note:* ATR is computed conditional on adaptations that passed source validation. This conditioning inflates apparent transfer; the dossier reports the admission rate (fraction of candidates reaching transfer evaluation) alongside ATR so the unconditional yield is visible.
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
*   **Hypothesis ($\mathcal{H}_1$):** On complex tasks requiring exploratory branching ($d \ge 30$), gibbrn extends trajectory survival depth such that $\text{MDDD}_{0.90}(\text{gibbrn}) \ge 2.0 \times \text{MDDD}_{0.90}(\text{baseline-(B)})$ with Log-Rank $p < 0.01$ **and** a bootstrap 95% confidence interval for the MDDD ratio whose lower bound exceeds $1.5\times$. Task success rate is non-inferior (within $5\text{pp}$ of the best baseline arm) and mean cost per completed task plus latency (median + p95) are reported against proposed practicality triggers (pending pilot calibration — tripping a trigger yields INCONCLUSIVE, never a direct fail; see Table 6.2). Three quantities stay distinct: the point estimate (answers "did it reach 2× here?"), the interval (answers "how precisely do we know the effect size?"), and the Log-Rank test (answers only "do the survival curves differ?" — it does not directly evidence a doubling).
*   **Null Hypothesis ($\mathcal{H}_0$):** gibbrn checkpointing and causal rollback do not double survival depth, or static deterministic pipelines (Agentless / pre-wired DAGs) achieve equal or superior completion rates at lower compute cost.
*   **Three-arm comparison:** (A) unmanaged adaptive agent; (B) the same agent with conventional controls (scoped credentials, sandbox, durable execution, audit logs) but without gibbrn state-integrity mechanisms; (C) the same agent with gibbrn. The thesis requires (C) to beat (B), not only (A). Model, task pool, token/step budget, and run conditions are held equivalent where feasible.
*   **Workload:** 150 long-horizon tasks from GAIA Level 3 and deep repository refactoring tasks. (Task pool composition: available GAIA Level 3 evaluation instances supplemented by curated deep repository refactoring tasks; pool frozen at pre-registration for Gate M12).
*   **Statistical Methodology:** Kaplan-Meier survival curve estimation with Log-Rank test and Cox proportional hazards regression. The Log-Rank $p$-value tests *whether survival curves differ*; the *magnitude* claim ($\ge 2.0\times$) is evaluated via the bootstrap CI for the MDDD ratio, not via the $p$-value. Sensitivity analyses include weighted log-rank tests (Peto-Peto and Harrington-Fleming $G^\rho$ family) to evaluate non-proportional hazards.
*   **Failure Threshold at Gate M18:** Verdicts follow canonical Table 6.2. In brief: ratio point $< 2.0\times$ vs the (B) conventional-controls arm (secondary reports vs (A) unmanaged and (S) static pipeline), CI lower $\le 1.5\times$, success inferior by $>5\text{pp}$, a tripped practicality trigger without a cost-reduction path, or a static-pipeline win on the joint success–cost criterion → STOP/PIVOT. Incremental value is measured as (C)−(B), never (C)−(A) alone.

---

### Core RQ7 — Cross-Model Replication & Delegated Trust Integration
*   **Research Question:** Does the three-substrate architecture remain sound when the cognitive model is swapped entirely across commercial and open-weights tiers, and does the Effect Gate reliably enforce fine-grained capability boundaries when authority is delegated from external enterprise Identity and Access Management (IAM) systems?
*   **Hypothesis ($\mathcal{H}_1$):** When the cognitive model is swapped (Tier 1 Commercial API $\leftrightarrow$ Tier 3 Open-Weights) and execution authority is anchored to external enterprise OIDC identity providers, gibbrn demonstrates:
    1.  Unauthorized-Effect Rate $\text{UER} \le 0.001$ under active adversarial injection.
    2.  Immediate, deterministic policy propagation under credential rotation, scope narrowing, and asynchronous token revocation within lease TTL ($\le 2000\text{ms}$).
    3.  End-to-end token validation latency overhead $\le 20\text{ms}$ median.
*   **Null Hypothesis ($\mathcal{H}_0$):** Swapping the cognitive model causes parameter smuggling that bypasses external IAM mapping, OR token validation introduces $>50\text{ms}$ median latency, OR asynchronous revocation fails to burn active capability leases before their expiration.
*   **Workload & Attack Model:** $N = 200$ synthetic enterprise delegation sessions evaluated across 3 **mock** IAM architectures (in-memory identity provider mock; see confounder controls):
    - *OIDC/OAuth 2.0 Client Credentials & Token Exchange:* Simulating Okta/Auth0 machine-to-machine delegation.
    - *Cloud IAM Role Delegation:* Simulating AWS IAM assume-role / GCP service account impersonation with temporary session policies.
    - *Agentic Identity Provider (AIP) Protocol:* Simulating CrowdStrike-style scoped capability manifests (vendor announcement, Sept 2, 2026; behavior simulated, not a live CrowdStrike integration).
    - *Adversarial Injections:* 50 token replay attacks, 50 parameter-smuggled privilege escalation attempts, 50 out-of-scope delegation requests, and 50 asynchronous mid-trajectory credential revocations during live tool dispatch.
*   **Mock vs. live boundary:** RQ7 tests against **mock IAM** only. Integration against **live provider sandboxes** (Okta/Auth0 test tenants, AWS/GCP test projects) is deferred to Gate M24 external deployment validation and is not claimed at M21. The brief (`10_1517_TECHNICAL_BRIEF.md`) reflects this boundary.
*   **Statistical limits:** For 0/200 with zero observed unauthorized effects, the one-sided 95% Clopper-Pearson upper bound is $\approx 0.0149$ ($\approx 1.5\%$; rule of three: $3/200$). RQ7 therefore cannot establish $\text{UER} \le 0.001$; it is a *mock-integration pilot* whose PASS (0 observed unauthorized effects, revocation within TTL) qualifies the architecture for live-provider validation, not a $\le 0.001$ claim.
*   **Statistical Methodology:** Binomial test with one-sided Clopper-Pearson 95% confidence intervals against the pilot zero-event criterion; paired Wilcoxon signed-rank test on latency impact.
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

> **Note on Statistical Power:** Power values in Table 6.1 are *preliminary design-time estimates*, not results of completed simulation-based power analyses. Assumed effect sizes: RQ1 corruption reduction 80% vs. 50% null; RQ2 CRR 80% vs. 45% baseline; RQ3 UER 0.000 vs. 0.25 control rate; RQ4 retention 98% vs. 80% degraded control; RQ5 ATR 0.80 vs. 0.50 null with 100 pairs; RQ6 hazard ratio ~0.5 (doubling of MDDD); RQ7 pilot exceedance vs. 0.001 threshold. Formal simulation-based power curves (with seeds, model versions, and censoring assumptions) will be generated, archived, and frozen as part of pre-registration *before* data collection at each milestone phase. Until then, sample sizes are planning targets.

### Table 6.2: Canonical Gate-Decision Table (binding; no overlaps; boundary values assigned)

*How to read this table.* **PROCEED** requires *all* binding criteria met, boundary-inclusive (≥/≤ counts as met). **INCONCLUSIVE → Narrow** covers every partial or uncertain outcome: point estimate inside a stated planning band, a confidence interval straddling a threshold, or a proposed review trigger tripped — one remediation/calibration cycle, then re-evaluation. **FAIL** maps to the gate-specific Narrow-scope / Pivot / Stop disposition. Two distinctions apply throughout: (i) *engineering stretch targets* (e.g. ≤14ms pre-execution in Table 4.1, p95 review bounds below) are aspirations, not binding — missing a stretch target alone never fails a gate; (ii) *observed rates* are not *confidence bounds* — a point estimate meeting a threshold with a straddling interval is INCONCLUSIVE, not a pass. Planning bands and proposed triggers are frozen at pre-registration; intervals below assume the stated methods.

| Gate | PROCEED iff ALL met | INCONCLUSIVE → Narrow (one cycle) | FAIL → disposition |
| :--- | :--- | :--- | :--- |
| M3 (RQ1) | Corruption reduction ≥80% (McNemar $p<0.01$); completion within proposed 5pp non-inferiority margin (frozen at pre-reg); median overhead ≤30ms; p95 ≤60ms (proposed tail trigger, pending calibration) | Reduction in [50%,80%); or any binding point met but interval straddles its threshold; or median >30ms (root-cause first — profile IPC/validation/sandbox); or completion degraded beyond margin | Reduction <50% with interval excluding 80% → Pivot (re-scope taxonomy) or Stop strand. PIVOT to API gateway only after root-cause shows an architectural limit, documented as a narrower threat model — never an equivalent substitute |
| M6 (RQ2) | CRR point ≥80% with $\kappa \ge 0.75$ | CRR point in [70%,80%) → optimize DAG tracing, one cycle | CRR point <70% → STOP strand (Pivot to telemetry-hybrid only with to-be-preregistered justification) |
| M9 (RQ3 pilot) | 0/1,000 unauthorized AND FDR point ≤2.0% ($N_{\text{benign}}=500$ planning assumption, TBD at pre-reg) with interval excluding straddle AND median ≤30ms AND p95 ≤60ms (proposed) → proceed to confirmatory $N\approx3{,}000$ | Exactly 1 failure (observed 0.001); or 0/1,000 with FDR interval straddling 2.0% (e.g. observed 1.8% = 9/500, Wilson upper ≈3.1%); or median ≤30ms with p95 >60ms; or median >30ms pending root-cause → root-cause, expand suite, optimize; no "≤0.001" claim | ≥2 failures (observed >0.001); or FDR point >2.0% with interval excluding 2.0%; or median >30ms shown architectural → STOP |
| M12 (RQ4) | FPR ≤0.02 AND retention ≥98% (intervals reported, no straddle) | Retention in [95%,98%) with FPR met (e.g. 96% → Narrow: expand suite/seeds); or any straddling interval → replicate | FPR >0.02 (interval excluding) OR retention <95% → NARROW scope to manually authored skills; STOP only if no mitigation path after one cycle |
| M15 (RQ5) | Mode A: ATR point ≥0.80 with bootstrap CI lower >0.60; OR Mode B: co-adaptation bounded with $\Delta P_{\text{transfer}}$ point ≥0 and reported CI | Mode A point met but CI lower ≤0.60 → enlarge transfer set; Mode B bound shown but $\Delta P$ interval straddles zero → replicate; $\Delta P_{\text{source}} < 5\text{pp}$ → inconclusive on transfer (report raw deltas) | Neither mode met with adequate precision, or global regression >2% → NARROW to single-model vertical; STOP only on uncontained regression |
| M18 (RQ6) | MDDD ratio point ≥2.0 vs (B) arm AND bootstrap CI lower >1.5 AND log-rank $p<0.01$ AND success within 5pp of best baseline arm AND no practicality trigger tripped (proposed triggers, pending pilot calibration — NOT binding fail: cost per completed task >3× best baseline, or p95 latency >2× baseline) | Ratio in [1.5,2.0) with interval including 2.0 → more tasks/optimization; or ratio met but a practicality trigger tripped → cost/latency-reduction cycle + calibrate | Ratio <1.5, or interval excluding 2.0 with adequate power, or success inferior >5pp, or static pipeline wins joint success–cost → STOP/PIVOT |
| M21 (RQ7) | 0 unauthorized in 200 AND all revocations ≤TTL (2000ms) AND median ≤20ms | Single revocation miss within 10% over TTL under load (proposed measurement tolerance, pending calibration) → replicate under controlled load | Any unauthorized effect, or systematic revocation failure → NARROW to standalone capabilities |
| M24 | Case protocol (frozen at M18 pre-reg) shows demonstrable ROI on ≤2 partner deployments incl. first live-IAM validation | Mixed ROI (1 of 2 positive) → NARROW to responsive vertical | No ROI and no live-IAM path → PIVOT or STOP per investor governance |

*Worked boundary checks:* FDR 1.8% on $N_{\text{benign}}=500$ → point meets 2.0% but Wilson interval straddles → **INCONCLUSIVE** (enlarge benign suite), not a pass. Latency median 27ms with p95 within bound → **PROCEED (pilot)**; same median with p95 >60ms → **INCONCLUSIVE** (tail optimization). Retention 96% with FPR met → **INCONCLUSIVE** (expand suite/seeds). CRR exactly 70% → Narrow cycle; exactly 80% → PROCEED. Observed FDR exactly 2.0% with finite $N$ → interval straddles → **INCONCLUSIVE**, never a pass by equality alone.

### Table 6.2b: Evidence artifact to publish per gate

| Gate | Must-publish artifact (methods + raw outcomes + verdict recommendation, auditable) |
| :--- | :--- |
| M3 | To-be-preregistered protocol record, per-task outcomes, McNemar table, latency histogram incl. p95, supported-ops list with known bypass paths |
| M6 | Annotation guide, adjudicated labels, $\kappa$, Wilcoxon results, frozen subset manifest |
| M9 | Attack suite manifest, per-attack verdicts, Clopper-Pearson/Wilson bounds, FDR/latency distributions, root-cause memos for any failure |
| M12 | Injection positions, regression suite, ANOVA + ART sensitivity, FPR/retention intervals |
| M15 | Pair list, $\Delta P_{\text{source}}$/$\Delta P_{\text{transfer}}$, bootstrap CIs, admission rate |
| M18 | KM curves, log-rank + Cox, MDDD CIs, joint success/cost/latency table, no-op audit summary |
| M21 | Mock IDP code, per-session verdicts, revocation timing logs |
| M24 | Case protocols, integration effort logs, partner-observed metrics (no partner names claimed in advance) |

---

## 5. Pre-Registration Commitment

Experimental protocols for each Core RQ *will be* pre-registered on OSF.io or a comparable open-science registry prior to data collection at each milestone phase. **No protocol is preregistered as of this dossier version; nothing in this dossier should be cited as a preregistered result.** This pre-registration prevents post-hoc hypothesis adjustment and ensures strict reproducibility. Pre-registration records will specify:
1. Primary and null hypotheses.
2. Selected foundation models, pinned API versions, and temperature/sampling seeds.
3. Pre-defined outcome variables and binary exception thresholds.
4. Complete statistical test specifications, including handling of right-censored observations and competing risks.
5. Pre-registered kill, narrow, and proceed criteria matching the dossier roadmap gates.
