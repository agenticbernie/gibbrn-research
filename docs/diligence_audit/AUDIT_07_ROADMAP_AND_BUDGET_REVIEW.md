# AUDIT-07: Roadmap Feasibility, Financial Audit, and Capital Scenarios

**Target Project:** GIBBRN  
**Audit Mode:** Independent Adversarial Diligence Audit (1517-Oriented Simulation)  
**Standard:** Critical Path Feasibility, Single-Point-of-Failure (SPOF) Analysis, and Financial Recalculation  

---

## 1. Executive Roadmap & Budget Verdict

The committee conducted a line-by-line recalculation of the financial model in `08_RND_BUDGET_AND_CAPITAL_PLAN.md` and an operational dependency audit of `07_18_MONTH_RND_ROADMAP.md`.

### Core Diligence Finding:
1.  **The Mathematics of the Budget are Accurate:** All itemized line items, token sums (10.63B tokens), blended rates, and contingency percentages recalculate correctly to the penny (\$120,000, \$285,000, and \$480,000).
2.  **The \$120,000 Minimum Plan is Dangerously Undercapitalized:** Relying on a solo researcher living on \$3,000/month for 18 months without health insurance or engineering support to build five distributed subsystems is an **existential single-point-of-failure (Severity S3)**.
3.  **Phase 4 (Experience Admission) is Over-Scoped for 90 Days:** Building an automated Git quarantine staging branch, micro-sandbox execution harness, and 25-task regression suite within Months 10–12 is unrealistic for a small pre-seed team alongside active benchmarking.
4.  **The \$285,000 Target Plan is the Scientifically Credible Pre-Seed Ask:** It funds a dedicated half-time Research Systems Engineer, provides adequate cloud microVM sandboxes, and protects researcher continuity.

---

## 2. Independent Financial Recalculation

Table 7.1 verifies the arithmetic across all three funding tiers.

### Table 7.1: Independent Budget Verification

| Expense Category | Scenario A (Minimum) | Scenario B (Target) | Scenario C (Expanded) | Recalculation Verification | Diligence Risk Assessment |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Principal Researcher Subsistence** | \$54,000 (\$3k/mo) | \$90,000 (\$5k/mo) | \$126,000 (\$7k/mo) | $\text{Rate} \times 18\text{ mo}$ | **S3 in Scenario A.** \$36k/year gross is below living wage in US tech hubs after self-employment tax. |
| **Research Systems Engineer** | \$0 (Solo) | \$54,000 (\$3k/mo half) | \$108,000 (\$6k/mo full) | $\text{Rate} \times 18\text{ mo}$ | **Severe bottleneck in Scenario A.** Solo builder must write all proxy, kernel, and DB code. |
| **Model API Compute** | \$24,000 | \$48,000 | \$78,000 | Verified against token model | **Sensitive to reasoning tokens.** If o1/o3 reasoning tokens are used, spend will double. |
| **Cloud Sandbox & Database** | \$14,400 (\$800/mo) | \$28,800 (\$1.6k/mo) | \$45,000 (\$2.5k/mo) | $\text{Rate} \times 18\text{ mo}$ | **Realistic.** 3 Hetzner bare-metal nodes + managed DB easily fit \$1,600/mo. |
| **Adversarial Red-Teaming** | \$3,000 | \$15,000 | \$30,000 | Lump sum allocation | **Adequate.** \$15k in Scenario B funds legitimate external hacker bounties. |
| **Developer Hardware & Tooling** | \$4,500 | \$8,000 | \$16,000 | Initial capital outlay | **Realistic.** Workstations and local trace cache disks. |
| **Legal, Incorporation & IP** | \$3,500 | \$8,000 | \$18,000 | Formation + TM | **Sufficient.** Covers Delaware C-Corp via Clerky/Stripe Atlas + baseline legal. |
| **Academic Dissemination** | \$1,600 | \$5,200 | \$14,000 | Registration + travel | **Sufficient.** Covers travel for 1 top-tier conference (NeurIPS/ICLR). |
| **Subtotal (Direct Costs)** | **\$105,000** | **\$257,000** | **\$435,000** | **Exact sum verified** | Math verified. |
| **Contingency Reserve (10%)** | \$15,000 | \$28,000 | \$45,000 | $\approx 10\% \times \text{Total}$ | **Properly structured buffer.** |
| **AUDITED CAPITAL TOTAL** | **\$120,000** | **\$285,000** | **\$480,000** | **Exact sum verified** | **All three totals are mathematically sound.** |

---

## 3. Token Compute Model Recalculation

The dossier models 13,200 trajectories across six milestones consuming 10.63B tokens at an average blended rate of \$4.50 per 1M tokens.

$$\text{Calculated Cost} = 10.63\text{B tokens} \times \frac{\$4.50}{1,000,000} = \$47,835 \quad (\text{Budgeted at } \$48,000)$$

### Diligence Stress-Test on Token Economics:
*   **Scenario A: Commodity API Price Deflation (-50%):** If blended token prices fall to \$2.25/1M tokens, compute cost drops to \$23,900, creating an immediate \$24k windfall. gibbrn should commit to redeploying this into expanding sample sizes for RQ3 and RQ6.
*   **Scenario B: Reasoning Token Inflation (+100%):** If models output 3,000 hidden reasoning tokens per step, token volume doubles to 21.2B tokens, driving compute cost to \$95,000. Under the Target Plan, the \$28,000 contingency buffer covers a 58% overrun, but a 100% overrun would require cutting Phase 6 benchmark volume.

---

## 4. Roadmap Critical Path and Hidden Dependencies

Figure 7.1 highlights the critical path and the primary scheduling bottleneck identified by the committee.

```
M01 - M03: Phase 1 (Foundations & Harness)
                  |
                  v
M04 - M06: Phase 2 (Flight Recorder & Lineage)
                  |
                  v
M07 - M09: Phase 3 (Authority Reducer & Effect Gate)
                  |
                  v  <--- [DILIGENCE BOTTLENECK: High Risk of Milestone Spillover]
M10 - M12: Phase 4 (Experience Admission & Regression Sandbox)
                  |
                  v
M13 - M15: Phase 5 (Persistent Risk Ledger & Long-Horizon MDDD)
                  |
                  v
M16 - M18: Phase 6 (Cross-Runtime Integration & Final Gate)
```

### The Phase 4 Bottleneck (Months 10–12):
Phase 4 requires building an automated regression runner that executes candidate agent skills inside micro-sandboxes (Docker/gVisor), measures performance against 25 benchmark tasks, detects regressions, and commits to a versioned Git store. 

**Diligence Critique:** For a two-person team, building a secure, multi-tenant automated CI/CD micro-sandbox that cannot be escaped by malicious candidate code is an immense infrastructure challenge that routinely takes 6 to 9 months of dedicated engineering. Attempting to complete this in 90 days alongside active benchmarking is a severe scheduling risk.

---

## 5. Scope Pruning Directive: 8 RQs $\to$ 5 Essential RQs

To eliminate scheduling risk and ensure that an 18-month program produces publishable, unassailable systems results, the committee mandates pruning the research scope from eight questions down to **five essential questions**:

```
+-----------------------------------------------------------------------------------+
|                        MANDATED RESEARCH SCOPE PRUNING                            |
+-----------------------------------------------------------------------------------+
| RETAIN AS CORE (High Value, Essential to Thesis):                                 |
| - RQ1: Four-Tier State Taxonomy Validation                                        |
| - RQ2: Causal State Spine vs. Native Traces                                       |
| - RQ3: Authority Reducer & Privilege Laundering Elimination                       |
| - RQ4: Grounded Experience Admission vs. Poisoned Memory                          |
| - RQ6: Extending Maximum Dependable Dependency Depth (MDDD)                       |
+-----------------------------------------------------------------------------------+
| DEFER / MERGE (Pruned to Save 4 Months of Engineering):                            |
| - RQ5 (Persistent Risk Ledger): Merge into RQ3 as an authority rate limit feature. |
| - RQ7 (Skill Accumulation vs. LoRA): DEFER beyond Month 18. Avoids expensive GPU  |
|   fine-tuning comparisons that distract from core systems state integrity.        |
| - RQ8 (Cross-Runtime Portability): Downgrade from a standalone scientific RQ to a |
|   software engineering integration deliverable in Phase 6.                        |
+-----------------------------------------------------------------------------------+
```

By focusing exclusively on **RQ1, RQ2, RQ3, RQ4, and RQ6**, gibbrn guarantees that the core thesis is thoroughly proved or falsified without spreading the team over peripheral fine-tuning and cross-framework benchmarks.
