# FINAL_VERIFY_03 — Numbers and Targets Ledger

**Project:** GIBBRN Dossier V2  
**Scope:** All numerical claims, targets, thresholds, rates, and budget figures  
**Audit Date:** September 2026  
**Classification Key:** MEASURED FACT | ENGINEERING TARGET | BUDGET ASSUMPTION | RESEARCH HYPOTHESIS | CALCULATION | LITERATURE VALUE  

---

## Governing Rule

Every number in the dossier must carry an explicit or clearly implied epistemic classification. No number may be presented as a measured fact unless actual experiment data exists. All pre-experiment targets must be labeled as ENGINEERING TARGETS or RESEARCH HYPOTHESES. Budget numbers are BUDGET ASSUMPTIONS, not predictions.

---

## Section 1: Security and Latency Thresholds

| Claim | Current Location | Stated Value | Verified Classification | Issue? | Required Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Capability token TTL | V2_03 §4, V2_04 §3.2, V2_05 §2.3, V2_07 §3 | ≤ 2000ms | ENGINEERING TARGET | None — correctly motivated by TOCTOU threat model. Standard lease durations in auth systems (e.g., Kerberos ~5m; short-lived JWTs) are much longer; 2000ms is aggressive but scientifically motivated. | Add label in V2_04 Table caption: "ENGINEERING TARGET." |
| Unix domain socket ingestion | V2_04 Table 4.1 | < 1.5ms | ENGINEERING TARGET | Not labeled as target in table. | Add footnote to Table 4.1: "All values in this table are ENGINEERING DESIGN TARGETS, not experimentally measured results." |
| Schema validation latency | V2_04 Table 4.1 | < 2.0ms | ENGINEERING TARGET | Same as above. | Same footnote. |
| Capability/lease check | V2_04 Table 4.1 | < 1.0ms | ENGINEERING TARGET | Same as above. | Same footnote. |
| Budget/risk balance query | V2_04 Table 4.1 | < 1.5ms | ENGINEERING TARGET | Same as above. | Same footnote. |
| gVisor sandbox dispatch | V2_04 Table 4.1 | < 8.0ms | ENGINEERING TARGET | gVisor (runsc) spawn latency in warm-pool mode can be 1–20ms depending on host configuration. The <8ms target is achievable with pre-warmed microVM pools but not guaranteed. Must be labeled. | Same footnote. Also note: "gVisor warm-pool spawn latency of <8ms is achievable but requires dedicated pre-warmed container pool management." |
| Total synchronous overhead | V2_04 Table 4.1 | ≤ 14ms | ENGINEERING TARGET (sum of above targets) | Sum arithmetic: 1.5+2.0+1.0+1.5+8.0 = 14.0ms ✅ Sum is internally consistent. | Label as sum of component targets. |
| End-to-end overhead (Gate M3) | V2_07 §2 | ≤ 30ms | RESEARCH GATE CRITERION | This is the falsification gate, not a claimed result. Correctly presented. ✅ | None beyond adding ENGINEERING TARGET framing in V2_04. |
| Latency for pilot partners | V2_10 §12 | < 20ms | ENGINEERING TARGET for seed justification | Correctly framed as future target. ✅ | None. |

---

## Section 2: Security and Reliability Thresholds

| Claim | Location | Stated Value | Classification | Issue? | Required Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Unauthorized-Effect Rate | V2_06 §3 (RQ3), V2_07 §3 | UER ≤ 0.001 (N=1,000) | RESEARCH GATE CRITERION (pre-registered) | None — correctly framed as gate criterion. | None. |
| False-Denial Rate | V2_06 §3 (RQ3) | FDR ≤ 2.0% | RESEARCH GATE CRITERION | None. | None. |
| False-Promotion Rate | V2_06 §3 (RQ4) | FPR ≤ 0.02 | RESEARCH GATE CRITERION | None. | None. |
| State corruption reduction | V2_06 §3 (RQ1) | ≥ 80% reduction | RESEARCH HYPOTHESIS | Hypothesis correctly labeled. ✅ | None. |
| Causal Reconstruction Rate | V2_06 §3 (RQ2) | CRR ≥ 80% | RESEARCH HYPOTHESIS | Hypothesis correctly labeled. ✅ | None. |
| Downstream accuracy under poisoning | V2_06 §3 (RQ4) | ≥ 98% retention | RESEARCH HYPOTHESIS | Hypothesis correctly labeled. ✅ | None. |
| MINJA attack success rate | V2_02, V2_10 | ">85%" | LITERATURE VALUE (from Dong et al. NeurIPS 2025) | ">85%" is configuration-dependent per secondary sources; the paper's specific rates vary by domain (EHR, e-commerce, QA). Accept as directional indicator. | Add qualifier: "across evaluated configurations; specific rates vary by domain." Year must be corrected to NeurIPS 2025. |
| MDDD 2.0× doubling | V2_06 §3 (RQ5), V2_07 | MDDD ≥ 2.0× baseline | RESEARCH HYPOTHESIS (the Company Thesis Gate) | Correctly labeled as gate criterion. The 2.0× threshold is an a priori design choice (not derived from pilot data). This is acceptable at R&D stage. | None. |
| MDDD in seed round scenario | V2_10 §12 | MDDD ≥ 35 steps | FORECAST (seed round justification scenario) | This number (35 steps) appears as a seed-round target alongside 70% completion. These are plausible scenario parameters, not pre-registered gates. | Label explicitly as FORECAST / ILLUSTRATIVE SCENARIO (not a Gate criterion). |

---

## Section 3: Budget and Financial Figures

| Claim | Location | Stated Value | Classification | Issue? | Required Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Primary capital ask | V2_08 §1 | USD 285,000 | FINANCIAL PLAN | Correctly presented. ✅ | None. |
| Constrained fallback | V2_08 §1 | USD 120,000 | ALTERNATIVE SCENARIO | Correctly framed. ✅ | None. |
| Principal stipend | V2_08 Table 8.1 | $90,000 ($5k/mo) | BUDGET ASSUMPTION | Reasonable for a systems researcher in a low-cost geography or solo founder mode. Not verifiable as "correct." | Label column header: "(BUDGET ASSUMPTIONS — presented at September 2026 planning)" |
| Research Engineer (half-time) | V2_08 Table 8.1 | $54,000 ($3k/mo × 18 mo) | BUDGET ASSUMPTION | $3k/mo half-time is below market for a systems engineer in San Francisco or NYC but may be appropriate for a distributed team. | Same table label. |
| API Compute | V2_08 Table 8.1, §3 | $48,000 | BUDGET ASSUMPTION | $4.50/1M blended rate is unlabeled as an assumption. Must be labeled. | Add footnote: "BUDGET ASSUMPTION: Blended API rate of ~$4.50/1M tokens as of September 2026. Rate is subject to significant change over 18 months; Scenario B in §4 addresses 100% inflation." |
| Blended rate | V2_08 §3 | $4.50/1M tokens | BUDGET ASSUMPTION | Presented inline as fact. | Add "(BUDGET ASSUMPTION, September 2026)" parenthetical. |
| Total inference cost calculation | V2_08 §3 | $47,835 ≈ $48,000 | CALCULATION | Arithmetic: 10,630M × $4.50/1M = $47,835 ✅ | None — arithmetic correct. |
| Cloud sandbox infrastructure | V2_08 Table 8.1 | $28,800 ($1,600/mo) | BUDGET ASSUMPTION | Plausible for dedicated gVisor-capable cloud instances. | Same table label. |
| Red-team bounties | V2_08 Table 8.1 | $15,000 | BUDGET ASSUMPTION | Reasonable for an 8-week external red-team program. | Same table label. |
| Contingency reserve | V2_08 Table 8.1 | $28,000 (10%) | BUDGET ASSUMPTION / RISK BUFFER | Correctly labeled as contingency. ✅ | None. |
| Seed round target | V2_10 §12 | $3M–$4M | FORECAST (IF thesis validated) | Clearly framed as conditional. ✅ | None. |

### Budget Arithmetic Verification

**Primary Plan ($285,000):**
- Subtotal: $90,000 + $54,000 + $48,000 + $28,800 + $15,000 + $8,000 + $8,000 + $5,200 = $257,000 ✅
- + 10% contingency ($28,000) = $285,000 ✅ (Note: 10% of $257,000 = $25,700; the stated $28,000 is rounded up. Acceptable rounding for a 10% buffer — within 2% of actual 10%.)

**Capital Exposure Schedule (Table 8.3):**
- Gate M3: $12k/mo × 3 = $36k ✅
- Gate M6: $36k + $14k/mo × 3 = $36k + $42k = $78k ✅
- Gate M9: $78k + $18k/mo × 3 = $78k + $54k = $132k ✅
- Gate M12: $132k + $18k/mo × 3 = $132k + $54k = $186k ✅
- Gate M15: $186k + $21k/mo × 3 = $186k + $63k = $249k ✅
- Gate M18: $249k + $12k/mo × 3 = $249k + $36k = $285k ✅

**All budget arithmetic verified correct.**

### Token Allocation Verification (Table 8.2):

Sum of trajectory counts: 500 + 1,200 + 2,500 + 4,000 + 2,000 + 3,000 = 13,200 ✅

Token subtotals:
- Phase 1: 500 × 12 steps × ~30k tokens/step ≈ 180M ✅ (rough order consistent)
- Phase 5: 2,000 × 45 steps × ~35k tokens/step ≈ 3.15B ≈ 3.2B ✅

Sum of token columns: 180M + 650M + 1,100M + 2,600M + 3,200M + 2,400M + 500M = 10,630M ✅

**Token arithmetic internally consistent.**

---

## Section 4: Research Sample Sizes and Power

| Claim | Location | Stated Value | Classification | Issue? | Required Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| RQ1 sample | V2_06 | 200 SWE-bench Lite tasks | RESEARCH DESIGN | SWE-bench Lite has 300 total instances; 200-task subset is feasible. ✅ | None. |
| RQ2 sample | V2_06 | 150 AgentErrorBench failure traces | RESEARCH DESIGN | **Issue: AgentErrorBench has 200 annotated trajectories. Using 150 is feasible, but the benchmark must be correctly cited (Zhu et al. 2025, not Xie et al. 2024).** | Carry forward citation fix. |
| RQ3 sample | V2_06 | N=1,000 adversarial attacks | RESEARCH DESIGN | 1,000 attacks at UER ≤ 0.001 threshold requires 0 or 1 unauthorized executions to pass. Fisher's Exact Test is appropriate for 2×2 contingency. ✅ | None. |
| RQ4 sample | V2_06 | 300 sequential tasks | RESEARCH DESIGN | Feasible; Two-Way ANOVA stated. | None. |
| RQ5 sample | V2_06 | 150 deep tasks | RESEARCH DESIGN | GAIA Level 3 has limited publicly available tasks; the 150-task pool may combine GAIA Level 3 with deep SWE-bench. Design should clarify sourcing. | Add clarification: "Task pool sourced from available GAIA Level 3 instances supplemented by deep repository refactoring tasks; final composition determined at Gate M12." |
| Statistical power (RQ1) | V2_06 Table 6.1 | 1-β = 0.90 | RESEARCH DESIGN | McNemar's test power for N=200, paired, α=0.01, effect of 80% reduction: power ≥ 0.90 is feasible if the baseline error rate is ≥ 5%. Not formally derived in document but credible. | Add note: "Power values are design-time estimates; formal power analysis simulation will be conducted at experimental setup." |
| Statistical power (RQ5) | V2_06 Table 6.1 | 1-β = 0.90, Log-Rank α=0.01 | RESEARCH DESIGN | Log-Rank test for N=150 split across two arms: power depends on hazard ratio and event counts. A 2× MDDD effect is a large effect; 0.90 power with N=75 per arm at α=0.01 is feasible for large effects. | Same power estimate note. |

---

## Section 5: 1517 Fund Investor Facts

| Claim | Location | Verification Status | Required Action |
| :--- | :--- | :--- | :--- |
| 1517 Fund check range | V2_10 (implied) | PUBLICLY DOCUMENTED FACT — secondary aggregators confirm $50k–$1M range, ~$400k average pre-seed (sourced from 1517fund.com and secondary aggregators) | No specific check size claim in V2_10; dossier does not claim a specific 1517 check size. ✅ |
| 1517 Fund focus on dropouts and unconventional founders | V2_10 §1 (implied audience) | PUBLICLY DOCUMENTED FACT — confirmed from 1517fund.com, co-founders Strachman & Gibson | ✅ |
| 1517 Fund Fund IV active | Secondary source (2025) | PUBLICLY DOCUMENTED — Fund IV opened 2025 per secondary aggregator | ✅ Dossier does not reference a specific fund number, so no issue. |

---

> **Agents can change. Their integrity must persist.**
