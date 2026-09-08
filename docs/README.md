# GIBBRN Documentation Index & Repository Map

**Project:** gibbrn — Agent State Integrity Layer  
**Repository:** `github.com/agenticbernie/gibbrn-research`  
**Dossier Version:** 4.2 (36-Month Systems Research & Prototype Program)  
**License:** Strict Restricted Research & Evaluation License (See [`LICENSE`](../LICENSE))  
**Audience:** 1517 Fund Investment Committee, Distributed Systems Researchers, AI Security Architects

---

> **"Agents can change. Their integrity must persist."**

> **GIBBRN investigates continuity and integrity for long-lived adaptive agents.**

---

## Structure of `/docs`

The documentation in this repository is organized into four distinct tiers reflecting the iterative adversarial diligence and evidence verification process:

```
docs/
├── submission/         <-- [PRIMARY] Canonical V4 36-month research dossier (14 files)
├── verification/       <-- Complete audit ledgers from the final evidence verification pass (10 files)
├── diligence_audit/    <-- Adversarial diligence audit reports modeled on a 1517-style technical review (12 files)
└── archive/            <-- Historical working archives preserving complete scientific lineage
    ├── v2_reconstructed/  (Post-audit reconstructed draft)
    └── v1_initial/        (Initial exploratory research proposal)
```

---

## 1. Primary Submission Dossier (`/docs/submission`)

The canonical V4.2 research dossier. Externally checkable claims carry epistemic labels and sources; open verification items (unconfirmed citations, pre-registration, statistical calibration) are marked inline. Verification reports marked SUPERSEDED are historical. V3 24-month capital figures retained in `08_CAPITAL_PLAN.md` Appendices H1–H3 are historical context; the canonical financing model is the V4.2 rebase ($450k current / ~$700k program / ~$250k conditional Year-3).

| File | Document Title | Focus & Core Contribution |
| :--- | :--- | :--- |
| **[`00_README.md`](./submission/00_README.md)** | Dossier Master Overview | Executive summary, systems architecture diagram, milestone schedule, and reading order. |
| **[`01_RESEARCH_THESIS.md`](./submission/01_RESEARCH_THESIS.md)** | Core Research Thesis | Continuity + integrity thesis, north-star RQ, Agentless counter-case (τ^τ-Bench discipline), non-goals. |
| **[`02_EVIDENCE_LANDSCAPE.md`](./submission/02_EVIDENCE_LANDSCAPE.md)** | Evidence Landscape | Verified literature plus September 6–8, 2026 evidence delta (13 sources, 7 clusters). |
| **[`03_STATE_SEMANTICS_AND_TRUST_MODEL.md`](./submission/03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** | State Semantics & Trust Model | Four-Class State Taxonomy (retained), Continuity Model, Goal Contract, Invariants 1–9. |
| **[`04_ARCHITECTURE.md`](./submission/04_ARCHITECTURE.md)** | Systems Architecture | The Three Physical Engines (Continuity Spine, Consequence Pipeline + Authority Broker, Skill Compilation), gVisor sandboxing, labeled latency targets. |
| **[`05_SECURITY_AND_FAILURE_MODEL.md`](./submission/05_SECURITY_AND_FAILURE_MODEL.md)** | Security & Threat Model | Hardened security model plus V4 threats (ADV-06–ADV-09), expanded failure taxonomy SYS-01–SYS-10. |
| **[`06_CORE_RESEARCH_PROGRAM.md`](./submission/06_CORE_RESEARCH_PROGRAM.md)** | Core Research Program | Twelve RQs (RQ1–RQ12) across 3 arcs, G1–G8 goals, competing-risks / Aalen–Johansen CIF modeling for $\text{MDID}_\tau$, pre-registration commitment. |
| **[`07_36_MONTH_ROADMAP.md`](./submission/07_36_MONTH_ROADMAP.md)** | 36-Month R&D Roadmap | ~24 evidence checkpoints and twelve binding gates (M3–M36); four major thesis gates (M9/M18/M24/M36). |
| **[`08_CAPITAL_PLAN.md`](./submission/08_CAPITAL_PLAN.md)** | Capital & Expense Plan | V4.2 rebase: $450k current target, ~$700k program, ~$250k conditional Year-3; V3 figures as history. |
| **[`09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md`](./submission/09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** | Novelty & Company Thesis | Potential research contributions vs. commoditized plumbing, OCAP lineage, CONTINUITY precedent, platform risks. |
| **[`10_1517_TECHNICAL_BRIEF.md`](./submission/10_1517_TECHNICAL_BRIEF.md)** | 1517 Investor Technical Brief | High-density 12-question diligence responses for the 1517 Fund Investment Committee. |
| **[`11_INVESTOR_OVERVIEW.md`](./submission/11_INVESTOR_OVERVIEW.md)** | Investor Overview (One Page) | Problem, thesis, wedge, evidence plan, and capital status in one page. |
| **[`RESEARCH_DECISION_LEDGER.md`](./submission/RESEARCH_DECISION_LEDGER.md)** | Living Systems ADR Ledger | Architecture Decision Records covering initial formulation (AD-001–AD-011), post-diligence decisions (AD-012–AD-023; AD-017/AD-019 superseded), and V4 transition + V4.1 review (AD-024–AD-047). |
| **[`DOSSIER_CHANGELOG.md`](./submission/DOSSIER_CHANGELOG.md)** | Master Provenance Ledger | Full traceability V1 → V2 → V3 → V4 (CHG-001–CHG-059). |

---

## 2. Verification Audit Ledgers (`/docs/verification`)

The complete verification paper trail generated during the final submission-grade evidence verification pass:

*   [`FINAL_VERIFY_00_SUBMISSION_VERDICT.md`](./verification/FINAL_VERIFY_00_SUBMISSION_VERDICT.md) — Scorecard, blocking issues, and spot-check audit.
*   [`FINAL_VERIFY_01_CITATION_LEDGER.md`](./verification/FINAL_VERIFY_01_CITATION_LEDGER.md) — Line-by-line verification table for all 19 citations.
*   [`FINAL_VERIFY_02_FACT_AND_LANGUAGE_LEDGER.md`](./verification/FINAL_VERIFY_02_FACT_AND_LANGUAGE_LEDGER.md) — Audit of absolute claims, competitor statements, and epistemic labels.
*   [`FINAL_VERIFY_03_NUMBERS_AND_TARGETS.md`](./verification/FINAL_VERIFY_03_NUMBERS_AND_TARGETS.md) — Quantitative classifications, latency budgets, and token arithmetic.
*   [`FINAL_VERIFY_04_BENCHMARK_AND_STATISTICS.md`](./verification/FINAL_VERIFY_04_BENCHMARK_AND_STATISTICS.md) — MDID mathematical review and experimental protocols for Core RQ1–RQ5.
*   [`FINAL_VERIFY_05_COMPETITOR_AND_NOVELTY.md`](./verification/FINAL_VERIFY_05_COMPETITOR_AND_NOVELTY.md) — Steel-man analysis of 5 competitor classes and novelty decomposition.
*   [`FINAL_VERIFY_06_1517_AND_CAPITAL.md`](./verification/FINAL_VERIFY_06_1517_AND_CAPITAL.md) — Historical V2/V3 capital-diligence ledger (audits $285k/$120k/$400k-era structures) — superseded for current financing; see `08_CAPITAL_PLAN.md`.
*   [`FINAL_VERIFY_07_CANONICAL_FACT_SHEET.md`](./verification/FINAL_VERIFY_07_CANONICAL_FACT_SHEET.md) — Single source of truth for approved figures, citations, and terminology.
*   [`FINAL_VERIFY_08_PATCHSET.md`](./verification/FINAL_VERIFY_08_PATCHSET.md) — Surgical patch specifications for all documents.
*   [`FINAL_VERIFY_09_FINAL_CHANGELOG.md`](./verification/FINAL_VERIFY_09_FINAL_CHANGELOG.md) — Detailed changelog recording all 24 applied modifications.

---

## 3. Adversarial Diligence Simulation (`/docs/diligence_audit`)

The independent adversarial diligence simulation (modeled on a 1517-style technical review) that stress-tested the initial dossier:

*   [`AUDIT_00_EXECUTIVE_VERDICT.md`](./diligence_audit/AUDIT_00_EXECUTIVE_VERDICT.md) — Initial diligence score, critical red flags, and kill test summary.
*   [`AUDIT_01_CLAIM_LEDGER.md`](./diligence_audit/AUDIT_01_CLAIM_LEDGER.md) — Comprehensive inventory and audit of foundational claims.
*   [`AUDIT_02_CITATION_AND_SOURCE_CHECK.md`](./diligence_audit/AUDIT_02_CITATION_AND_SOURCE_CHECK.md) — Identification of citation errors and synthetic references in early drafts.
*   [`AUDIT_03_NUMBERS_MODELS_AND_BENCHMARKS.md`](./diligence_audit/AUDIT_03_NUMBERS_MODELS_AND_BENCHMARKS.md) — Review of token economics, model names, and benchmark suites.
*   [`AUDIT_04_NOVELTY_AND_COMPETITIVE_LANDSCAPE.md`](./diligence_audit/AUDIT_04_NOVELTY_AND_COMPETITIVE_LANDSCAPE.md) — Critical evaluation of novelty claims against Temporal, DBOS, and Mem0.
*   [`AUDIT_05_ARCHITECTURE_AND_SECURITY_REDTEAM.md`](./diligence_audit/AUDIT_05_ARCHITECTURE_AND_SECURITY_REDTEAM.md) — Red-team attack vectors (parameter smuggling, TOCTOU, replay divergence).
*   [`AUDIT_06_EXPERIMENT_AND_STATISTICS_REVIEW.md`](./diligence_audit/AUDIT_06_EXPERIMENT_AND_STATISTICS_REVIEW.md) — Critique of geometric compounding and recommendation of survival analysis.
*   [`AUDIT_07_ROADMAP_AND_BUDGET_REVIEW.md`](./diligence_audit/AUDIT_07_ROADMAP_AND_BUDGET_REVIEW.md) — Critical path analysis and evaluation of the \$120k vs. \$285k budgets.
*   [`AUDIT_08_1517_DILIGENCE.md`](./diligence_audit/AUDIT_08_1517_DILIGENCE.md) — Dedicated diligence simulation from the perspective of 1517 Fund.
*   [`AUDIT_09_CROSS_DOCUMENT_CONSISTENCY.md`](./diligence_audit/AUDIT_09_CROSS_DOCUMENT_CONSISTENCY.md) — Reconciliation of terminology, subsystem counts, and numbers across drafts.
*   [`AUDIT_10_REQUIRED_REWRITES.md`](./diligence_audit/AUDIT_10_REQUIRED_REWRITES.md) — Specific rewrite directives implemented in V2 and Final Submission.
*   [`AUDIT_11_FINAL_RESEARCH_DECISION.md`](./diligence_audit/AUDIT_11_FINAL_RESEARCH_DECISION.md) — The Kill Test: why the project should proceed, narrow, or stop.

---

## 4. Historical Working Archives (`/docs/archive`)

Preserves the complete, untampered historical evolution of the research:
*   [`docs/archive/v2_reconstructed/`](./archive/v2_reconstructed/) — The intermediate V2 files created directly following the diligence audit.
*   [`docs/archive/v1_initial/`](./archive/v1_initial/) — The initial exploratory research dossier.

---

> **Agents can change. Their integrity must persist.**
