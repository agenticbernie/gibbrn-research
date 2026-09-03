# AUDIT-03: Numerical Rigor, Benchmark Validity, and Model Lifecycle Audit

**Target Project:** GIBBRN  
**Audit Mode:** Independent Adversarial Diligence Audit (1517-Oriented Simulation)  
**Standard:** Quantitative Defensibility, Statistical Soundness, and Benchmark Operationalization  

---

## 1. Executive Numerical Audit

In early-stage systems proposals, founders often introduce precise-sounding numbers (e.g., *"<15ms latency"*, *"85% reconstruction"*, *"2.0× MDDD extension"*) to convey technical authority. 

Our audit evaluated whether every number in the GIBBRN dossier is:
- **A. Source-Derived** (backed by verifiable academic literature);
- **B. Mathematically Calculated** (reproducible with explicit formulas and inputs);
- **C. Experimental Target** (an aspirational engineering threshold to be tested);
- **D. Budget Estimate** (an operational financial assumption); or
- **E. Arbitrary Threshold** (a heuristic design choice).

---

## 2. Numerical Claim Audit Matrix

Table 3.1 itemizes and classifies the primary numerical assertions across the dossier.

### Table 3.1: Corpus Numerical Claim Verification

| Value | Dossier Location | Mathematical / Empirical Context | Strict Classification | Diligence Evaluation & Risk |
| :--- | :--- | :--- | :--- | :--- |
| **$27.4\%$** | `02_EVIDENCE` | Performance delta attributed to harness adapter design holding model constant. | **A. Source-Derived** | **VALIDATED.** Derived directly from Jimenez et al. (NeurIPS 2024) and Xia et al. (2024) on SWE-bench Lite. |
| **$>85\%$** | `02_EVIDENCE`<br>`05_THREAT` | Attack success rate of persistent memory poisoning attacks. | **A. Source-Derived** | **VALIDATED (METADATA PENDING).** Supported by Dong et al. (MINJA, NeurIPS), though dossier cited wrong author. |
| **$0.98^{50} \approx 36.4\%$** | `01_PROBLEM`<br>`02_EVIDENCE` | End-to-end success rate over 50 steps at 98% per-step accuracy. | **B. Calculated** | **MATHEMATICALLY NAIVE.** Exact arithmetic for i.i.d. Bernoulli trials, but invalid for correlated agent trajectories with recovery mechanisms. |
| **$<\!15\text{ms}$** | `03_STATE`<br>`04_SYSTEM` | Synchronous effect gate pre-execution evaluation latency. | **C. Experimental Target** | **AMBITIOUS TARGET.** Achievable for local regex/Pydantic validation, but risky if checking SQLite/PostgreSQL state over network sockets. |
| **$<\!25\text{ms}$** | `06_BENCHMARKS` | Cross-runtime median effect gate latency in LangGraph/SWE-agent. | **C. Experimental Target** | **PLAUSIBLE TARGET.** Realistic for in-process Python hooks; unverified for external sidecar microservices. |
| **$\le 30\text{ms}$** | `07_ROADMAP` | M3 Gate threshold for telemetry event capture overhead. | **C. Experimental Target** | **SOLID GATE.** Sound falsification threshold. If overhead exceeds 30ms, interactive usability is compromised. |
| **$\ge 80\%$** | `06_BENCHMARKS`<br>`07_ROADMAP` | Causal Reconstruction Rate ($\text{CRR}$) at Gate M6. | **C. Experimental Target** | **REASONABLE TARGET.** Represents a $2\times$ gain over native OpenTelemetry spans ($\sim 40\%$). |
| **$\text{UER} = 0.000$** | `06_BENCHMARKS`<br>`07_ROADMAP` | Unauthorized-Effect Rate under prompt injection. | **E. Arbitrary Threshold** | **UNFALSIFIABLE IF UNBOUNDED.** Must be bounded to registered, high-risk external tool mutations. |
| **$\text{FPR} \le 0.02$** | `06_BENCHMARKS`<br>`07_ROADMAP` | False-Promotion Rate of candidate operational skills. | **C. Experimental Target** | **MEASURABLE TARGET.** Validated via regression suite pass/fail tracking. |
| **$\ge 2.0\times$** | `06_BENCHMARKS`<br>`07_ROADMAP` | Extension of Maximum Dependable Dependency Depth ($\text{MDDD}_{0.90}$). | **C. Experimental Target** | **CRITICAL RESEARCH GOAL.** The core thesis gate of the entire company. |
| **13,200** | `08_BUDGET` | Total benchmark trajectories executed in 18 months (Target Plan). | **B. Calculated** | **REPRODUCIBLE.** Sum of M3 (500) + M6 (1,200) + M9 (2,500) + M12 (4,000) + M15 (2,000) + M18 (3,000). |
| **10.63B** | `08_BUDGET` | Total token volume modeled across 18 months. | **B. Calculated** | **REPRODUCIBLE BUT FRAGILE.** Assumes strict token limits per step (avg 18k–71k tokens/trajectory). |
| **\$48,000** | `08_BUDGET` | Total model API spend in Target Plan. | **D. Budget Estimate** | **SENSITIVE TO PRICING.** Assumes blended rate of \$4.50/1M tokens. If reasoning tokens explode, budget will overrun. |
| **\$120,000** | `08_BUDGET` | Minimum Viable Funding Plan total. | **D. Budget Estimate** | **UNDERCAPITALIZED.** \$3k/mo founder subsistence leaves zero room for health insurance or living cost shocks. |
| **\$285,000** | `08_BUDGET` | Target Funding Plan total. | **D. Budget Estimate** | **HIGHLY CREDIBLE.** Well-balanced allocation between researcher subsistence, systems engineer, compute, and cluster ops. |

---

## 3. Benchmark Operationalization Audit

A core methodology question for deep-tech diligence is: **Does the benchmark actually measure what the research question claims to test?**

Table 3.2 audits every benchmark proposed in `06_EXPERIMENT_AND_BENCHMARK_PLAN.md`.

### Table 3.2: Benchmark Suitability and Gap Analysis

| Research Question | Proposed Benchmark | What the Benchmark Actually Measures | What the RQ Claims to Test | Diligence Finding & Required Adaptation |
| :--- | :--- | :--- | :--- | :--- |
| **RQ1: State Taxonomy** | SWE-bench Lite (200 tasks) | Patch correctness on Python GitHub issues. | State serialization corruption and dictionary bugs. | **PARTIAL FIT.** SWE-bench Lite measures whether the bug was fixed, not internal state dict health. gibbrn must instrument the harness to log internal state mutation exceptions. |
| **RQ2: State Spine vs. Traces** | AgentErrorBench (150 trajectories) | Step-level root-cause annotations in failed trajectories. | Causal reconstruction accuracy ($\text{CRR}$). | **EXCELLENT FIT.** Specifically designed for root-cause error localization. Legitimate dataset. |
| **RQ3: Authority Reducer** | "Prompt Injection Red-Team Suite (100 attacks)" | Custom synthetic prompt injection dataset. | Resistance to endogenous authority laundering. | **NOVEL BENCHMARK REQUIRED.** No off-the-shelf standard exists for agent authority laundering. gibbrn must release this testbed as an open-source contribution (`gibbrn-auth-bench`). |
| **RQ4: Experience Admission** | "Continual Learning SWE Suite (300 tasks)" | Sequential task execution with memory. | Memory poisoning resistance and regression avoidance. | **MODIFIED BENCHMARK REQUIRED.** Standard SWE-bench is episodic (stateless). Testing continual memory requires chaining tasks with shared repo state. |
| **RQ5: Persistent Risk Ledger** | "Multi-Session Exfiltration Suite (50 campaigns)" | Distributed micro-actions across sessions. | Detection of lifetime-scoped resource exhaustion. | **CUSTOM SUITE REQUIRED.** Must clearly state that this is a custom synthetic simulation suite. |
| **RQ6: MDDD Extension** | GAIA Level 3 & Deep SWE-bench | Multi-modal web, file, and code assistant tasks. | Maximum Dependable Dependency Depth. | **STRONG FIT.** GAIA Level 3 contains the highest dependency depth tasks in public literature ($d > 25$). |
| **RQ7: Skill Accumulation** | Multi-Repo Maintenance (5 repos) | Recurring software maintenance across libraries. | Transferable procedural skill without fine-tuning. | **GOOD FIT.** Practical proxy for enterprise developer agent adaptation. |
| **RQ8: Cross-Runtime Portability**| LangGraph + SWE-agent $\times$ Claude + Gemini | Software repair across two frameworks and two models. | Cross-runtime abstraction overhead and latency. | **STRONG FIT.** Clean $2 \times 2$ factorial experimental design. |

---

## 4. Foundation Model Lifecycles and API Drift

The dossier names specific commercial and open models:
- **Claude 3.5 Sonnet** (Anthropic)
- **Gemini 2.0 Flash** (Google)
- **GPT-4o** (OpenAI)
- **Llama 3.3** (Meta)
- **DeepSeek R1** (DeepSeek)

### Diligence Finding on Model Dependencies:
1.  **API Version Deprecation Risk:** An 18-month research program starting in late 2026 will span well into 2028. Tying experimental baselines to specific point-releases (e.g., `claude-3-5-sonnet-20241022`) creates severe reproducibility risks, as foundation model providers routinely deprecate endpoints on 6-to-12-month cycles.
2.  **Reasoning Token Compute Blindspot:** Frontier reasoning models (e.g., OpenAI o1/o3, Gemini 2.0 Flash Thinking, DeepSeek R1) output hidden "reasoning tokens" that are billed at premium output rates. The token budget in `08_RND_BUDGET_AND_CAPITAL_PLAN.md` assumes standard input/output token ratios, underestimating reasoning token burn by up to $2.5\times$ if reasoning models are used extensively in deep trajectories.

### Remediation:
- In `06_EXPERIMENT_AND_BENCHMARK_PLAN.md` and `08_RND_BUDGET_AND_CAPITAL_PLAN.md`, shift from hard-coded model version dependencies to **standardized model capability tiers**:
  - *Tier 1 (Frontier Reasoning):* Models with internal test-time compute.
  - *Tier 2 (Frontier Multimodal/Coding):* High-speed code execution models.
  - *Tier 3 (Open-Weights Control):* Locally hosted weights (e.g., Llama 3.3 70B) to guarantee immutable 18-month experimental baselines.
