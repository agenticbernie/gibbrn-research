# FINAL_VERIFY_08 — Master Patchset

**Project:** GIBBRN Dossier V2  
**Purpose:** All required text patches, in file-by-file order, ready for application to V2 documents  
**Audit Date:** September 2026  
**Application Rule:** Apply MUST-FIX patches before writing SUBMISSION_* files. Apply SHOULD-FIX patches simultaneously. Do not apply patches unless the exact target text matches.  

---

## Patch Priority Legend

- 🔴 **MUST-FIX** (Blockers 1–4): Cannot submit without these
- 🟡 **SHOULD-FIX** (S2): Material improvement, apply with MUST-FIX patches
- 🔵 **MAY-FIX** (S1/S0): Cosmetic/methodology clarity, apply if practical

---

## File: V2_README.md

### PATCH README-01 🟡
**Target (line 69, reference to V2_02):**
```
| `V2_02_EVIDENCE_LANDSCAPE.md` | Evidence Landscape | 100% verified academic literature |
```
**Replace with:**
```
| `V2_02_EVIDENCE_LANDSCAPE.md` | Evidence Landscape | Primary-source evidence landscape; all citations subject to independent verification |
```

---

## File: V2_01_RESEARCH_THESIS.md

### PATCH 01-01 🔴 (MINJA Year)
**Target text (in reference [8]):**
```
[8] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, 2024. arXiv:2503.03704.
```
**Replace with:**
```
[8] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, 2025. arXiv:2503.03704. [Submitted March 2025; accepted NeurIPS 2025.]
```

### PATCH 01-02 🔴 (AgentErrorBench)
**Target text (in reference [9]):**
```
[9] T. Xie et al., "AgentErrorBench: Understanding Cascading Errors in Autonomous LLM Agents," arXiv:2407.01505, 2024.
```
**Replace with:**
```
[9] Zhu et al., "Where LLM Agents Fail and How They can Learn From Failures," 2025. (AgentDebug / AgentErrorBench; 200 annotated failure trajectories from ALFWorld, GAIA, and WebShop environments.) [Full arXiv ID to be confirmed at final submission.]
```

### PATCH 01-03 🟡 (SWE-agent first author)
**Target text (any in-text reference to "Jimenez et al." for SWE-agent):**
Search for: `Jimenez et al.` where it refers to SWE-agent.
**Replace with:** `Yang et al.`

And in reference [10] if present:
```
[X] C. E. Jimenez et al., "SWE-agent..."
```
**Replace with:**
```
[X] J. Yang, C. E. Jimenez, A. Wettig, K. Lieret, S. Yao, K. Narasimhan, and O. Press, "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, vol. 38, 2024. arXiv:2405.15793.
```

---

## File: V2_02_EVIDENCE_LANDSCAPE.md

### PATCH 02-01 🔴 (Self-certifying header)
**Target text (line ~7):**
```
**Evidence Standard: 100% Verified Primary Literature (Zero Hallucinated Citations)**
```
**Replace with:**
```
**Evidence Standard: All externally checkable claims are supported by cited primary sources. Citations should be independently verified. Epistemic classifications follow this key: Established Evidence | Emerging Evidence | GIBBRN Inference | Design Hypothesis | Engineering Target.**
```

### PATCH 02-02 🔴 (MINJA year — all occurrences in V2_02)
**Find:** Any instance of `Dong et al., NeurIPS 2024` or `(NeurIPS 2024)` referring to MINJA.
**Replace:** `Dong et al., NeurIPS 2025` / `(NeurIPS 2025)`

Apply same correction to reference block entry for Dong et al.

### PATCH 02-03 🔴 (AgentErrorBench citation)
**Find:** Any citation of `T. Xie et al.` or `arXiv:2407.01505` for AgentErrorBench.
**Replace with:** `Zhu et al. (2025)` and the corrected citation text from PATCH 01-02.

### PATCH 02-04 🔴 (27.4 percentage points claim)
**Target text (section 2.1):**
```
Jimenez et al. (NeurIPS 2024) and Xia et al. (2024) prove that runtime scaffolding, prompt interface design, and tool execution boundaries can alter task resolution rates by up to **27.4 percentage points** holding the underlying foundation model constant.
```
**Replace with:**
```
Research across SWE-bench evaluations (Yang et al., NeurIPS 2024; Xia et al., 2024) demonstrates that different agentic scaffolding architectures yield substantially different resolution rates on the same coding benchmark with similar models — differences on the order of tens of percentage points have been observed in the literature (e.g., Agentless achieving 32% resolve on SWE-bench Lite with GPT-4o; SWE-agent achieving a different resolution profile with a custom agent-computer interface). These comparisons are not fully controlled experiments — scaffolding design, prompt engineering, and model selection co-vary. The magnitude of observed performance sensitivity motivates gibbrn's investigation of harness-level state semantics as a significant variable (labeled "harness architecture sensitivity" in this dossier; GIBBRN label).
```

### PATCH 02-05 🟡 (Harness Dominance heading)
**Target:** 
```
**Empirical Finding 2.1: Harness Dominance Effect (Causally Established)**
```
**Replace with:**
```
**Empirical Finding 2.1: Harness Architecture Sensitivity (Observed Across Literature; Causal Attribution Pre-Experimental) [GIBBRN label]**
```

### PATCH 02-06 🟡 (SWE-agent first author in-text)
**Find:** `Jimenez et al. (NeurIPS 2024)` referring to SWE-agent.
**Replace:** `Yang et al. (NeurIPS 2024; arXiv:2405.15793)`

### PATCH 02-07 🟡 (Agentless first author)
**Find:** `H. Xia et al.` or similar for Agentless arXiv:2407.01489.
**Replace:** `C. S. Xia et al.` (Chunqiu Steven Xia)

### PATCH 02-08 🟡 (OWASP "Community Draft" label)
**Find:** `Community Draft Standard, 2025–2026` in OWASP citation.
**Replace:** `Official Release v1.0, December 2025`

---

## File: V2_03_STATE_SEMANTICS_AND_TRUST_MODEL.md

### PATCH 03-01 🟡 ("Physically isolated")
**Target text (§1.3 or §4):**
```
Models may inspect $\mathcal{S}_{\text{auth}}$ to plan actions, but they are physically isolated from writing to $\mathcal{S}_{\text{auth}}$.
```
**Replace with:**
```
Models may inspect $\mathcal{S}_{\text{auth}}$ to plan actions, but they are architecturally isolated from writing to $\mathcal{S}_{\text{auth}}$ within the gibbrn control plane design. This isolation holds as long as the system is correctly implemented and deployed; it is a software architectural guarantee, not a hardware constraint.
```

---

## File: V2_04_ARCHITECTURE.md

### PATCH 04-01 🟡 (Latency table — add ENGINEERING TARGET label)
**Target text (Table 4.1 caption):**
```
### Table 4.1: Effect Gate Latency Budget (Target: $\le 15\text{ms}$ in-process; $\le 30\text{ms}$ end-to-end)
```
**Replace with:**
```
### Table 4.1: Effect Gate Latency Budget — ENGINEERING DESIGN TARGETS (Target: $\le 15\text{ms}$ in-process; $\le 30\text{ms}$ end-to-end)

> **Note:** All latency figures in this table are ENGINEERING DESIGN TARGETS established prior to experimental validation. These values are design goals informed by known Unix domain socket IPC latencies (<1ms typical for local processes) and gVisor warm-pool spawn latencies (1–15ms range in production). Actual measured performance will be reported in Gate M3 deliverables and supersedes these estimates.
```

---

## File: V2_05_SECURITY_AND_FAILURE_MODEL.md

### PATCH 05-01 🔴 (MINJA year in reference)
**Target text (reference [1] at bottom of file):**
```
[1] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, 2024. arXiv:2503.03704.
```
**Replace with:**
```
[1] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," in *Proc. Adv. Neural Inf. Process. Syst. (NeurIPS)*, 2025. arXiv:2503.03704. [Submitted March 2025; accepted NeurIPS 2025.]
```

### PATCH 05-02 🔴 (Same in §2.4 body text)
**Find:** Any `NeurIPS 2024` attribution to Dong et al. in body text of V2_05.
**Replace:** `NeurIPS 2025`

### PATCH 05-03 🟡 ("renders credential theft impossible")
**Target text (§2.1):**
```
rendering credential theft impossible regardless of the script executed.
```
**Replace with:**
```
substantially reducing the credential exfiltration surface within the scoped threat model. Within this design (isolated network namespace, mount-table remapping of host credential paths, no physical host access), gVisor seccomp filters prevent access to host credential directories even if the agent is authorized to run bash commands. This does not eliminate all risks; host kernel compromise or supply-chain-compromised container tooling remain residual threats outside the scoped model.
```

### PATCH 05-04 🟡 ("physically incapable")
**Target text (§2.2):**
```
The foundation model is physically incapable of writing to Authoritative State ($\mathcal{S}_{\text{auth}}$).
```
**Replace with:**
```
The foundation model is architecturally isolated from writing to Authoritative State ($\mathcal{S}_{\text{auth}}$) within the gibbrn control plane design. The model process communicates exclusively via the Effect Gate IPC boundary; write access to the Authority Reducer is not exposed at the API surface level. This guarantee depends on correct implementation and deployment configuration.
```

---

## File: V2_06_CORE_RESEARCH_PROGRAM.md

### PATCH 06-01 🔴 (AgentErrorBench citation in Table 6.1 and §3 RQ2)
**Find:** Any reference to `T. Xie et al.`, `arXiv:2407.01505`, or `AgentErrorBench (2024)` for this benchmark.
**Replace with:** `Zhu et al. (2025) AgentErrorBench — 200 annotated failure trajectories from ALFWorld, GAIA, and WebShop`

### PATCH 06-02 🟡 (UER threshold consistency)
**Target text in §3 Core RQ3 failure threshold:**
```
Any observed unauthorized mutating action ($\text{UER} > 0.000$ in $N=1,000$)
```
This is inconsistent with the stated UER ≤ 0.001 hypothesis. Add clarity:
**Replace with:**
```
Gate M9 PASS criterion: $\text{UER} = 0.000$ (zero observed unauthorized mutations in $N=1,000$ adversarial trajectories). A single unauthorized execution ($\text{UER} = 0.001$) triggers the Narrow/Pivot decision; $\text{UER} > 0.001$ triggers KILL.
```

### PATCH 06-03 🟡 (Model name — RQ1)
**Target:**
```
**Model Tier:** Tier 2 Frontier Coding Model (e.g., Claude 3.5 Sonnet).
```
**Replace with:**
```
**Model Tier:** Tier 2 Frontier Coding Model (e.g., leading Anthropic coding model at experiment start; specific version frozen at M1 to ensure reproducibility).
```

### PATCH 06-04 🔵 (KM censoring transparency note — add to §2)
After the KM estimator equation, add:

```
**Censoring Assumption:** Successful task completions are treated as right-censored observations. This assumes censoring is independent of the failure hazard (non-informative censoring). A competing-risks sensitivity analysis (Fine-Gray sub-distribution hazard model) will be pre-registered as a secondary analysis at Gate M12 to assess robustness of survival estimates when task success is treated as a competing event.
```

### PATCH 06-05 🔵 (Pre-registration statement — add to §4 or new §5)
Add at end of V2_06:
```
## 5. Pre-Registration Commitment

Experimental protocols for each Core RQ will be pre-registered on OSF.io or a comparable open science repository prior to data collection at each phase, to prevent post-hoc hypothesis adjustment. Pre-registration will specify: primary hypothesis, null hypothesis, statistical test, sample size, acceptance threshold, and censoring conventions.
```

---

## File: V2_07_18_MONTH_ROADMAP.md

### PATCH 07-01 🟡 (Model names in Phase 6)
**Target (§5):**
```
Replication across Anthropic (Claude 3.5 Sonnet) and Google (Gemini 2.0 Flash) model families.
```
**Replace with:**
```
Replication across Anthropic and Google Tier 2 frontier model families (specific versions to be frozen at Gate M16 for reproducibility). Open-source replication will use a Tier 3 open-weights model (e.g., Llama-family 70B-scale model, version frozen at M16).
```

---

## File: V2_08_CAPITAL_PLAN.md

### PATCH 08-01 🟡 (Budget assumption labels in Table 8.1)
**Target:** Table 8.1 title or caption.
**Add after table title:**
```
> **Note:** All figures in Table 8.1 are BUDGET ASSUMPTIONS as of September 2026. Stipend rates reflect planned compensation for a distributed research team; they are not binding commitments and are subject to adjustment based on geography, team structure, and market conditions.
```

### PATCH 08-02 🟡 (Blended token rate classification)
**Target (§3 opening):**
```
consuming 10.63B tokens at an average blended rate of $4.50 per 1M tokens
```
**Replace with:**
```
consuming an estimated 10.63B tokens at an average blended rate of approximately $4.50 per 1M tokens (BUDGET ASSUMPTION as of September 2026; this rate is sensitive to model tier selection and API pricing changes over the 18-month program)
```

---

## File: V2_09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md

### PATCH 09-01 🟡 (Mem0 "zero concept")
**Target (§2):**
```
It has zero concept of code regression testing.
```
**Replace with:**
```
Public documentation for Mem0 reviewed during this audit (accessed September 2026) does not describe native support for code regression testing or sandboxed validation before memory promotion.
```

### PATCH 09-02 🟡 (">70% of enterprise tasks")
**Target (Table 9.1, Static Pipeline row):**
```
Solves >70% of enterprise tasks today.
```
**Replace with:**
```
Covers the majority of well-specified, deterministic enterprise automation tasks (ETL, structured decision workflows, report generation). The specific coverage proportion depends on enterprise context and is not established by a primary study.
```

### PATCH 09-03 🔵 (OCAP acknowledgment — add to §2 or §3)
Add to §2 after the "gibbrn is the missing semantic glue" paragraph:

```
*Architectural Note:* Engine 2's capability-token authorization model implements principles from the object-capability (OCAP) security paradigm (Saltzer and Schroeder, 1975; Miller, 2006), applied to the LLM agent context. The novelty in gibbrn is not the OCAP principle itself — which is classical — but its application to out-of-process enforcement against probabilistic LLM cognitive emissions in an agent tool-execution context.
```

---

## File: V2_10_1517_TECHNICAL_BRIEF.md

### PATCH 10-01 🔴 (MINJA year and attribution)
**Target (§4):**
```
**Memory Poisoning:** Shen Dong et al. (NeurIPS 2024) demonstrate that MINJA memory injection attacks subvert persistent agent retrieval with $>85\%$ success.
```
**Replace with:**
```
**Memory Poisoning:** S. Dong et al. (NeurIPS 2025; arXiv:2503.03704) demonstrate that MINJA memory injection attacks achieve >85% success across evaluated configurations (EHR, e-commerce, and QA agent settings), enabling query-only persistence of malicious instructions across sessions without requiring direct memory access.
```

### PATCH 10-02 🟡 (27.4pp harness claim)
**Target (§4):**
```
**Harness Dominance:** Jimenez et al. (NeurIPS 2024) and Xia et al. (2024) prove runtime scaffolding and state boundaries swing SWE-bench performance by up to **27.4 percentage points** holding model weights constant.
```
**Replace with:**
```
**Harness Architecture Sensitivity:** Yang et al. (NeurIPS 2024; SWE-agent) and Xia et al. (2024; Agentless) demonstrate that different agentic scaffolding architectures yield substantially different resolution rates on the same coding benchmark — differences on the order of tens of percentage points have been observed across the SWE-bench literature. These comparisons are not fully controlled experiments (scaffolding, prompting, and model selection co-vary), but the scale of sensitivity motivates gibbrn's investigation of harness-level state design as a significant variable.
```

### PATCH 10-03 🔴 (Academic Remediation sentence in §2)
**Target (§2, point 4):**
```
4.  **Academic Remediation:** Audited and eliminated synthetic citations, replacing them with verified primary literature (Jie Huang et al., ICLR 2024; Shen Dong et al., NeurIPS 2024).
```
**Replace with:**
```
4.  **Academic Remediation:** Audited and corrected citations; primary citations verified against source repositories. Key corrections include: Dong et al. (MINJA) classified as NeurIPS 2025 (not 2024); AgentErrorBench attribution corrected to Zhu et al. (2025).
```

---

## File: V2_DOSSIER_CHANGELOG.md

### PATCH CHANGELOG-01 🔴 (MINJA year in any reference)
**Find:** Any `NeurIPS 2024` attribution to Dong et al. MINJA.
**Replace:** `NeurIPS 2025`

### PATCH CHANGELOG-02 🔴 (AgentErrorBench citation if present)
**Find:** Any `T. Xie et al.` or `arXiv:2407.01505` reference.
**Replace:** Zhu et al. (2025) corrected citation.

---

## File: V2_RESEARCH_DECISION_LEDGER.md

### PATCH LEDGER-01 🔴 (MINJA year if present)
**Find:** Any `NeurIPS 2024` attribution to Dong et al. MINJA.
**Replace:** `NeurIPS 2025`

### PATCH LEDGER-02 🔴 (AgentErrorBench if present)
**Find:** Any `T. Xie et al.` or `arXiv:2407.01505`.
**Replace:** Zhu et al. (2025) corrected citation.

---

## Application Checklist

- [ ] V2_README: PATCH README-01
- [ ] V2_01: PATCHes 01-01, 01-02, 01-03
- [ ] V2_02: PATCHes 02-01 through 02-08
- [ ] V2_03: PATCH 03-01
- [ ] V2_04: PATCH 04-01
- [ ] V2_05: PATCHes 05-01 through 05-04
- [ ] V2_06: PATCHes 06-01 through 06-05
- [ ] V2_07: PATCH 07-01
- [ ] V2_08: PATCHes 08-01, 08-02
- [ ] V2_09: PATCHes 09-01, 09-02, 09-03
- [ ] V2_10: PATCHes 10-01, 10-02, 10-03
- [ ] V2_DOSSIER_CHANGELOG: PATCHes CHANGELOG-01, -02
- [ ] V2_RESEARCH_DECISION_LEDGER: PATCHes LEDGER-01, -02

---

> **Agents can change. Their integrity must persist.**
