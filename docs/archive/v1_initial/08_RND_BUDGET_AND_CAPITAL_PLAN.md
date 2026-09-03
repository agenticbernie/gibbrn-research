# 08 — 18-Month R&D Budget and Capital Allocation Plan

**Project Name:** GIBBRN  
**Document Track:** Financial Engineering & Research Resource Allocation  
**Date:** September 2026  
**Audience:** Deep-Tech Investors, 1517 Fund Partners, Technical Founders  
**Capital Baseline:** Minimum Viable Funding Plan $\ge \$100,000$ (Structured as Three Scenarios)  

---

## 1. Capital Allocation Philosophy: Capital Tied to Experimental Gates

Traditional software startups raise capital to build sales pipelines, hire growth marketers, and establish burn-heavy operations. **gibbrn allocates every dollar to empirical experimental throughput.**

This capital plan is engineered to fund an **18-month rigorous R&D program**. Every line item is mapped directly to a specific research checkpoint (M3, M6, M9, M12, M15, M18) and justified by quantitative compute, infrastructure, and human subsistence modeling.

We present three structured funding scenarios:
1.  **Scenario A: Minimum Viable Research Plan (\$120,000)** — Lean single-researcher subsistence, shared cloud resources, highly focused benchmark execution on open-weights and targeted frontier model APIs.
2.  **Scenario B: Target Research Plan (\$285,000)** — Full-time Principal Researcher + dedicated part-time Research Systems Engineer, dedicated sandbox clusters, comprehensive red-teaming, and exhaustive benchmark sweeps across frontier models.
3.  **Scenario C: Expanded Multi-Framework Plan (\$480,000)** — Two full-time systems researchers, distributed hardware sandboxing, formal third-party security audits, and multi-cloud design-partner staging environments.

---

## 2. Itemized Financial Model Across Three Scenarios

Table 8.1 details the 18-month expenditure across the three funding plans.

### Table 8.1: Comprehensive 18-Month Expense Breakdown (USD)

| Budget Category | Scenario A: Minimum Viable Plan | Scenario B: Target Research Plan | Scenario C: Expanded Research Plan | Primary Research Milestone Supported |
| :--- | :--- | :--- | :--- | :--- |
| **Principal Researcher Subsistence** | \$54,000 (\$3,000/mo) | \$90,000 (\$5,000/mo) | \$126,000 (\$7,000/mo) | Continuous research leadership (M1–M18) |
| **Research Systems Engineer / Co-builder**| \$0 (Solo Founder) | \$54,000 (Half-time @ \$3k/mo) | \$108,000 (Full-time @ \$6k/mo) | Sidecar proxy & kernel sandboxing (M4–M18) |
| **Foundation Model API Compute** | \$24,000 | \$48,000 | \$78,000 | Benchmark sweeps for RQ1–RQ8 (M3–M18) |
| **Cloud Sandbox & Database Infrastructure**| \$14,400 (\$800/mo) | \$28,800 (\$1,600/mo) | \$45,000 (\$2,500/mo) | Docker/gVisor microVMs & Postgres WAL (M1–M18) |
| **Adversarial Red-Teaming & Security** | \$3,000 (Self-directed) | \$15,000 (External bounties) | \$30,000 (Formal 3rd-party audit) | Threat model validation (M7–M9) |
| **Developer Hardware & Tooling** | \$4,500 (Local workstation) | \$8,000 (Workstation + GPUs) | \$16,000 (Dual high-RAM dev nodes) | Local trace replay & offline testing |
| **Legal, Incorporation & IP Protection** | \$3,500 (Delaware C-Corp) | \$8,000 (C-Corp + Trademark) | \$18,000 (Provisional patent filings) | Corporate formation & asset defense |
| **Academic Dissemination & Publication** | \$1,600 (ArXiv / Open Access)| \$5,200 (NeurIPS/ICLR travel) | \$14,000 (Multiple conferences/workshops) | Peer-reviewed validation of results |
| **Contingency Reserve (10% Buffer)** | \$15,000 | \$28,000 | \$45,000 | Token price volatility & compute reruns |
| **TOTAL 18-MONTH CAPITAL REQUIREMENT** | **\$120,000** | **\$285,000** | **\$480,000** | **Complete 18-Month Program** |

---

## 3. Detailed Compute & Token Modeling

The primary operational expenditure alongside researcher subsistence is foundation model inference cost. Table 8.2 outlines the mathematical assumptions governing our API compute budget under the Target Plan (\$48,000).

### Table 8.2: Compute Volume and Cost Projection (Target Plan)

| Benchmark / Campaign | Model Tier Used | Trajectories Executed | Avg Steps per Trajectory | Total Tokens (Input + Output) | Blended Rate per 1M Tokens | Total Estimated Cost |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Phase 1: Harness Calibration (M3)** | Claude 3.5 Sonnet / Gemini 2.0 | 500 | 12 | 180M tokens | \$5.00 / 1M | \$900 |
| **Phase 2: Flight Recorder (M6)** | Claude 3.5 Sonnet / GPT-4o | 1,200 | 18 | 650M tokens | \$5.50 / 1M | \$3,575 |
| **Phase 3: Authority Red-Team (M9)** | Sonnet / Gemini / Llama 3.3 | 2,500 | 15 | 1.1B tokens | \$4.80 / 1M | \$5,280 |
| **Phase 4: Skill Admission (M12)** | Frontier Models + DeepSeek R1 | 4,000 | 22 | 2.6B tokens | \$4.50 / 1M | \$11,700 |
| **Phase 5: Long-Horizon MDDD (M15)**| Claude 3.5 Sonnet / Gemini 2.0 | 2,000 | 45 (Deep) | 3.2B tokens | \$4.50 / 1M | \$14,400 |
| **Phase 6: Multi-Runtime Final (M18)**| Cross-Model Validation Matrix | 3,000 | 25 | 2.4B tokens | \$4.20 / 1M | \$10,080 |
| **Ad-Hoc Prototyping & Debugging** | Mixed Frontier & Local Models | N/A | N/A | 500M tokens | \$4.15 / 1M | \$2,065 |
| **TOTAL INFERENCE COMPUTE** | — | **13,200 trajectories** | — | **10.63B tokens** | — | **\$48,000** |

---

## 4. Cloud Infrastructure & Sandboxing Architecture

To execute 13,200 trajectories safely, gibbrn requires isolated execution environments to prevent agent actions from contaminating the host or escaping the testbed.

### Infrastructure Allocation (\$1,600 / month in Target Plan):
1.  **Benchmarking Worker Nodes (\$900/mo):**
    - 3$\times$ Dedicated Hetzner/AWS instances (64 vCPU, 256GB RAM, NVMe storage).
    - Host running 128 concurrent isolated gVisor/Docker micro-containers executing bash, git, and python tasks.
2.  **State Spine Database Cluster (\$400/mo):**
    - Managed PostgreSQL 16 instance with read replicas and WAL streaming to test high-throughput append-only event logging.
    - DuckDB and ClickHouse local instances for high-speed Flight Recorder parquet log querying.
3.  **Telemetry and Artifact Storage (\$300/mo):**
    - 10TB S3-compatible object storage for storing raw execution traces, git diff blobs, and full container snapshots for causal replay.

---

## 5. Monthly Cash Flow Schedule (Burn Profile)

Figure 8.1 illustrates the cash burn rate across the 18-month lifecycle for the **Target Plan (\$285,000)**.

```
Monthly Burn Schedule (Target Plan: $285,000 Total)

$24k |                                               [M14-M15: MDDD Push]
     |                                                    ######
$20k |                                                    ######      [M18: Final Push]
     |                                  [M11-M12: Skills] ######           ######
$16k |                     [M8-M9: Auth]     ######       ######           ######
     |                          ######       ######       ######           ######
$12k |   [M1-M3: Harness]       ######       ######       ######           ######
     |        ######            ######       ######       ######           ######
 $8k |        ######   ######   ######       ######       ######   ######  ######
     +--------------------------------------------------------------------------------->
       M1  M2  M3   M4  M5  M6   M7  M8  M9   M10 M11 M12  M13 M14 M15  M16 M17 M18
```

*   **Months 1–6 (Foundations & Recorder):** Baseline burn of \$11,000–\$13,000/month. Focus on architecture formalization, harness engineering, and local testbed setup.
*   **Months 7–12 (Authority & Skill Admission):** Burn accelerates to \$16,000–\$18,000/month as red-teaming bounties and continuous regression testing micro-sandboxes scale up.
*   **Months 13–15 (Long-Horizon MDDD Validation):** Peak burn of \$21,000–\$23,000/month due to massive token consumption in deep 45+ step trajectories.
*   **Months 16–18 (Integration & Partner Staging):** Burn stabilizes at \$15,000–\$17,000/month focused on packaging, cross-runtime evaluation, and research dissemination.

---

## 6. Sensitivity Analysis & Capital Efficiency Safeguards

To ensure that gibbrn survives market and technical volatility, we have modeled three primary sensitivity vectors:

### Vector 1: Foundation Model API Price Drops
*   *Industry Trend:* Frontier API token prices have fallen 50–80% year-over-year.
*   *Financial Impact:* If blended token prices fall by 50% during the 18-month cycle, compute savings (\$24,000 in Target Plan) will not be extracted as profit. Instead, they will be redeployed to double the statistical sample size of RQ6 ($\text{MDDD}$ evaluation) from 2,000 to 4,000 trajectories, significantly tightening confidence intervals.

### Vector 2: Compute Inflation / Inefficient Prompts
*   *Adverse Scenario:* Prompt verbosity or agent loop thrashing increases average tokens per trajectory by $2.0\times$.
*   *Defensive Protocol:* gibbrn’s Flight Recorder tracks cost per trajectory in real time. If a benchmark run deviates $>25\%$ from expected token budgets, automatic circuit breakers pause execution. Furthermore, our 10% contingency buffer (\$28,000) fully covers compute overruns without threatening researcher subsistence.

### Vector 3: Sudden Obsolescence / Breakthrough Foundation Models
*   *Adverse Scenario:* A foundation model provider releases an integrated state-management mechanism at Month 9 that renders third-party state spines partially commoditized.
*   *Defensive Protocol:* The project triggers an immediate emergency checkpoint gate review. If the core thesis is invalidated, the unspent capital (estimated at $\sim \$150,000$) is returned to investors rather than burned on unviable development.

---

## 7. What Capital Unlocks Technically

Table 8.3 articulates the specific technical difference between funding tiers.

### Table 8.3: Technical Deliverables by Capital Tier

| Technical Capability | Minimum Plan (\$120,000) | Target Plan (\$285,000) | Expanded Plan (\$480,000) |
| :--- | :--- | :--- | :--- |
| **Research Team** | 1 Solo Researcher | 1 Lead Researcher + 0.5 Systems Eng | 2 Full-Time Senior Systems Researchers |
| **Frameworks Evaluated** | LangGraph only | LangGraph + SWE-agent / OpenHands | LangGraph, AutoGen, OpenHands, CrewAI |
| **Benchmark Sample Size** | 4,000 total trajectories | 13,200 total trajectories | 25,000 total trajectories |
| **Sandboxing Standard** | Local Docker containers | Dedicated gVisor/KVM cluster | Multi-tenant isolated bare-metal nodes |
| **Security Audit** | Internal red-teaming | External bounty program | Formal CREST/third-party penetration audit |
| **Statistical Power** | $1 - \beta = 0.80$ | $1 - \beta = 0.90$ | $1 - \beta = 0.95$ across all tests |
| **Design Partner Pilots** | Informal developer trials | 2 Formal instrumented company pilots | 5 Production enterprise deployments |
