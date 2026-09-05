# 10 — 1517 Fund Investor Technical Brief (Submission)

**Project Name:** GIBBRN  
**Document Track:** Executive Investor Diligence & Systems Brief  
**Date:** September 2026 | **Verification Pass:** V3 Delta Pending Verification  
**Target:** 1517 Fund Investment Committee  
**Standard:** 12 Direct Diligence Responses (Post-Adversarial Diligence)  

---

### 1. What is gibbrn?
**gibbrn investigates Agent State Integrity for long-lived autonomous agents.** Technically, it is a proposed framework-neutral persistent control plane designed to preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous systems operate, accumulate experience, and change over time.

---

### 2. What changed after the latest research cycle and adversarial audit?
1.  **Separation of Thesis from Initial Wedge:** Broad "Agent Operating System" claims were abandoned in favor of a sharp, high-value wedge: the **Deterministic Effect Gate**.
2.  **Subsystem Consolidation (5 $\to$ 3 Engines):** Merged redundant components into three physical engines: the *Causal State Spine*, the *Deterministic Effect Gate*, and the *Verified Adaptation Engine*.
3.  **Mathematical Reformulation:** Replaced the naive geometric error compounding formula ($P = p^d$) with formal **discrete survival analysis hazard rate modeling** ($S(k) = \prod (1 - h(i))$).
4.  **Academic Remediation:** Audited and corrected citations; primary citations verified against source repositories. Key corrections include: Dong et al. (MINJA) classified as NeurIPS 2025 (not 2024); AgentErrorBench attribution corrected to Zhu et al. (2025).
5.  **Capital Ask & Scope Evolution (V3):** Expanded to **\$400,000 for a 24-month founder-led systems research program** structured across 7 Core Research Questions and 8 binding gates, reframing GIBBRN as *Integrity Infrastructure for Adaptive Agents* across three decoupled substrates (Adaptive Cognition, Execution Substrate, and Trust Substrate).

---

### 3. What is the narrow initial technical wedge?
**Deterministic Authority and Effect Integrity.** 
We are researching how an autonomous agent can change its probabilistic cognitive reasoning without silently changing what it is authorized to do in the external world. The wedge is an out-of-process reference monitor that intercepts proposed tool mutations, validating them against external cryptographic capabilities and containing execution inside ephemeral gVisor micro-sandboxes.

---

### 4. What empirical evidence supports the problem?
*   **Harness Architecture Sensitivity:** Yang et al. (NeurIPS 2024; SWE-agent) and Xia et al. (2024; Agentless) demonstrate that different agentic scaffolding architectures yield substantially different resolution rates on the same coding benchmark — differences on the order of tens of percentage points have been observed across the SWE-bench literature. These comparisons are not fully controlled experiments (scaffolding, prompting, and model selection co-vary), but the scale of sensitivity motivates gibbrn's investigation of harness-level state design as a significant variable.
*   **Reflection Instability:** Jie Huang et al. (ICLR 2024) and Valmeekam et al. (NeurIPS 2023) demonstrate that model self-reflection is non-monotonic and prone to ungrounded confirmation bias without external symbolic verification.
*   **Memory Poisoning:** S. Dong et al. (NeurIPS 2025; arXiv:2503.03704) demonstrate query-only memory injection (MINJA), reporting ~98.2% malicious-record injection and ~76.8% attack success averaged across evaluated agents and victim-target pairs (EHR, e-commerce, QA settings; configuration-dependent — not a universal rate).
*   **Harness Portability Deficit:** HarnessDev (Wu et al., arXiv:2609.01437, Sept 2026; 6 creators, 2,207 instances) finds generated harnesses lag human-engineered references on code/search while matching/exceeding on writing/ML experiments, with evolution gains shrinking on held-out tasks and exhibiting executor dependence — motivating RQ5.
*   **Who experiences this:** platform/infra engineers shipping agents with shell/API/DB access, DevOps teams managing long-horizon automation, and agent-framework maintainers handling authorization and memory lifecycle. *Problem-discovery interviews (10–15, M01–M03) are proposed to ground this characterization; no partners are pre-claimed.*

**Status and what is already done:** This dossier is a *pre-prototype research proposal*. No prototype benchmarks, measured gate results, customers, partners, or revenue are claimed. What exists is the falsifiable protocol suite (RQ1–RQ7), architecture specification, and gate criteria in this repository.

---

### 5. What remains unproven?
1.  Whether external checkpointing and rollback can achieve a statistically significant doubling of trajectory survival depth ($\text{MDDD}_{0.90} \ge 2.0\times$) on non-deterministic tasks.
2.  Whether automated regression testing for candidate skills can run fast enough ($<60\text{s}$) and cheap enough ($<3\times$ task cost) to be viable in continuous operation.
3.  Whether enterprise developers will adopt an out-of-process control daemon over ad-hoc in-process scripts.

---

### 6. Why might existing stacks be insufficient?
*   **Temporal / DBOS:** Temporal's documented model (deterministic workflow code + non-deterministic activities memoized in Event History) supports LLM-driven dynamic branching at runtime and durable recovery. What it does not by itself provide, per public documentation reviewed, is agent-specific semantic validation of why a model proposed a given side effect or whether its in-context authority was laundered.
*   **Mem0 / Letta:** Focus on semantic similarity retrieval; public documentation reviewed does not describe native support for regression testing, sandboxed validation, or provenance isolation before memory promotion, leaving direct vectors for MINJA-style memory poisoning in evaluated settings.
*   **Lakera Guard / Guardrails:** Rely on probabilistic natural-language classifiers to scan prompts and outputs, operating at the text inspection layer rather than enforcing deterministic kernel sandboxing or state constraints.

---

### 7. Why might existing stacks actually be sufficient (The Counter-Case)?
If enterprise computing rejects open-ended autonomous agent loops entirely and converges on **rigid, deterministic DAGs (the Agentless paradigm)** where models are called only for narrow, single-step extractions, static pipelines will suffice. gibbrn exists to test whether there is a valuable task territory requiring dynamic exploratory branching that static pipelines cannot solve.

---

### 8. What exactly will be tested over 24 months?
Seven causally chained research questions across rigorous benchmark trajectories:
*   *Core RQ1 (State Classification):* Testing whether 4-tier typed schemas reduce state corruption by $\ge 80\%$ on SWE-bench Lite.
*   *Core RQ2 (Causal Reconstruction):* Testing whether Merkle DAG event trees achieve $\ge 80\%$ root-cause failure attribution.
*   *Core RQ3 (Authority Integrity):* Testing whether the Deterministic Effect Gate achieves zero observed unauthorized effects across a $N=1,000$ red-team pilot (95% one-sided upper $\approx 0.003$; confirmatory $N \approx 3{,}000$ required before any "$\le 0.001$" claim), with three-arm controls (unmanaged / conventional-controls / gibbrn).
*   *Core RQ4 (Verified Adaptation):* Testing whether micro-sandbox regression testing maintains $\ge 98\%$ retention under MINJA poisoning.
*   *Core RQ5 (Adaptation Portability & Safe Specialization):* Testing whether learned skills and harness policies achieve $\text{ATR} \ge 0.80$ on cross-model transfer, or whether the Verified Adaptation Engine safely bounds domain/model-specific co-adaptation to prevent downstream regressions.
*   *Core RQ6 (Trajectory Survival):* Testing whether checkpoint rollback doubles $\text{MDDD}_{0.90}$ over unmanaged baselines on GAIA Level 3.
*   *Core RQ7 (IAM Integration):* Testing whether Trust Substrate integrity holds when bound to **mock** enterprise IAM (OIDC/OAuth, cloud role delegation, CrowdStrike-style scoped manifests simulated); live-provider validation deferred to M24.

*First experiment (Days 1–90, proposed):* minimal interceptor + overhead distribution, RQ1 paired sample, first 200-attack RQ3 pilot slice, 5–8 discovery interviews, Gate M3 evidence package. Full plan in `08_CAPITAL_PLAN.md` §8; no results claimed.*

---

### 9. What are the eight research checkpoint gates?
*   **Gate M3:** Interception overhead $\le 30\text{ms}$; state exceptions reduced by $\ge 80\%$.
*   **Gate M6:** Causal failure attribution rate $\text{CRR} \ge 80\%$.
*   **Gate M9 (Main Wedge):** Zero observed unauthorized effects across the $N=1,000$ pilot (95% upper $\approx 0.003$); false denials $\le 2.0\%$. Single failure → Narrow/Pivot; $>0.001$ or FDR breach → STOP.
*   **Gate M12:** False-Promotion Rate $\text{FPR} \le 0.02$; downstream retention $\ge 98\%$.
*   **Gate M15:** Dual-mode satisfaction on Harness Generalization (either portable transfer $\text{ATR} \ge 0.80$, or verified safe specialization bounding co-adaptation with zero downstream regressions).
*   **Gate M18 (Scientific Gate):** $\text{MDDD}_{0.90} \ge 2.0\times$ baseline ($p < 0.01$ Log-Rank test).
*   **Gate M21:** Cross-model replication and IAM integration holds bounds.
*   **Gate M24 (Company Verdict):** Design partner validation and formal proceed/pivot/stop verdict.

---

### 10. What does the requested capital buy?
**USD 400,000 over 24 months** (Budget Allocation matching Table 8.1) funds:
*   Founder / Principal Researcher proposed compensation (\$120k over 24 mo) and part-time Research Engineer / contractor contingent on funding (\$72k).
*   Model inference compute for benchmark campaigns (\$62k; planning assumptions in `08_CAPITAL_PLAN.md` §5, buffered by reserve).
*   Dedicated sandbox infrastructure, database WAL, and cloud observability (\$36k).
*   Hardware, local workstations, and tooling (\$24k).
*   External adversarial red-teaming bounties and security evaluations (\$18k; scope-limited review, not an "independent audit").
*   Legal incorporation, IP protection, and research dissemination (\$16k total: \$9k legal/IP + \$7k dissemination/travel).
*   Strategic contingency reserve buffering API price volatility and funding the M9 confirmatory phase (\$52k; 13.0%).
*   Gates are founder-proposed review points, not investor-agreed disbursement tranches; any gated release or return mechanics require a separate agreement. No capital preservation or return is promised.

---

### 11. What result kills the thesis?
*   **At M9:** If capability tokens and kernel sandboxing fail to stop unauthorized mutating effects ($\text{UER} > 0.001$).
*   **At M18:** If checkpoint rollback fails to double $\text{MDDD}_{0.90}$ with $p < 0.01$.

If Gate M18 fails, **we will stop pursuing the broad company thesis and either wind down the program or pursue only a narrower direction if supported by evidence and investor governance.** We will not pivot to a generic AI wrapper.

---

### 12. What result would justify a subsequent seed round?
A subsequent institutional Seed round at M24 would become defensible if gibbrn demonstrates:
1.  The Effect Gate maintains zero observed unauthorized effects across the $N=1,000$ pilot *and* the pre-registered $N \approx 3{,}000$ confirmatory phase (one-sided 95% upper $\le 0.001$), with FDR and latency within bounds and three-arm incremental value over conventional controls.
2.  gibbrn-managed adaptive agents achieve a pre-registered, practically meaningful improvement in survival depth ($\text{MDDD}_{0.90} \ge 2.0\times$ baseline, $p < 0.01$ with bootstrap CI lower $> 1.5\times$) with success non-inferior and cost reported.
3.  Learned skills and harnesses either exhibit portable cross-model transfer ($\text{ATR} \ge 0.80$) or are verifiably constrained via safely bounded specialization without contaminating global state.
4.  External deployment evaluations (M24, up to 2 partners recruited post-M18) confirm integration effort, ROI signal, and first live-IAM validation. No partners are pre-claimed.

### Founder information still required (not stated in this dossier)
The repository does not currently document founder identity, background, commitment, location/cost basis, or relevant systems/security experience. Before outreach, the founder should supply a short founder note (who, why this thesis, why capable, time commitment). Nothing about internships, education status, or employment history should be inferred or described as "college dropout" without founder confirmation. See `11_INVESTOR_OVERVIEW.md` for the consolidated ask.

---

> **Agents can change. Their integrity must persist.**
