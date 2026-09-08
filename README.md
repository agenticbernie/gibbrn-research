# GIBBRN — Agent State Integrity Layer

### 36-Month Systems Research & Prototype Program
**Target Audience:** 1517 Fund Investment Committee, Distributed Systems Researchers, AI Security Architects  
**Repository:** `github.com/agenticbernie/gibbrn-research`  
**Status:** Pre-Seed R&D-Stage Systems Hypothesis (Checkpoint-Gated Empirical Program)  
**Capital Status (V4.2, founder-authorized):** **Current Financing Target USD 450,000** (M0–M24) · **Modeled 36-Month Capitalization ~USD 700,000** · **Conditional Year-3 Extension ~USD 250,000** subject to the M24 evidence/Arc-III-readiness gates (see [`docs/submission/08_CAPITAL_PLAN.md`](./docs/submission/08_CAPITAL_PLAN.md))  
**License:** Strict Restricted Non-Commercial & Anti-Training License (See [`LICENSE`](./LICENSE))

---

> **"Agents can change. Their integrity must persist."**

> **GIBBRN investigates continuity and integrity for long-lived adaptive agents.**

---

## Executive Overview: What is gibbrn?

**GIBBRN investigates how long-lived adaptive agents can change models, runtimes, memory representations, skills, tools, collaborators, and execution environments while preserving canonical identity, authority, provenance, validated competence, objective integrity, and end-to-end consequence integrity.**

This is a research hypothesis/program, not an established guarantee.

This repository hosts the complete **36-Month R&D Technical Dossier (V4)**, building on the V3 24-month dossier (preserved in history) with a September 6–8, 2026 evidence delta of 13 newly verified evidence entries, prioritizing primary sources.

```
+-----------------------------------------------------------------------------------+
|                        GIBBRN SYSTEMS ARCHITECTURE                                |
+-----------------------------------------------------------------------------------+
| BROAD RESEARCH THESIS:                                                            |
| Continuity and integrity for long-lived adaptive agents: "How can a system       |
| change cognition, models, memory, skills, tools, runtime, environment, and        |
| collaborators without losing identity, objective, competence, authority,          |
| or consequence integrity?"                                                        |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| NARROW PRE-SEED INITIAL WEDGE:                                                    |
| Deterministic Authority & Consequence Integrity: "How autonomous agents can       |
| change their cognitive reasoning without silently changing what they are          |
| authorized to do — and whether the realized effect matches what was authorized."  |
+-----------------------------------------------------------------------------------+
```

### Three-year progression

```
YEAR 1 (M1–M12) — ACT SAFELY:        Can one adaptive agent act safely?
YEAR 2 (M13–M24) — CHANGE SAFELY:    Can that agent change safely?
YEAR 3 (M25–M36) — PERSIST TOGETHER: Can persistent agents operate together
                                     and remain governable? (conditional on M24)
```

---

## The Three Physical Research Engines

Architectural complexity has been disciplined into **three physical engines** (no fourth engine in V4):

1.  **Engine 1: Causal & Continuity State Spine (Storage, Identity & Lineage Substrate)**
    - Append-only PostgreSQL 16 / SQLite WAL event ledger.
    - Manages Merkle DAG event trees, identity/contract/authority/skill lineage, execution permits, effect receipts, outcome evidence, migration checkpoints, pending commitments (design targets).
    - Formally separates **Hermetic Replay** (local sealed containers) from **Open-World Causal Audit** (mutable APIs).
2.  **Engine 2: Deterministic Effect Gate / End-to-End Authority & Consequence Integrity Pipeline [PRIMARY WEDGE]**
    - Out-of-process daemon (Rust/Go) intercepting mutating tool requests.
    - Issues short-lived, single-use capability leases (TTL $\le 2000\text{ms}$) mitigating TOCTOU race conditions.
    - Adds a Tool Network Authority Broker (capability vs. endpoint vs. credential separation) and permit→effect→receipt reconciliation.
    - Couples capability checks with **gVisor (runsc) micro-sandboxes** to constrain the blast radius of malicious or unsafe tool parameters at the OS boundary.
3.  **Engine 3: Procedural Skill Compilation & Verified Adaptation Engine**
    - Pipeline: episodes → attribution → procedural clustering → family abstraction → candidate procedure → deterministic checks → advisory semantic review → held-out evaluation → regression suite → commit/reject/quarantine → specialization.
    - Narrowed strictly to verifier-rich domains (deterministic Python functions and Bash tool macros).
    - Enforces Git quarantine staging branches and micro-sandbox regression testing before promoting skills to durable memory. Semantic judges supply evidence only — never unilateral commit authority.

---

## Documentation Structure (`/docs`)

All project documentation is structured in the [`docs/`](./docs/README.md) directory:

```
docs/
├── submission/         <-- [PRIMARY DOSSIER] Canonical V4 36-month research dossier (14 files; see docs/submission/00_README.md)
├── verification/       <-- Audit ledgers (V2 + V3 delta). Reports marked SUPERSEDED are historical; do not cite as current.
├── diligence_audit/    <-- 1517-oriented adversarial diligence simulation reports (12 files; historical simulation, not an independent audit)
└── archive/            <-- Historical working archives preserving complete scientific lineage
    ├── v2_reconstructed/  (Post-audit reconstructed draft)
    └── v1_initial/        (Initial exploratory research proposal)
```

### Primary Research Dossier ([`docs/submission/`](./docs/submission/00_README.md))

| Chapter | Document Title | Description |
| :--- | :--- | :--- |
| **[00](./docs/submission/00_README.md)** | Dossier Master Overview | Executive summary, systems architecture, checkpoint schedule, and reading orders. |
| **[01](./docs/submission/01_RESEARCH_THESIS.md)** | Core Research Thesis | Continuity + integrity thesis, north-star RQ, counter-case (with τ^τ-Bench discipline), non-goals. |
| **[02](./docs/submission/02_EVIDENCE_LANDSCAPE.md)** | Evidence Landscape | Verified primary literature plus September 6–8, 2026 evidence delta (13 sources, 7 clusters). |
| **[03](./docs/submission/03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** | State Semantics & Trust Model | Four-Class State Taxonomy (retained), Continuity Model, Goal Contract, Invariants 1–9. |
| **[04](./docs/submission/04_ARCHITECTURE.md)** | Systems Architecture | Three Physical Engines, authority broker, consequence pipeline, labeled latency budgets. |
| **[05](./docs/submission/05_SECURITY_AND_FAILURE_MODEL.md)** | Security & Threat Model | Hardened security model plus V4 threats (context discontinuity, endpoint confusion, mismatch, capture). |
| **[06](./docs/submission/06_CORE_RESEARCH_PROGRAM.md)** | Core Research Program | Twelve RQs (RQ1–RQ12) across 3 arcs, G1–G8 goals, survival analysis for $\text{MDID}_\tau$, pre-registration. |
| **[07](./docs/submission/07_36_MONTH_ROADMAP.md)** | 36-Month R&D Roadmap | ~24 checkpoints and twelve binding gates (M3–M36); four major thesis gates (M9/M18/M24/M36). |
| **[08](./docs/submission/08_CAPITAL_PLAN.md)** | Capital & Expense Model | V4.2 rebase: $450k current target (M0–M24), ~$700k program, ~$250k conditional Year-3; V3 $400k/$150k retained as history. |
| **[09](./docs/submission/09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** | Novelty & Company Thesis | Potential research contributions vs. plumbing, OCAP lineage, CONTINUITY precedent, platform risk. |
| **[10](./docs/submission/10_1517_TECHNICAL_BRIEF.md)** | 1517 Technical Brief | High-density 12-question diligence summary for the 1517 Fund Investment Committee. |
| **[11](./docs/submission/11_INVESTOR_OVERVIEW.md)** | Investor Overview (One Page) | Problem, thesis, wedge, evidence plan, and capital status in one page. |
| **[ADRs](./docs/submission/RESEARCH_DECISION_LEDGER.md)** | Living Systems ADR Ledger | Historical records AD-001–AD-023 (AD-017/AD-019 superseded) plus V4 transition and V4.1 review AD-024–AD-047. |
| **[Changelog](./docs/submission/DOSSIER_CHANGELOG.md)** | Master Provenance Ledger | Full traceability V1 → V2 → V3 → V4 (CHG-001–CHG-059). |

---

## 36-Month Milestone Schedule & Falsification Gates

The program operates on a **~24-checkpoint / 12-gate** schedule (lightweight checkpoints every ~6 weeks; binding gates every 3 months; thesis reviews at M6/M12/M18/M24/M30/M36; major thesis gates at M9/M18/M24/M36).

```text
+----------------------------------------------------------------------------------------------------------------+
| ARC I — ACT SAFELY (M1–M12)                                                                                  |
| PHASE 1: M01 - M03 | State / identity / Goal Contract semantics | GATE M3: Interception/state classification  |
| PHASE 2: M04 - M06 | Causal & continuity reconstruction         | GATE M6: Causal reconstruction > telemetry  |
| PHASE 3: M07 - M09 | Authority & consequence pipeline (WEDGE)   | GATE M9 ★: Near-zero unauthorized effects   |
| PHASE 4: M10 - M12 | Procedural-family verified adaptation      | GATE M12: Poisoned/regressive skill blocked |
| ARC II — CHANGE SAFELY (M13–M24)                                                                              |
| PHASE 5: M13 - M15 | Adaptation portability / specialization    | GATE M15: Transfer or safe bounding         |
| PHASE 6: M16 - M18 | Integrated long-horizon integrity          | GATE M18 ★: Joint depth + incidence gain (C vs B) |
| PHASE 7: M19 - M21 | Cross-model/runtime migration continuity   | GATE M21: Migration preserves continuity    |
| PHASE 8: M22 - M24 | Objective & evaluation integrity           | GATE M24 ★: Objective integrity holds       |
| ARC III — PERSIST TOGETHER (M25–M36; CONDITIONAL on M24)                                                       |
| PHASE 9: M25 - M27 | Decision-sufficient state                  | GATE M27: Canonical variables justified     |
| PHASE 10: M28-M30 | Team coordination-state transfer           | GATE M30: Transfer reduces replacement cost |
| PHASE 11: M31-M33 | Shared-state governance                    | GATE M33: Governed sharing contains exploits|
| PHASE 12: M34-M36 | Integrated persistent-agent validation     | GATE M36 ★: Scientific (A) + Company (B) verdicts |
+----------------------------------------------------------------------------------------------------------------+
★ = major thesis gate
```

---

## Recommended Reading Order

### For Deep-Tech Investors (1517 Fund Investment Committee):
1.  **[`docs/submission/11_INVESTOR_OVERVIEW.md`](./docs/submission/11_INVESTOR_OVERVIEW.md)** — One-page overview: problem, thesis, wedge, evidence plan, capital status.
2.  **[`docs/submission/10_1517_TECHNICAL_BRIEF.md`](./docs/submission/10_1517_TECHNICAL_BRIEF.md)** — High-density 12-question diligence summary.
2.  **[`docs/submission/01_RESEARCH_THESIS.md`](./docs/submission/01_RESEARCH_THESIS.md)** — Core problem, thesis vs. wedge, counter-case, and non-goals.
3.  **[`docs/submission/08_CAPITAL_PLAN.md`](./docs/submission/08_CAPITAL_PLAN.md)** — Rebased financing model: $450k through M24, ~$700k program, ~$250k conditional Year-3.
4.  **[`docs/submission/09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md`](./docs/submission/09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** — Competitors, defensibility, and platform risk.
5.  **[`docs/submission/DOSSIER_CHANGELOG.md`](./docs/submission/DOSSIER_CHANGELOG.md)** — Complete audit provenance and modification history.

### For Systems Researchers and Security Engineers:
1.  **[`docs/submission/02_EVIDENCE_LANDSCAPE.md`](./docs/submission/02_EVIDENCE_LANDSCAPE.md)** — Verified literature plus September 2026 evidence delta.
2.  **[`docs/submission/03_STATE_SEMANTICS_AND_TRUST_MODEL.md`](./docs/submission/03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** — Four-Class State Taxonomy, Continuity Model, Goal Contract, Invariants 1–9.
3.  **[`docs/submission/04_ARCHITECTURE.md`](./docs/submission/04_ARCHITECTURE.md)** — The Three Physical Engines and gVisor sandboxing.
4.  **[`docs/submission/05_SECURITY_AND_FAILURE_MODEL.md`](./docs/submission/05_SECURITY_AND_FAILURE_MODEL.md)** — Hardened security architecture and threat mitigations.
5.  **[`docs/submission/06_CORE_RESEARCH_PROGRAM.md`](./docs/submission/06_CORE_RESEARCH_PROGRAM.md)** — RQ1–RQ12, G1–G8 goals, discrete survival analysis for $\text{MDID}_\tau$.
6.  **[`docs/submission/07_36_MONTH_ROADMAP.md`](./docs/submission/07_36_MONTH_ROADMAP.md)** — Checkpoint-gated timeline and binding kill triggers.
7.  **[`docs/submission/RESEARCH_DECISION_LEDGER.md`](./docs/submission/RESEARCH_DECISION_LEDGER.md)** — Living systems ADRs (AD-001 through AD-047).

---

## License & Intellectual Property Notice

This repository contains pre-publication research materials, architectural specifications, and experimental protocols. Public viewing and evaluation are permitted; commercial implementation, model training, reproduction, redistribution, and derivative use are strictly subject to the **[GIBBRN Strict Research and Evaluation License](./LICENSE)**:
- **Public Viewing & Evaluation:** Permitted for non-commercial academic research review, scientific evaluation, and investor technical due diligence.
- **Strict Anti-AI Training:** Use of this text, schemas, architectures, or metrics (including MDID) for AI/LLM model training, fine-tuning, distillation, benchmarking, or synthetic data generation is **strictly prohibited**.
- **No Commercial Use:** Commercial deployment, service integration, or derivative systems implementation requires a separate written commercial license.

See [`LICENSE`](./LICENSE) for complete legal terms.

---

> **Agents can change. Their integrity must persist.**
