# GIBBRN — Agent State Integrity Layer

### 18-Month Systems Research & Prototype Program
**Target Audience:** 1517 Fund Investment Committee, Distributed Systems Researchers, AI Security Architects  
**Repository:** `github.com/agenticbernie/gibbrn-research`  
**Status:** Pre-Seed R&D-Stage Systems Hypothesis (Checkpoint-Gated Empirical Program)  
**Primary Capital Ask:** **USD 285,000** for an 18-Month Founder-Led Systems Research Program  
**License:** Strict Restricted Non-Commercial & Anti-Training License (See [`LICENSE`](./LICENSE))  

---

> **"Agents can change. Their integrity must persist."**

---

## Executive Overview: What is gibbrn?

**gibbrn investigates Agent State Integrity for long-lived autonomous agents.**

Specifically, the project researches whether a framework-neutral control layer can preserve the integrity, authority, provenance, validation status, and recoverability of consequential agent state as autonomous systems operate, accumulate experience, and change over time.

This repository hosts the complete **18-Month R&D Technical Dossier**, which has undergone both an intensive 1517-oriented Adversarial Diligence Simulation and an independent Submission-Grade Evidence Verification Pass.

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

Architectural complexity has been disciplined into **three physical engines**:

1.  **Engine 1: The Causal State Spine (Storage & Lineage Substrate)**
    - Append-only PostgreSQL 16 / SQLite WAL event ledger.
    - Manages Merkle DAG event trees, effect receipts, and checkpoint snapshots.
    - Formally separates **Hermetic Replay** (local sealed containers) from **Open-World Causal Audit** (mutable APIs).
2.  **Engine 2: The Deterministic Effect Gate (Inline Policy & Kernel Sandbox) [PRIMARY WEDGE]**
    - Out-of-process daemon (Rust/Go) intercepting mutating tool requests.
    - Issues short-lived, single-use capability leases (TTL $\le 2000\text{ms}$) mitigating TOCTOU race conditions.
    - Couples capability checks with **gVisor (runsc) micro-sandboxes** to constrain the blast radius of malicious or unsafe tool parameters at the OS boundary.
3.  **Engine 3: The Experience Admission Engine (Verifier-Rich Skill Governance)**
    - Narrowed strictly to verifier-rich domains (deterministic Python functions and Bash tool macros).
    - Enforces Git quarantine staging branches and micro-sandbox regression testing before promoting skills to durable memory.

---

## Documentation Structure (`/docs`)

All project documentation is structured in the [`docs/`](./docs/README.md) directory:

```
docs/
├── submission/         <-- [PRIMARY DOSSIER] Primary submission candidate — evidence-verified 18-month research dossier (13 files)
├── verification/       <-- Complete audit ledgers from the final evidence verification pass (10 files)
├── diligence_audit/    <-- 1517-oriented adversarial diligence simulation reports (12 files)
└── archive/            <-- Historical working archives preserving complete scientific lineage
    ├── v2_reconstructed/  (Post-audit reconstructed draft)
    └── v1_initial/        (Initial exploratory research proposal)
```

### Primary Research Dossier ([`docs/submission/`](./docs/submission/00_README.md))

| Chapter | Document Title | Description |
| :--- | :--- | :--- |
| **[00](./docs/submission/00_README.md)** | Dossier Master Overview | Executive summary, systems architecture, checkpoint schedule, and reading orders. |
| **[01](./docs/submission/01_RESEARCH_THESIS.md)** | Core Research Thesis | Problem formulation, thesis vs. initial wedge, the Agentless counter-case, non-goals. |
| **[02](./docs/submission/02_EVIDENCE_LANDSCAPE.md)** | Evidence Landscape | Verified primary literature, SWE-bench harness sensitivity findings, competitive matrix. |
| **[03](./docs/submission/03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** | State Semantics & Trust Model | Four-Class State Taxonomy (Cognitive, Operational, Authoritative, Runtime), Invariants 1–5. |
| **[04](./docs/submission/04_ARCHITECTURE.md)** | Systems Architecture | Three Physical Engines, gVisor sandboxing, dataflow diagrams, labeled latency budgets. |
| **[05](./docs/submission/05_SECURITY_AND_FAILURE_MODEL.md)** | Security & Threat Model | Hardened security model: parameter smuggling defenses, kernel isolation, TOCTOU leases. |
| **[06](./docs/submission/06_CORE_RESEARCH_PROGRAM.md)** | Core Research Program | Five causally chained Core RQs, discrete survival hazard modeling for $\text{MDDD}_\tau$, pre-registration. |
| **[07](./docs/submission/07_24_MONTH_ROADMAP.md)** | 24-Month R&D Roadmap | Six milestone gates (M3–M18) with explicit Kill / Narrow / Pivot criteria. |
| **[08](./docs/submission/08_CAPITAL_PLAN.md)** | Capital & Expense Model | Primary \$285,000 budget vs. \$120,000 fallback, compute modeling, and capital-at-risk. |
| **[09](./docs/submission/09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** | Novelty & Company Thesis | Genuine novelty vs. plumbing, OCAP security lineage, competitor analysis, platform risk. |
| **[10](./docs/submission/10_1517_TECHNICAL_BRIEF.md)** | 1517 Technical Brief | High-density 12-question diligence summary for the 1517 Fund Investment Committee. |
| **[ADRs](./docs/submission/RESEARCH_DECISION_LEDGER.md)** | Living Systems ADR Ledger | Historical records AD-001–AD-011 and post-diligence decisions AD-012–AD-021. |
| **[Changelog](./docs/submission/DOSSIER_CHANGELOG.md)** | Master Provenance Ledger | Full traceability of all 24 modifications from V1 through V2 to Final Submission. |

---

## 24-Month Milestone Schedule & Falsification Gates

The program operates on a **16-checkpoint / 8-gate** schedule (lightweight checkpoints every ~6 weeks; binding gates every 3 months; thesis reviews every 6 months).

```text
+----------------------------------------------------------------------------------------------------------------+
| PHASE 1: M01 - M03 | State Semantics + minimal interceptor      | GATE M3: Interception/state classification   |
| PHASE 2: M04 - M06 | Causal State Spine + adaptation provenance | GATE M6: Causal reconstruction > telemetry   |
| PHASE 3: M07 - M09 | Deterministic Effect Gate (MAIN WEDGE)     | GATE M9: Near-zero unauthorized effects      |
| PHASE 4: M10 - M12 | Verified Skill Substrate                   | GATE M12: Poisoned/regressive skill blocked  |
| PHASE 5: M13 - M15 | Harness Generalization                     | GATE M15: Characterize transfer/portability  |
| PHASE 6: M16 - M18 | Integrated long-horizon survival           | GATE M18: Meaningful MDDD improvement        |
| PHASE 7: M19 - M21 | Cross-model replication + delegation       | GATE M21: Results survive model/runtime swaps|
| PHASE 8: M22 - M24 | Design partners + commercial falsification | GATE M24: Proceed / Narrow / Pivot / Stop    |
+----------------------------------------------------------------------------------------------------------------+
```

---

## Recommended Reading Order

### For Deep-Tech Investors (1517 Fund Investment Committee):
1.  **[`docs/submission/10_1517_TECHNICAL_BRIEF.md`](./docs/submission/10_1517_TECHNICAL_BRIEF.md)** — High-density 12-question diligence summary.
2.  **[`docs/submission/01_RESEARCH_THESIS.md`](./docs/submission/01_RESEARCH_THESIS.md)** — Core problem, thesis vs. wedge, counter-case, and non-goals.
3.  **[`docs/submission/08_CAPITAL_PLAN.md`](./docs/submission/08_CAPITAL_PLAN.md)** — \$400,000 budget model and capital-at-risk schedule.
4.  **[`docs/submission/09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md`](./docs/submission/09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** — Competitors, defensibility, and platform risk.
5.  **[`docs/submission/DOSSIER_CHANGELOG.md`](./docs/submission/DOSSIER_CHANGELOG.md)** — Complete audit provenance and modification history.

### For Systems Researchers and Security Engineers:
1.  **[`docs/submission/02_EVIDENCE_LANDSCAPE.md`](./docs/submission/02_EVIDENCE_LANDSCAPE.md)** — Verified literature and empirical gap analysis.
2.  **[`docs/submission/03_STATE_SEMANTICS_AND_TRUST_MODEL.md`](./docs/submission/03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** — Four-Class State Taxonomy and formal invariants.
3.  **[`docs/submission/04_ARCHITECTURE.md`](./docs/submission/04_ARCHITECTURE.md)** — The Three Physical Engines and gVisor sandboxing.
4.  **[`docs/submission/05_SECURITY_AND_FAILURE_MODEL.md`](./docs/submission/05_SECURITY_AND_FAILURE_MODEL.md)** — Hardened security architecture and threat mitigations.
5.  **[`docs/submission/06_CORE_RESEARCH_PROGRAM.md`](./docs/submission/06_CORE_RESEARCH_PROGRAM.md)** — Core RQ1–RQ7 and discrete survival analysis for $\text{MDDD}_\tau$.
6.  **[`docs/submission/07_24_MONTH_ROADMAP.md`](./docs/submission/07_24_MONTH_ROADMAP.md)** — Checkpoint-gated timeline and binding kill triggers.
7.  **[`docs/submission/RESEARCH_DECISION_LEDGER.md`](./docs/submission/RESEARCH_DECISION_LEDGER.md)** — Living systems ADRs (AD-001 through AD-021).

---

## License & Intellectual Property Notice

This repository contains pre-publication research materials, architectural specifications, and experimental protocols. Public viewing and evaluation are permitted; commercial implementation, model training, reproduction, redistribution, and derivative use are strictly subject to the **[GIBBRN Strict Research and Evaluation License](./LICENSE)**:
- **Public Viewing & Evaluation:** Permitted for non-commercial academic research review, scientific evaluation, and investor technical due diligence.
- **Strict Anti-AI Training:** Use of this text, schemas, architectures, or metrics (including MDDD) for AI/LLM model training, fine-tuning, distillation, benchmarking, or synthetic data generation is **strictly prohibited**.
- **No Commercial Use:** Commercial deployment, service integration, or derivative systems implementation requires a separate written commercial license.

See [`LICENSE`](./LICENSE) for complete legal terms.

---

> **Agents can change. Their integrity must persist.**
