# GIBBRN — Agent State Integrity Layer (Submission)

### 18-Month Systems Research & Prototype Program (Post-Adversarial Diligence Edition)
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Status:** R&D-Stage Systems Hypothesis (Checkpoint-Gated Empirical Program)  
**Primary Capital Ask:** **USD 285,000** for 18 Months (Scientifically Credible Plan)  
**Constrained Fallback:** **USD 120,000** (Reduced-Scope Solo-Researcher Plan)  

---

> **"Agents can change. Their integrity must persist."**

---

## Executive Overview: What is GIBBRN?

**gibbrn investigates Agent State Integrity for long-lived autonomous agents.** 

Specifically, the project researches whether a framework-neutral control layer can preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous systems operate, accumulate experience, and change over time.

This dossier reflects a complete systems reconstruction following an independent 1517-oriented adversarial diligence simulation and subsequent evidence verification pass. It formally separates the broad research thesis from the immediate pre-seed commercial wedge:

```
+-----------------------------------------------------------------------------------+
|                        GIBBRN SYSTEMS ARCHITECTURE                                |
+-----------------------------------------------------------------------------------+
| BROAD RESEARCH THESIS:                                                            |
| Investigating Agent State Integrity: "Which agent state may safely remain         |
| probabilistic and model-maintained, and which state must remain canonical,        |
| deterministic, provenance-preserving, validated, versioned, and enforced?"        |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| NARROW PRE-SEED INITIAL WEDGE:                                                    |
| Deterministic Authority and Effect Integrity: "How autonomous agents can change   |
| their cognitive reasoning without silently changing what they are authorized to   |
| do in the external world."                                                        |
+-----------------------------------------------------------------------------------+
```

---

## The Three Physical Research Engines

Architectural bloat has been eliminated. The system is consolidated into **three physical engines**:

1.  **Engine 1: The Causal State Spine (Storage & Lineage Substrate)**
    - Merges State Spine and Flight Recorder into an append-only PostgreSQL / SQLite WAL ledger.
    - Manages Merkle DAG event trees, effect receipts, and checkpoint snapshots.
    - Formally separates **Hermetic Replay** (local containers) from **Open-World Causal Audit** (mutable APIs).
2.  **Engine 2: The Deterministic Effect Gate (Inline Policy & Kernel Sandbox) [PRIMARY WEDGE]**
    - Merges Authority Reducer and Effect Gate into an out-of-process daemon (Rust/Go).
    - Issues short-lived single-use capability leases (TTL $\le 2000\text{ms}$) mitigating TOCTOU race conditions.
    - Couples capability checks with **gVisor (runsc) micro-sandboxes** to constrain the blast radius of malicious or unsafe tool parameters at the OS boundary.
3.  **Engine 3: The Experience Admission Engine (Verifier-Rich Skill Governance)**
    - Narrowed strictly to verifier-rich domains (deterministic Python functions and Bash tool macros).
    - Enforces Git quarantine staging branches and micro-sandbox regression testing before promoting skills.

---

## Complete Document Map

All 13 submission-grade documents are available in this repository:

| Document | Title | Core Contribution & Focus |
| :--- | :--- | :--- |
| **[01](./01_RESEARCH_THESIS.md)** | `01_RESEARCH_THESIS.md` | Problem definition, thesis vs. initial wedge, the Agentless counter-case, and non-goals. |
| **[02](./02_EVIDENCE_LANDSCAPE.md)** | `02_EVIDENCE_LANDSCAPE.md` | Primary-source evidence landscape, SWE-bench harness sensitivity, competitive matrix. |
| **[03](./03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** | `03_STATE_SEMANTICS_AND_TRUST_MODEL.md` | Four-Class State Taxonomy (Design Hypothesis), human trust roots, access matrix, Invariants 1–5. |
| **[04](./04_ARCHITECTURE.md)** | `04_ARCHITECTURE.md` | The Three Physical Engines (Spine, Gate, Admission), dataflow, gVisor sandboxing, latency budget. |
| **[05](./05_SECURITY_AND_FAILURE_MODEL.md)** | `05_SECURITY_AND_FAILURE_MODEL.md` | Hardened security model: parameter smuggling defenses, kernel isolation, TOCTOU leases, failure taxonomy. |
| **[06](./06_CORE_RESEARCH_PROGRAM.md)** | `06_CORE_RESEARCH_PROGRAM.md` | Five causally chained Core RQs and discrete survival hazard modeling for $\text{MDDD}_\tau$. |
| **[07](./07_18_MONTH_ROADMAP.md)** | `07_18_MONTH_ROADMAP.md` | Six checkpoint gates (M3–M18) with explicit Kill / Narrow / Pivot criteria. |
| **[08](./08_CAPITAL_PLAN.md)** | `08_CAPITAL_PLAN.md` | Primary \$285,000 budget vs. \$120,000 fallback, compute modeling, and capital-at-risk. |
| **[09](./09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** | `09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md` | Genuine novelty vs. commoditized plumbing, competitor matrix, and platform risks. |
| **[10](./10_1517_TECHNICAL_BRIEF.md)** | `10_1517_TECHNICAL_BRIEF.md` | Executive 12-question diligence response for 1517 Fund. |
| **[Ledger](./RESEARCH_DECISION_LEDGER.md)** | `RESEARCH_DECISION_LEDGER.md` | Complete historical ADRs updated with post-diligence decisions (AD-012 through AD-021). |
| **[Changelog](./DOSSIER_CHANGELOG.md)** | `DOSSIER_CHANGELOG.md` | Systematic provenance ledger documenting every V1 → V2 → Submission change with academic verification. |

---

## Recommended Reading Order

### For Deep-Tech Investors (1517 Fund Investment Committee):
1.  **[`10_1517_TECHNICAL_BRIEF.md`](./10_1517_TECHNICAL_BRIEF.md)** — High-density 12-question diligence summary.
2.  **[`01_RESEARCH_THESIS.md`](./01_RESEARCH_THESIS.md)** — Core problem, thesis vs. wedge, counter-case, and non-goals.
3.  **[`08_CAPITAL_PLAN.md`](./08_CAPITAL_PLAN.md)** — \$285,000 budget model and capital-at-risk schedule.
4.  **[`09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md`](./09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** — Competitors, defensibility, and platform risk.
5.  **[`DOSSIER_CHANGELOG.md`](./DOSSIER_CHANGELOG.md)** — Full audit provenance and modification history.

### For Systems Researchers and Security Engineers:
1.  **[`02_EVIDENCE_LANDSCAPE.md`](./02_EVIDENCE_LANDSCAPE.md)** — Evidence literature and empirical gap analysis.
2.  **[`03_STATE_SEMANTICS_AND_TRUST_MODEL.md`](./03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** — Four-Class State Taxonomy and formal invariants.
3.  **[`04_ARCHITECTURE.md`](./04_ARCHITECTURE.md)** — The Three Physical Engines and gVisor sandboxing.
4.  **[`05_SECURITY_AND_FAILURE_MODEL.md`](./05_SECURITY_AND_FAILURE_MODEL.md)** — Hardened security architecture and threat mitigations.
5.  **[`06_CORE_RESEARCH_PROGRAM.md`](./06_CORE_RESEARCH_PROGRAM.md)** — Core RQ1–RQ5 and discrete survival analysis for $\text{MDDD}_\tau$.
6.  **[`07_18_MONTH_ROADMAP.md`](./07_18_MONTH_ROADMAP.md)** — Checkpoint-gated timeline and binding kill triggers.
7.  **[`RESEARCH_DECISION_LEDGER.md`](./RESEARCH_DECISION_LEDGER.md)** — Living systems ADRs (AD-001 through AD-021).

---

## The 18-Month Checkpoint Schedule

```
+---------------------------------------------------------------------------------------------------------+
| PHASE 1: M01 - M03 | Foundations & Interceptor Harness      | GATE M3: Intercept overhead <= 30ms       |
| PHASE 2: M04 - M06 | Causal State Spine & Provenance        | GATE M6: Root-cause attribution >= 80%    |
| PHASE 3: M07 - M09 | Deterministic Effect Gate (MAIN WEDGE) | GATE M9: UER <= 0.001, FDR <= 2.0%        |
| PHASE 4: M10 - M12 | Verifier-Rich Experience Admission     | GATE M12: False-promotion <= 2.0%         |
| PHASE 5: M13 - M15 | Long-Horizon Trajectory Survival       | GATE M15: MDDD >= 2.0x (Log-Rank p < 0.01)|
| PHASE 6: M16 - M18 | Replication, Staging & Final Verdict   | GATE M18: Formal Proceed / Pivot / Stop   |
+---------------------------------------------------------------------------------------------------------+
```

---

## Verification and Evidence Standard

All citations in this dossier have undergone a submission-grade evidence verification pass. Epistemic classifications used throughout:

- **Established Evidence:** Replicated finding, peer-reviewed publication
- **Emerging Evidence:** Preliminary finding, single paper, not yet independently replicated
- **GIBBRN Inference:** Reasoned from established evidence but not directly demonstrated
- **Design Hypothesis:** Proposed design to be tested; not yet implemented or measured
- **Engineering Target:** Pre-experiment latency/performance goal; actual values reported in Gate deliverables
- **Budget Assumption:** Financial projection as of September 2026; sensitive to market changes

---

## Contact & Research Inquiries

*   **Project Lead:** Principal Systems Researcher & Technical Founder, gibbrn Project
*   **Repository Track:** `github.com/agenticbernie/gibbrn`
*   **Status:** Pre-Seed R&D Phase (Active 1517 Fund Diligence Cycle)
