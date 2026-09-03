# FINAL_VERIFY_02 — Fact and Language Ledger

**Project:** GIBBRN Dossier V2  
**Scope:** All factual assertions, epistemic labels, and language tone throughout V2 corpus  
**Audit Date:** September 2026  

---

## Part A: Absolute Security and Impossibility Claims

These phrases assert physical or mathematical impossibility without sufficient scope qualification. All must be replaced with scoped, policy-level language.

### A.1 — "rendering credential theft impossible"
- **File:** V2_05 §2.1, line 44  
- **Current text:** "rendering credential theft impossible regardless of the script executed."  
- **Problem:** "Impossible" is an absolute claim. gVisor is a defense-in-depth mechanism, not a formal proof of impossibility. Sophisticated kernel exploits or gVisor escape vulnerabilities (though rare) exist. The statement also does not scope the threat model (e.g., physical hardware access, malicious host kernel, supply-chain compromised container).  
- **Epistemic Classification:** Should be: DESIGN PROPERTY WITHIN SCOPED THREAT MODEL  
- **Required fix:** "Within the scoped threat model (isolated network namespace, mount-table remapping of credential paths, no physical host access), gVisor filesystem chroot and seccomp filter configuration substantially reduces the exfiltration surface for credential paths. No security architecture eliminates all risks; host kernel compromise or container escape remains a residual threat."

---

### A.2 — "the foundation model is physically incapable of writing to Authoritative State"
- **File:** V2_05 §2.2, V2_03 §1.3  
- **Current text:** "The foundation model is physically incapable of writing to Authoritative State ($\mathcal{S}_{\text{auth}}$)."  
- **Problem:** "Physically incapable" implies hardware enforcement. The actual enforcement is **software and architectural** — the model process does not have write access to the reducer state via the system's API surface design. This can be bypassed if the implementation has bugs, or if the agent process is granted unexpected privileges.  
- **Epistemic Classification:** DESIGN INVARIANT (ARCHITECTURAL ISOLATION)  
- **Required fix:** "The foundation model is architecturally isolated from writing to Authoritative State ($\mathcal{S}_{\text{auth}}$) within the gibbrn control plane design. The model process communicates only via the Effect Gate IPC boundary; write access to the Authority Reducer is not exposed to the agent process at the API surface level. This isolation relies on correct implementation and correct deployment configuration."

---

### A.3 — "Merkle chaining... providing tamper-evident audit integrity"
- **File:** V2_05 §3, V2_03 §2 (Invariant 2)  
- **Current text:** Claims that Merkle chaining provides tamper-evidence.  
- **Assessment:** This is ACCURATE AS STATED — Merkle chaining is well-established as a tamper-detection mechanism for audit logs. The document correctly distinguishes it from access control. ✅  
- **No change required.**

---

## Part B: Self-Certifying Language

### B.1 — "Evidence Standard: 100% Verified Primary Literature (Zero Hallucinated Citations)"
- **File:** V2_02, header (line 7)  
- **Problem:** This is self-certification. No external reviewer can independently confirm "zero hallucinated citations" by reading the document alone. The audit has found that at least one citation is fabricated (AgentErrorBench / arXiv:2407.01505) and one has a year error (MINJA / NeurIPS 2024 vs. 2025). The claim is therefore factually false.  
- **Required fix:** Replace with: "Evidence Standard: All claims requiring external facts are cited with primary sources. Citations should be independently verified. Known epistemic classifications: Established Evidence, Emerging Evidence, Inference, Design Hypothesis, Engineering Target."

---

### B.2 — "100% verified academic literature" (V2_README reference to V2_02)
- **File:** V2_README, line 69  
- **Required fix:** Replace with "primary-source evidence landscape."

---

## Part C: Overstatement in Competitor Analysis

### C.1 — "It has zero concept of code regression testing" (about Mem0)
- **File:** V2_09 §2  
- **Current text:** "It has zero concept of code regression testing."  
- **Problem:** "Zero concept of" is an absolute claim based on current public documentation. Mem0 and similar systems evolve rapidly; "zero concept" implies a permanent architectural impossibility.  
- **Epistemic Classification:** DOCUMENTATION-BASED ASSESSMENT  
- **Required fix:** "Public documentation for Mem0 reviewed during this audit does not describe native support for code regression testing or sandboxed validation before memory promotion."

---

### C.2 — "Solves >70% of enterprise tasks today" (static pipeline claim)
- **File:** V2_09 §1 table  
- **Current text:** "Solves >70% of enterprise tasks today."  
- **Problem:** No primary source cited for this percentage. This is an unsourced market claim.  
- **Required fix:** Remove the percentage and replace with: "Covers the majority of well-specified, deterministic enterprise automation tasks. Estimate is not sourced from a primary study; the actual proportion depends heavily on enterprise context."

---

## Part D: Inference-Presented-as-Finding

### D.1 — "Harness Dominance Effect" as an established term
- **File:** V2_02 §2.1 heading  
- **Current text:** "**Empirical Finding 2.1: Harness Dominance Effect (Causally Established)**"  
- **Problem:** "Harness Dominance Effect" is a GIBBRN-coined label. "Causally Established" overstates the experimental basis — the 27.4pp comparison is a between-paper cross-benchmark inference, not a within-study causal experiment.  
- **Required fix:** "**Empirical Finding 2.1: Harness Architecture Sensitivity (Observed Across Literature, Causal Attribution Unconfirmed)**" and label "Harness Dominance Effect" with "(GIBBRN label)".

---

### D.2 — "proves that environment scaffolding...can alter task resolution rates by up to 27.4 percentage points"
- **File:** V2_02 §2.1, V2_10 §4  
- **Current text:** "Jimenez et al. (NeurIPS 2024) and Xia et al. (2024) prove that runtime scaffolding...can alter task resolution rates by up to 27.4 percentage points holding the underlying foundation model constant."  
- **Problem:** Neither paper makes this comparison in a single controlled experiment. "Proves" overstates a multi-paper observation where multiple variables co-vary. The 27.4pp figure appears in the SWE-bench literature as a specific resolve rate, not a harness-driven delta.  
- **Required fix:** "Research across SWE-bench evaluations (Yang et al., NeurIPS 2024; Xia et al., 2024) demonstrates that different agentic scaffolding architectures applied to the same or similar coding benchmarks with similar models yield substantially different resolution rates — differences on the order of tens of percentage points have been observed in the literature. These comparisons are not fully controlled experiments (scaffolding, prompt design, and model selection co-vary); however, the magnitude of observed differences provides practical motivation for investigating harness-level state design as a significant variable."

---

## Part E: Model Version Specificity

### E.1 — "Claude 3.5 Sonnet" and "Gemini 2.0 Flash" hard-coded in experimental design
- **Files:** V2_06 §3 (Core RQ1 model tier), V2_07 §5, V2_08 Table 8.2  
- **Current text:** Hard-codes specific model version names.  
- **Problem:** Model versioning changes over 18-month program; experimental reproducibility requires version freezing at experiment start, not at document writing time.  
- **Required fix:**  
  - V2_06 §3 Core RQ1: "Tier 2 Frontier Coding Model (e.g., leading Anthropic coding model at experiment start; version frozen at M1 to ensure reproducibility)"  
  - V2_07 §5 replication: "Cross-model replication across Anthropic and Google Tier 2 frontier model families (specific versions frozen at M16 to ensure reproducibility)"  
  - V2_08 Table 8.2 Phase 1 label: Change "Claude Sonnet" to "Tier 2 Frontier Coding Model"  
  - V2_06 §3 Core RQ3: "Tier 1 Reasoning Models and Tier 3 Open-Weights Models (e.g., Llama-family open-weights model, 70B scale)"

---

## Part F: Latency Budget Classification

### F.1 — All latency targets presented without "ENGINEERING TARGET" label
- **File:** V2_04 Table 4.1, V2_07 Gate M3, V2_09 §4  
- **Current text:** Latency numbers (e.g., $< 1.5\text{ms}$, $< 2.0\text{ms}$, $\le 14\text{ms}$, $\le 15\text{ms}$, $\le 30\text{ms}$) presented in tables without explicit classification.  
- **Problem:** These are pre-experiment design targets. Presenting them in tables without labeling them as targets vs. measurements may mislead readers into thinking they are experimentally validated.  
- **Required fix:** Add table caption or footnote to V2_04 Table 4.1: *"All latency figures in this table are ENGINEERING DESIGN TARGETS established prior to experimental validation at Gate M3. Actual measured values will be reported in Gate M3 deliverables."*  
- Same footnote for V2_07 Gate M3 latency criteria.

---

## Part G: Token Cost Classification

### G.1 — "$4.50/1M tokens blended rate" presented as a fact
- **File:** V2_08 §3  
- **Current text:** "consuming 10.63B tokens at an average blended rate of $4.50 per 1M tokens"  
- **Problem:** Token prices fluctuate significantly. Presenting a specific rate without a "as of" date or qualification implies it is a durable fact.  
- **Required fix:** "consuming an estimated 10.63B tokens at an average blended rate of approximately \$4.50 per 1M tokens (BUDGET ASSUMPTION as of September 2026; rate is sensitive to model selection and API pricing changes over the 18-month program)"

---

## Part H: Statistical Assumption Documentation

### H.1 — Kaplan-Meier right-censoring assumption for task completion
- **File:** V2_06 §2  
- **Current text:** Tasks that "reached goal completion or hit budget limits" are listed as "right-censored."  
- **Issue:** In survival analysis, right-censoring assumes the censoring is independent of the failure process. **Completed tasks** are more accurately described as "competing events" (success event precluding failure observation) than censored observations. Budget-limited tasks could be argued as censored (trajectory might have survived longer). This is a statistical design choice that should be acknowledged.  
- **Required fix:** Add a design note: *"NOTE: Trajectory goal completions are treated as right-censored observations under the conservative assumption that these trajectories' underlying failure hazard is independent of task complexity at the censoring point. An alternative treatment considers task completions as a competing event (success), requiring a cause-specific or Fine-Gray competing risks model. We have pre-registered the KM approach with log-rank testing as the primary analysis; the competing risks analysis will be conducted as a sensitivity check."*  
- This is an S1 issue — does not invalidate the design, but transparency is required.

---

## Summary Table

| Section | Issue Type | Severity | Files | Status After Patch |
| :--- | :--- | :--- | :--- | :--- |
| A.1 Credential theft "impossible" | Absolute security claim | S2 | V2_05 | Scoped language required |
| A.2 Model "physically incapable" | Wrong epistemic qualifier | S2 | V2_05, V2_03 | "Architecturally isolated" |
| B.1 "100% Verified" header | Self-certification | S2 | V2_02 | Remove |
| B.2 "100% verified" README | Self-certification | S1 | V2_README | Soften |
| C.1 Mem0 "zero concept" | Overstatement | S2 | V2_09 | Documentation caveat |
| C.2 ">70% enterprise tasks" | Unsourced market claim | S2 | V2_09 | Remove percentage |
| D.1 "Harness Dominance Effect" | Invented label as established term | S1 | V2_02 | Label as GIBBRN label |
| D.2 "proves...27.4pp" | Inference as causal fact | S3 | V2_02, V2_10 | Reframe (see VERIFY_00 BLOCKER 3) |
| E.1 Model names hard-coded | Version hygiene | S1 | V2_06, V2_07, V2_08 | Tier-based descriptions |
| F.1 Latency without target label | Fact vs. target conflation | S1 | V2_04, V2_07 | Add ENGINEERING TARGET footnote |
| G.1 Token rate as fact | Cost assumption vs. fact | S1 | V2_08 | Add BUDGET ASSUMPTION label |
| H.1 KM censoring assumption | Statistical transparency | S1 | V2_06 | Add competing risks sensitivity note |

---

> **Agents can change. Their integrity must persist.**
