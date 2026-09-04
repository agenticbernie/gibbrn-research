# 08 — Capital Allocation, Financial Engineering, and Sensitivity Plan (Submission)

**Project Name:** GIBBRN  
**Document Track:** Financial Modeling & Capital Allocation (Version 2)  
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Audience:** Deep-Tech Investors, 1517 Fund Partners, Technical Founders  
**Primary Capital Ask:** **USD 285,000 for 18 Months** (Checkpoint-Gated Empirical R&D Plan)  

---

## 1. Capital Request Overview

In response to the financial diligence audit (`AUDIT_07`), Dossier V2 clarifies its funding position. We do not present the \$150,000 and \$400,000 figures as interchangeable options.

### The Canonical Funding Request:
> **gibbrn is requesting USD 285,000 in pre-seed research capital to fund an 18-month empirical R&D program.**

*   **The Primary Plan (\$400,000):** Provides full-time founder subsistence for the Principal Systems Researcher, budget capacity for a part-time Research Systems Engineer / contractor (contingent on funding), 13,200 benchmark trajectories across frontier models (\$48,000 API compute), dedicated gVisor cloud sandboxes, external red-team bounties, and a 10% contingency buffer.
*   **The Constrained Fallback (\$150,000):** A high-risk, solo-founder survival scenario. It is preserved strictly as an extreme contingency plan, requiring severe scope reductions.

---

## 2. Itemized 18-Month Financial Breakdown

Table 8.1 details the line-item expenditures for the Primary Plan (\$400,000) alongside the Constrained Plan (\$150,000).

### Table 8.1: Audited 18-Month Expense Model (USD)

> **Note:** All figures in Table 8.1 are BUDGET ASSUMPTIONS as of September 2026. Stipend and contractor rates reflect planned compensation assumptions for a founder-led program with optional part-time research engineering support contingent on funding, and are not binding commitments.

| Expense Category | Primary Pre-Seed Plan (\$400,000) | Constrained Fallback Plan (\$150,000) | Milestone Gate Supported | What Disappears Under Constrained Plan |
| :--- | :--- | :--- | :--- | :--- |
| **Principal Systems Researcher (Founder, Full-Time)** | \$90,000 (\$5,000/mo) | \$54,000 (\$3,000/mo) | M1–M18 (Continuous) | Founder living stipend cut by 40%; creates severe personal burnout risk. |
| **Research Systems Engineer (Planned Hire / Contractor)** | \$54,000 (Half-time @ \$3k/mo) | \$0 (Solo Founder) | M4–M18 (Core Engines) | **ELIMINATED.** Founder executes all benchmark, harness, and kernel infrastructure solo. |
| **Foundation Model API Compute** | \$48,000 (13,200 trajectories) | \$24,000 (4,000 trajectories) | M3–M18 (Core RQs) | Benchmark volume cut by 70%; statistical power reduced to $1-\beta = 0.80$. |
| **Cloud Sandbox & DB Infrastructure**| \$28,800 (\$1,600/mo) | \$14,400 (\$800/mo) | M1–M18 (Continuous) | Dedicated bare-metal gVisor clusters replaced with cheap, noisy shared VMs. |
| **Adversarial Red-Teaming Bounties** | \$15,000 | \$3,000 | M7–M9 (Gate M9) | External bounty program eliminated; restricted to self-directed red-teaming. |
| **Developer Hardware & Tooling** | \$8,000 | \$4,500 | Setup & Trace Caching | Hardware refresh deferred; limited local trace storage capacity. |
| **Legal, Incorporation & Trademark** | \$8,000 | \$3,500 | Corporate Formation | Formal trademark defense and IP counsel deferred. |
| **Academic Dissemination & Travel** | \$5,200 (1 major conference) | \$1,600 (ArXiv only) | M16–M18 (Dissemination)| In-person conference presentation (NeurIPS/ICLR) eliminated; preprints only. |
| **Subtotal (Direct Research Costs)** | **\$257,000** | **\$105,000** | — | — |
| **Contingency Reserve (10%)** | \$28,000 | \$15,000 | Price Volatility Buffer | Buffer reduced, leaving zero margin for token price shocks. |
| **TOTAL CAPITAL REQUIREMENT** | **\$400,000** | **\$150,000** | **18-Month Program** | **Significant reduction in statistical rigor and systems velocity.** |

---

## 3. Detailed Token Compute Modeling (\$48,000 in Primary Plan)

The compute model recalculates token spend across 13,200 trajectories consuming an estimated 10.63B tokens at an average blended rate of approximately \$4.50 per 1M tokens (BUDGET ASSUMPTION as of September 2026; this rate is sensitive to model tier selection and API pricing changes over the 18-month program):

$$\text{Total Inference Cost} = 10,630\text{M tokens} \times \frac{\$4.50}{1\text{M tokens}} = \$47,835 \quad (\text{Budgeted at } \$48,000)$$

### Table 8.2: Milestone Token Allocation

| Research Phase | Model Tier Allocation | Trajectories | Avg Steps / Traj | Total Tokens | Blended Rate / 1M | Total Estimated Cost |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Phase 1: Interceptor Calibration (M3)** | Tier 2 (Coding: Tier 2 Frontier Coding Model) | 500 | 12 | 180M tokens | \$5.00 | \$900 |
| **Phase 2: Causal State Spine (M6)** | Tier 2 + Tier 3 (Open Weights) | 1,200 | 18 | 650M tokens | \$5.50 | \$3,575 |
| **Phase 3: Effect Gate Red-Team (M9)** | Tier 1 (Reasoning) + Tier 2 + Tier 3 | 2,500 | 15 | 1.10B tokens | \$4.80 | \$5,280 |
| **Phase 4: Experience Admission (M12)** | Tier 2 (Frontier) + Tier 1 | 4,000 | 22 | 2.60B tokens | \$4.50 | \$11,700 |
| **Phase 5: Long-Horizon Survival (M15)**| Tier 1 (Reasoning) + Tier 2 (Deep) | 2,000 | 45 (Deep) | 3.20B tokens | \$4.50 | \$14,400 |
| **Phase 6: Replication & Pilots (M18)**| Cross-Model Validation Matrix | 3,000 | 25 | 2.40B tokens | \$4.20 | \$10,080 |
| **Ad-Hoc Prototyping & Debugging** | Mixed Frontier & Local Models | — | — | 500M tokens | \$4.15 | \$2,065 |
| **TOTAL INFERENCE COMPUTE** | — | **13,200** | — | **10.63B tokens** | — | **\$48,000** |

---

## 4. Compute Sensitivity & Price Volatility Safeguards

1.  **Scenario A: Foundation Model Price Deflation (-50%):** If frontier API token prices fall by 50% (to \$2.25/1M tokens), compute spend drops to \$23,900. The \$24,000 savings will not be taken as profit; it will be automatically redeployed to expand the sample size of Core RQ5 ($\text{MDDD}$ survival analysis) from 150 to 300 deep tasks.
2.  **Scenario B: Reasoning Token Inflation (+100%):** If models generate substantial hidden internal reasoning tokens, driving effective token volume to 21.2B tokens, compute spend would rise to \$95,000. Our \$28,000 contingency buffer covers a 58% overrun. If inflation exceeds 60%, the program will shift Phase 4 regression runner micro-tests to locally hosted open-weights models (Llama 3.3 70B on our bare-metal nodes), neutralizing API costs.

---

## 5. Capital-at-Risk by Milestone Gate

Table 8.3 outlines cumulative expenditure and unspent capital preserved across each research gate.

### Table 8.3: Capital Exposure Schedule (Primary Plan: \$400,000)

| Checkpoint Gate | Cumulative Months | Monthly Burn Rate | Cumulative Capital Spent | Capital Remaining / Preserved | Falsification Trigger if Gate Fails |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Gate M3** | Months 1–3 | \$12,000 / mo | \$36,000 | **\$249,000** | Stop or materially narrow the program; preserve unspent capital subject to investor governance if interception latency $>100\text{ms}$. |
| **Gate M6** | Months 4–6 | \$14,000 / mo | \$78,000 | **\$207,000** | Narrow thesis; preserve capital if replay fails. |
| **Gate M9** | Months 7–9 | \$18,000 / mo | \$132,000 | **\$153,000** | Pivot to narrow security proxy if capability tokens leak. |
| **Gate M12** | Months 10–12 | \$18,000 / mo | \$186,000 | **\$99,000** | Defer autonomous admission if regression testing is too costly. |
| **Gate M15** | Months 13–15 | \$21,000 / mo | \$249,000 | **\$36,000** | Stop pursuing the broad company thesis; preserve remaining capital subject to governing investment terms if MDDD fails to double. |
| **Gate M18** | Months 16–18 | \$12,000 / mo | \$400,000 | **\$0** | Final Thesis Verdict (Seed Round vs. Dissolve). |
