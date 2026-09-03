# FINAL_VERIFY_04 — Benchmark and Statistical Methods Ledger

**Project:** GIBBRN Dossier V2  
**Scope:** All benchmark claims, statistical methodology, experimental design, and metric definitions  
**Audit Date:** September 2026  

---

## Part 1: The MDDD Metric — Mathematical Audit

### 1.1 Formal Definition Review

The dossier defines MDDD as:

$$\text{MDDD}_\tau = \max \left\{ k \in \mathbb{N} \;\middle|\; \hat{S}(k) \ge \tau \right\}$$

with Kaplan-Meier estimator:

$$\hat{S}(k) = \prod_{i: t_i \le k} \left(1 - \frac{d_i}{n_i}\right)$$

**Assessment:** The definition is mathematically correct. KM estimated survival at the 90th percentile stopping depth is a valid way to define a discrete depth-to-failure metric. The "maximum dependable depth" interpretation is sensible and maps cleanly onto the practical question of "how deep can we rely on an agent before catastrophic failure?"

---

### 1.2 Kaplan-Meier Censoring Appropriateness — Material Statistical Issue

**The Core Issue:**

The dossier states (V2_06 §2):
> "$n_i$ is the number of trajectories at risk just prior to step $i$ (excluding right-censored tasks that reached goal completion or hit budget limits)."

This treats **completed tasks (success events)** as right-censored observations. This is a **statistical design choice that requires explicit justification**, because:

1. **In standard survival analysis**, right-censored observations are assumed to have the same underlying hazard as uncensored observations (non-informative censoring). A trajectory that **succeeds** at step $k$ may have fundamentally different underlying characteristics from a trajectory that survives by chance (selection bias toward robust trajectories).

2. **Task completion is more naturally a competing event** (success) that precluded observation of the failure event. This is the classic competing risks setting, not right-censoring.

3. **Budget-hit trajectories** are more defensibly right-censored: they didn't fail, they simply couldn't be observed further.

**Verdict:** The KM approach with success = right-censored is a workable first-order approximation if:
- The proportion of censored-due-to-success is documented
- Non-informative censoring is stated as an explicit assumption
- A competing risks sensitivity analysis (Fine-Gray model) is pre-registered as secondary analysis

This is a **methodology transparency issue (S1)**, not an S2 flaw, because the KM approach is common in software reliability literature with similar censoring conventions. However, a technically sophisticated reviewer will ask about it.

**Required Action:** Add to V2_06 §2, end of KM definition:

> *"**Censoring Assumption:** Successful task completions are treated as right-censored observations under the assumption that censoring is independent of the failure hazard. This is a simplifying assumption; trajectories that succeed may differ systematically from those that fail, potentially introducing selection bias. A competing-risks sensitivity analysis (Fine-Gray sub-distribution hazard model) will be pre-registered as a secondary analysis at Gate M12 to assess the robustness of survival estimates."*

---

### 1.3 Hypothesis Test: Log-Rank (Mantel-Cox) Assumptions

**Assessment:** Log-Rank test is appropriate for comparing two independent survival curves (gibbrn vs. baseline). Assumptions:
- **Independent observations:** Each trajectory is independent ✅ (by experimental design; different tasks, different runs)
- **Non-informative censoring:** As discussed above, requires explicit statement
- **Proportional hazards over time:** Log-Rank is most powerful when hazard ratio is constant over steps; if gibbrn's benefit only emerges after step 20+, the Log-Rank test may have reduced power. Recommended: also report Weighted Log-Rank tests (e.g., Peto-Peto or Harrington-Fleming) as sensitivity checks.

**Required Action:** Add to V2_06 §3 (Core RQ5):
> *"Sensitivity analyses will include weighted log-rank tests (Peto-Peto and Harrington-Fleming G-rho family) to assess robustness if the hazard ratio between treatment arms is non-proportional."*

---

### 1.4 Cox Proportional Hazards Regression

The dossier mentions "Cox proportional hazards regression" as a secondary analysis. This is appropriate for quantifying confounders (task type, model tier, trajectory depth category). **No issues.**

---

## Part 2: Core RQ Experimental Designs — Protocol Assessment

### 2.1 Core RQ1 — McNemar's Test Appropriateness

**Setup:** 200 SWE-bench Lite tasks run with both standard LangGraph dict (baseline) and gibbrn typed schema. Paired McNemar's test.

**Assessment:**
- McNemar's test is appropriate for paired binary outcomes (corrupt / not-corrupt) ✅
- N=200 provides adequate power for McNemar at α=0.01 if baseline exception rate is ≥ 5%
- **Issue:** The outcome variable "state mutation exception" may be continuous or multi-category, not purely binary. State corruption can have partial manifestations. Clarify whether the binary outcome is: (a) any serialization exception → 1; (b) task completion failure due to state → 1; (c) any detectable state inconsistency → 1.

**Required Action:** V2_06 §3 Core RQ1 — add: "The binary corruption outcome is defined as: at least one unhandled state-type violation, schema validation failure, or tool argument mismatch within a single trajectory run. Trajectories with partial state warnings but successful task completion are separately recorded."

---

### 2.2 Core RQ2 — Wilcoxon Signed-Rank + Human Blinding

**Setup:** 150 AgentErrorBench failure traces. Blinded human + automated causal reconstruction. Wilcoxon signed-rank test.

**Assessment:**
- Wilcoxon signed-rank is appropriate for paired ordinal outcomes (localization step accuracy) ✅
- Double-blinding with Cohen's Kappa ≥ 0.75 is methodologically sound ✅
- **Issue:** "Blinded human annotation" requires clarification of the blinding protocol. Annotators must not know which trace came from which tool. The annotation instruction must specify what counts as correct root-cause localization (e.g., within ±1 step of ground truth, or exact step match).

**Issue with benchmark attribution:** AgentErrorBench is attributed to "T. Xie et al., arXiv:2407.01505" — this is incorrect (see Citation Ledger). The corrected reference is Zhu et al. (2025). If the actual AgentErrorBench does contain ground-truth step labels for 200 trajectories in ALFWorld/GAIA/WebShop, this is confirmed by the Zhu et al. (2025) paper. Sample of 150 from 200 available is feasible.

**Required Action:** Fix citation. Add to V2_06 §3 Core RQ2: "Annotators are given trajectory logs with system identifiers removed and are asked to identify the earliest step where an irreversible error state was established. Root-cause localization is scored as correct if the identified step matches the ground-truth label within ±1 step."

---

### 2.3 Core RQ3 — Fisher's Exact Test for UER

**Setup:** N=1,000 adversarial attack trajectories. Fisher's Exact for 2×2 table: gibbrn vs. unmanaged. UER ≤ 0.001.

**Assessment:**
- Fisher's Exact Test is appropriate for small-count comparisons in a 2×2 contingency table ✅
- With 1,000 attack attempts: if gibbrn has 0 unauthorized executions and baseline has ~250+ (UER ≥ 0.25), Fisher's is maximally significant (p << 0.001) ✅
- **Note on UER definition:** UER ≤ 0.001 means ≤ 1 unauthorized execution in 1,000. But the gate states: "Any observed unauthorized mutating action (UER > 0.000 in N=1,000)." This is a stricter threshold than UER ≤ 0.001 — it means zero tolerance. These two thresholds are inconsistent within the same document. The gate in V2_07 must match the threshold in V2_06.

**Required Action:** Align thresholds. Recommended: "Gate M9 PASS criterion: UER = 0.000 (zero observed unauthorized mutations in N=1,000 adversarial trajectories). UER = 0.001 (1/1,000) triggers the Narrow/Pivot decision; UER > 0.001 triggers immediate KILL."

---

### 2.4 Core RQ4 — Two-Way ANOVA Design

**Setup:** 300 sequential tasks with 15% MINJA adversarial injection. Two-Way ANOVA (memory architecture × adversarial pressure).

**Assessment:**
- Two-Way ANOVA is appropriate if the outcome is continuous (downstream accuracy score) ✅
- Latin square task order randomization across 3 seeds addresses task-order confounding ✅
- **Issue:** "15% embedded MINJA adversarial injection patterns" — this proportion and the injection mechanism must be pre-specified to allow reproducibility. How are the 15% adversarial tasks identified and inserted? Are they inserted at random positions? Does the adversarial fraction stay constant at 15% throughout the sequential run?
- **Issue:** ANOVA assumes normal distribution of residuals. With binary or accuracy-bounded outcomes, this may not hold. Pre-register a non-parametric alternative (Aligned Rank Transform ANOVA).

**Required Action:** V2_06 §3 Core RQ4 — add: "Adversarial injection protocol: 15% of tasks (45 out of 300) are replaced with MINJA-style queries following the methodology of Dong et al. (NeurIPS 2025), inserted at uniformly random positions within each 300-task sequence. A non-parametric Aligned Rank Transform ANOVA will be pre-registered as sensitivity analysis."

---

### 2.5 Core RQ5 — GAIA Level 3 Availability Issue

**Setup:** 150 deep tasks from GAIA Level 3 + deep repository refactoring.

**Assessment:**
- GAIA Level 3 is the hardest tier of the GAIA benchmark (available since mid-2024). However, the publicly available evaluation set for Level 3 may contain fewer than 150 tasks total.
- The dossier notes "deep repository refactoring tasks" as supplement. The exact composition of the 150-task pool is not pre-specified in V2_06.
- **Issue:** If GAIA Level 3 has fewer publicly available test instances, the pool composition must be documented in the pre-registration.

**Required Action:** V2_06 §3 Core RQ5 — add: "Task pool composition: (a) available GAIA Level 3 evaluation instances (exact count TBD at experimental setup based on benchmark availability at Gate M12); (b) supplementary deep repository refactoring tasks from a curated internal task set if GAIA Level 3 instances are insufficient for N=75 per arm. Task pool composition will be pre-registered at Gate M12."

---

## Part 3: Benchmark Ecosystem Validity

| Benchmark | Claim | Verification Status | Issues |
| :--- | :--- | :--- | :--- |
| **SWE-bench Lite** | 200 tasks from 300 total; multi-file maintenance | ✅ SWE-bench Lite confirmed as 300 instances; 200-task subset is valid | None |
| **AgentErrorBench** | 150 failure traces; ground-truth root-cause step labels | ⚠️ Confirmed to exist (Zhu et al. 2025, 200 trajectories from ALFWorld/GAIA/WebShop). Incorrect citation must be fixed. Ground-truth step labels exist in the benchmark. | Fix citation. Confirm 150 subset feasibility from 200 available. |
| **gibbrn-auth-bench** | 1,000 adversarial attack trajectories | ℹ️ INTERNAL BENCHMARK — this is a gibbrn-constructed benchmark not yet in existence. This is an ENGINEERING DELIVERABLE (Phase 3, M7-M9). | Label clearly in V2_06 as "INTERNAL BENCHMARK DELIVERABLE: to be constructed during Phase 3." |
| **MINJA adversarial patterns** | "MINJA-style queries" in RQ4 | ⚠️ MINJA is a documented attack methodology (Dong et al. NeurIPS 2025). "MINJA-style queries" can be operationalized using the paper's methodology. | Ensure the injection methodology follows Dong et al. (NeurIPS 2025) specification exactly; cite the construction protocol. |
| **GAIA Level 3** | 150 deep tasks requiring exploratory branching | ⚠️ GAIA benchmark exists and Level 3 is the hardest tier. Exact number of publicly available Level 3 instances needs verification at Gate M12. | Acknowledge size uncertainty in pre-registration. |

---

## Part 4: Inter-Rater Reliability

The dossier requires Cohen's Kappa ≥ 0.75 for Core RQ2 human annotation.

**Assessment:** Kappa ≥ 0.75 is the "substantial agreement" threshold per Landis & Koch (1977). This is appropriate. The dossier should specify:
- Number of annotators (minimum 2 for Kappa computation; ideally 3 for majority vote)
- Qualification criteria for annotators
- Disagreement resolution protocol

**Required Action:** V2_06 §3 Core RQ2 — add: "Annotation team: two independent research engineers with distributed systems background. Disagreements resolved by a third senior reviewer. Cohen's Kappa computed between the two primary annotators pre-resolution."

---

## Part 5: Pre-Registration Commitment

The dossier proposes experimental designs but does not explicitly mention pre-registration. For submission to a research-oriented audience, stating the intent to pre-register (e.g., on OSF or arXiv) before each gate experiment is beneficial.

**Required Action:** V2_06 §4 or V2_07 §1 — add: "Experimental protocols for each Core RQ will be pre-registered on OSF.io or a comparable repository prior to data collection, to prevent post-hoc hypothesis adjustment. Pre-registration will include: hypothesis, null hypothesis, statistical test, sample size, acceptance threshold, and censoring conventions."

---

## Summary

| ID | Issue | Severity | File | Required Action |
| :--- | :--- | :--- | :--- | :--- |
| BM-01 | KM censoring: success as competing event vs. right-censored | S1 | V2_06 §2 | Add competing risks sensitivity note |
| BM-02 | Log-rank assumption of proportional hazards | S1 | V2_06 §3 (RQ5) | Add weighted log-rank sensitivity |
| BM-03 | UER threshold inconsistency (0.001 vs. 0.000) | S1 | V2_06 §3, V2_07 §3 | Align gate thresholds |
| BM-04 | MINJA injection protocol underspecified | S1 | V2_06 §3 (RQ4) | Specify injection position and randomization |
| BM-05 | GAIA Level 3 pool size uncertain | S1 | V2_06 §3 (RQ5) | Add pool composition pre-registration note |
| BM-06 | gibbrn-auth-bench is an engineering deliverable | S1 | V2_06 §3 (RQ3) | Label as "to be constructed in Phase 3" |
| BM-07 | AgentErrorBench citation error | S3 🔴 | V2_06 Table 6.1 | Fix citation (Zhu et al. 2025) |
| BM-08 | McNemar binary outcome definition underspecified | S1 | V2_06 §3 (RQ1) | Define exact binary criterion |
| BM-09 | RQ2 blinding protocol underspecified | S1 | V2_06 §3 (RQ2) | Add annotation protocol details |
| BM-10 | No pre-registration commitment stated | S1 | V2_06 §4 | Add pre-registration statement |

---

> **Agents can change. Their integrity must persist.**
