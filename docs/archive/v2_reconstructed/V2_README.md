# GIBBRN — Agent State Integrity Layer (Dossier V2)

### 18-Month Systems Research & Prototype Program (Post-Adversarial Diligence Edition)
**Date:** September 2026  
**Status:** R&D-Stage Systems Hypothesis (Checkpoint-Gated Empirical Program)  
**Primary Capital Ask:** **USD 285,000** for 18 Months (Scientifically Credible Plan)  
**Constrained Fallback:** **USD 120,000** (Reduced-Scope Solo-Researcher Plan)  

---

> **"Agents can change. Their integrity must persist."**

---

## Executive Overview: What is GIBBRN V2?

**gibbrn investigates Agent State Integrity for long-lived autonomous agents.** 

Specifically, the project researches whether a framework-neutral control layer can preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous systems operate, accumulate experience, and change over time.

Dossier V2 reflects a complete systems reconstruction following an adversarial technical diligence audit. It formally separates the broad research thesis from the immediate pre-seed commercial wedge:

```
+-----------------------------------------------------------------------------------+
|                        GIBBRN V2 SYSTEMS ARCHITECTURE                             |
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

In Dossier V2, architectural bloat has been eliminated. The system is consolidated into **three physical engines**:

1.  **Engine 1: The Causal State Spine (Storage & Lineage Substrate)**
    - Merges State Spine and Flight Recorder into an append-only PostgreSQL / SQLite WAL ledger.
    - Manages Merkle DAG event trees, effect receipts, and checkpoint snapshots.
    - Formally separates **Hermetic Replay** (local containers) from **Open-World Causal Audit** (mutable APIs).
2.  **Engine 2: The Deterministic Effect Gate (Inline Policy & Kernel Sandbox) [PRIMARY WEDGE]**
    - Merges Authority Reducer and Effect Gate into an out-of-process daemon (Rust/Go).
    - Issues short-lived single-use capability leases (TTL $\le 2000\text{ms}$) mitigating TOCTOU race conditions.
    - Couples capability checks with **gVisor (runsc) micro-sandboxes** to neutralize parameter smuggling.
3.  **Engine 3: The Experience Admission Engine (Verifier-Rich Skill Governance)**
    - Narrowed strictly to verifier-rich domains (deterministic Python functions and Bash tool macros).
    - Enforces Git quarantine staging branches and micro-sandbox regression testing before promoting skills.

---

## Complete Dossier V2 Document Map

All 13 reconstructed V2 documents are available in this repository:

| Document | Title | Core Contribution & Focus |
| :--- | :--- | :--- |
| **[01](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_01_RESEARCH_THESIS.md)** | `V2_01_RESEARCH_THESIS.md` | Problem definition, thesis vs. initial wedge, the Agentless counter-case, and non-goals. |
| **[02](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_02_EVIDENCE_LANDSCAPE.md)** | `V2_02_EVIDENCE_LANDSCAPE.md` | 100% verified academic literature, SWE-agent vs. Agentless findings, competitive matrix. |
| **[03](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** | `V2_03_STATE_SEMANTICS_AND_TRUST_MODEL.md` | Four-Class State Taxonomy (Design Hypothesis), human trust roots, access matrix, Invariants 1–5. |
| **[04](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_04_ARCHITECTURE.md)** | `V2_04_ARCHITECTURE.md` | The Three Physical Engines (Spine, Gate, Admission), dataflow, gVisor sandboxing, latency budget. |
| **[05](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_05_SECURITY_AND_FAILURE_MODEL.md)** | `V2_05_SECURITY_AND_FAILURE_MODEL.md` | Hardened security model: parameter smuggling defenses, kernel isolation, TOCTOU leases, failure taxonomy. |
| **[06](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_06_CORE_RESEARCH_PROGRAM.md)** | `V2_06_CORE_RESEARCH_PROGRAM.md` | Five causally chained Core RQs and discrete survival hazard modeling for $\text{MDDD}_\tau$. |
| **[07](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_07_18_MONTH_ROADMAP.md)** | `V2_07_18_MONTH_ROADMAP.md` | Six checkpoint gates (M3–M18) with explicit Kill / Narrow / Pivot criteria. |
| **[08](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_08_CAPITAL_PLAN.md)** | `V2_08_CAPITAL_PLAN.md` | Primary \$285,000 budget vs. \$120,000 fallback, compute modeling, and capital-at-risk. |
| **[09](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** | `V2_09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md` | Genuine novelty vs. commoditized plumbing, competitor matrix, and platform risks. |
| **[10](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_10_1517_TECHNICAL_BRIEF.md)** | `V2_10_1517_TECHNICAL_BRIEF.md` | Executive 12-question diligence response for 1517 Fund. |
| **[Ledger](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_RESEARCH_DECISION_LEDGER.md)** | `V2_RESEARCH_DECISION_LEDGER.md` | Complete historical ADRs updated with V2 post-diligence decisions (AD-012 through AD-021). |
| **[Changelog](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_DOSSIER_CHANGELOG.md)** | `V2_DOSSIER_CHANGELOG.md` | Systematic provenance ledger documenting every V1 $\to$ V2 change with academic verification. |

---

## Recommended Reading Order

### For Deep-Tech Investors (1517 Fund Investment Committee):
1.  **[`V2_10_1517_TECHNICAL_BRIEF.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_10_1517_TECHNICAL_BRIEF.md)** — High-density 12-question diligence summary.
2.  **[`V2_01_RESEARCH_THESIS.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_01_RESEARCH_THESIS.md)** — Core problem, thesis vs. wedge, counter-case, and non-goals.
3.  **[`V2_08_CAPITAL_PLAN.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_08_CAPITAL_PLAN.md)** — \$285,000 budget model and capital-at-risk schedule.
4.  **[`V2_09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** — Competitors, defensibility, and platform risk.
5.  **[`V2_DOSSIER_CHANGELOG.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_DOSSIER_CHANGELOG.md)** — Full audit provenance and modification history.

### For Systems Researchers and Security Engineers:
1.  **[`V2_02_EVIDENCE_LANDSCAPE.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_02_EVIDENCE_LANDSCAPE.md)** — Verified literature and empirical gap analysis.
2.  **[`V2_03_STATE_SEMANTICS_AND_TRUST_MODEL.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** — Four-Class State Taxonomy and formal invariants.
3.  **[`V2_04_ARCHITECTURE.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_04_ARCHITECTURE.md)** — The Three Physical Engines and gVisor sandboxing.
4.  **[`V2_05_SECURITY_AND_FAILURE_MODEL.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_05_SECURITY_AND_FAILURE_MODEL.md)** — Hardened security architecture and threat mitigations.
5.  **[`V2_06_CORE_RESEARCH_PROGRAM.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_06_CORE_RESEARCH_PROGRAM.md)** — Core RQ1–RQ5 and discrete survival analysis for $\text{MDDD}_\tau$.
6.  **[`V2_07_18_MONTH_ROADMAP.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_07_18_MONTH_ROADMAP.md)** — Checkpoint-gated timeline and binding kill triggers.
7.  **[`V2_RESEARCH_DECISION_LEDGER.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_RESEARCH_DECISION_LEDGER.md)** — Living systems ADRs (AD-001 through AD-021).

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

## Contact & Research Inquiries

*   **Project Lead:** Principal Systems Researcher & Technical Founder, gibbrn Project
*   **Repository Track:** `github.com/agenticbernie/gibbrn`
*   **Status:** Pre-Seed R&D Phase (Active 1517 Fund Diligence Cycle)
