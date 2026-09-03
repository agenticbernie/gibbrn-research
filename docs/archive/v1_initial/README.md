# GIBBRN — Agent State Integrity Layer for Long-Lived Autonomous Agents

### 18-Month Technical R&D Dossier for 1517 Fund & Systems Researchers
**Date:** September 2026  
**Status:** R&D-Stage Systems Hypothesis (Empirical Checkpoint-Gated Program)  
**Capital Target:** \$120,000 (Minimum) | \$285,000 (Target Pre-Seed) | \$480,000 (Expanded)  

---

> **"Agents can change. Their integrity must persist."**

---

## Executive Overview

**gibbrn** is a framework-neutral persistent control plane designed to preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous systems operate, accumulate experience, and change over time.

Contemporary agent frameworks conflate probabilistic model thoughts with canonical, authoritative system state. Over long operational horizons, this causes:
1.  **Epistemic Drift:** Hallucinated causal histories become unchallengeable facts.
2.  **Endogenous Authority Laundering:** Models escalate their own privileges via conversational self-reflection.
3.  **Compounding Dependency Collapse:** Reliability decays exponentially over multi-step dependency graphs ($P_{\text{total}} \approx p^d$).
4.  **Memory Poisoning (OWASP ASI06):** Injected untrusted data corrupts persistent behavioral guidance weeks after initial exposure.

gibbrn addresses the central systems question:
> **Which agent state may safely remain probabilistic and model-maintained, and which state must be canonical, deterministic, provenance-preserving, validated, versioned, and externally enforced?**

---

## Complete Technical Dossier Map

This repository contains the complete 11-part technical dossier engineered for early-stage deep-tech investors (such as **1517 Fund**), distributed systems researchers, and potential design partners.

| Document | Title | Core Focus |
| :--- | :--- | :--- |
| **[01](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/01_PROBLEM_AND_RESEARCH_THESIS.md)** | `01_PROBLEM_AND_RESEARCH_THESIS.md` | Problem formalization, State-Integrity thesis, non-goals, and boundary conditions. |
| **[02](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md)** | `02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md` | State of the art, SWE-agent vs. Agentless harness studies, memory poisoning, and gap analysis. |
| **[03](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/03_AGENT_STATE_MODEL_AND_INVARIANTS.md)** | `03_AGENT_STATE_MODEL_AND_INVARIANTS.md` | Mathematical 4-tier state taxonomy, access control matrix, and formal system invariants. |
| **[04](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/04_SYSTEM_ARCHITECTURE.md)** | `04_SYSTEM_ARCHITECTURE.md` | 5 core subsystems, dataflow, CQRS projections, and battle-tested substrate reuse. |
| **[05](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md)** | `05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md` | Dual failure taxonomy: Adversarial vectors (ASI06/MINJA) vs. Systemic compounding cascades. |
| **[06](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/06_EXPERIMENT_AND_BENCHMARK_PLAN.md)** | `06_EXPERIMENT_AND_BENCHMARK_PLAN.md` | Formal falsification protocols for RQ1–RQ8, MDDD metric formulas, and power analysis. |
| **[07](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/07_18_MONTH_RND_ROADMAP.md)** | `07_18_MONTH_RND_ROADMAP.md` | Checkpoint-gated milestones (M3, M6, M9, M12, M15, M18) with explicit Kill / Pivot criteria. |
| **[08](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/08_RND_BUDGET_AND_CAPITAL_PLAN.md)** | `08_RND_BUDGET_AND_CAPITAL_PLAN.md` | Itemized 18-month financial plan across 3 capital scenarios, token compute modeling, and burn schedules. |
| **[09](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/09_TECHNICAL_FOUNDER_AND_1517_CASE.md)** | `09_TECHNICAL_FOUNDER_AND_1517_CASE.md` | Strategic investment case, incumbent defensibility moats, and 1517 Fund alignment. |
| **[10](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/10_1517_TECHNICAL_BRIEF.md)** | `10_1517_TECHNICAL_BRIEF.md` | Executive 12-question diligence response for the 1517 Fund Investment Committee. |
| **[Ledger](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/RESEARCH_DECISION_LEDGER.md)** | `RESEARCH_DECISION_LEDGER.md` | Living audit log of architectural decisions: KEEP, MODIFY, DEFER, KILL entries. |

---

## Recommended Reading Order

### For Deep-Tech Investors (1517 Fund Investment Committee):
1.  **[10_1517_TECHNICAL_BRIEF.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/10_1517_TECHNICAL_BRIEF.md)** — High-density 12-question diligence summary.
2.  **[01_PROBLEM_AND_RESEARCH_THESIS.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/01_PROBLEM_AND_RESEARCH_THESIS.md)** — Core thesis and explicit non-goals.
3.  **[08_RND_BUDGET_AND_CAPITAL_PLAN.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/08_RND_BUDGET_AND_CAPITAL_PLAN.md)** — How capital converts into empirical checkpoints.
4.  **[09_TECHNICAL_FOUNDER_AND_1517_CASE.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/09_TECHNICAL_FOUNDER_AND_1517_CASE.md)** — Moats, defensibility, and anti-thesis invalidation criteria.

### For Distributed Systems & AI Security Researchers:
1.  **[02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/02_EVIDENCE_AND_RESEARCH_LANDSCAPE.md)** — State-of-the-art gap analysis.
2.  **[03_AGENT_STATE_MODEL_AND_INVARIANTS.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/03_AGENT_STATE_MODEL_AND_INVARIANTS.md)** — Formal state taxonomy and mathematical invariants.
3.  **[04_SYSTEM_ARCHITECTURE.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/04_SYSTEM_ARCHITECTURE.md)** — Subsystem engineering and integration topologies.
4.  **[05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/05_THREAT_MODEL_AND_FAILURE_TAXONOMY.md)** — Adversarial and systemic failure analysis.
5.  **[06_EXPERIMENT_AND_BENCHMARK_PLAN.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/06_EXPERIMENT_AND_BENCHMARK_PLAN.md)** — RQ1–RQ8 falsification protocols.
6.  **[RESEARCH_DECISION_LEDGER.md](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/RESEARCH_DECISION_LEDGER.md)** — Living architectural decision log.

---

## The 18-Month Checkpoint Schedule

```
+---------------------------------------------------------------------------------------------------------+
| PHASE 1: M01 - M03 | Foundations & Telemetry Harness        | GATE M3: Intercept overhead <= 30ms       |
| PHASE 2: M04 - M06 | Flight Recorder & Causal Replay        | GATE M6: Root-cause attribution >= 80%    |
| PHASE 3: M07 - M09 | Authority Reducer & Effect Gate        | GATE M9: UER <= 0.001, FDR <= 2%          |
| PHASE 4: M10 - M12 | Experience Admission & Quarantine      | GATE M12: False-promotion <= 2%           |
| PHASE 5: M13 - M15 | Persistent Risk & MDDD Extension       | GATE M15: MDDD >= 2.0x baseline (p < 0.01)|
| PHASE 6: M16 - M18 | Cross-Runtime & Final Thesis Gate      | GATE M18: Final Proceed / Pivot / Stop    |
+---------------------------------------------------------------------------------------------------------+
```

---

## Contact & Research Inquiries

For technical correspondence, design-partner inquiries, or research collaboration regarding the gibbrn R&D program:
*   **Project Lead:** Principal Systems Researcher & Technical Founder, gibbrn Project
*   **Repository Track:** `github.com/agenticbernie/gibbrn`
*   **Status:** Pre-Seed R&D Phase (Active Investor Diligence Cycle)
