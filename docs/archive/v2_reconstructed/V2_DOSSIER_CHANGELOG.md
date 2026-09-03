# Dossier V2 Changelog and Epistemic Provenance Record

**Project Name:** GIBBRN  
**Document Track:** Audit Provenance & Document Lineage  
**Date:** September 2026  
**Audience:** Technical Due-Diligence Reviewers, Systems Researchers, 1517 Fund  
**Purpose:** Comprehensive Traceability of All Architectural, Mathematical, and Editorial Modifications from Dossier V1 to Dossier V2  

---

## 1. Executive Summary of V1 $\to$ V2 Reconstruction

Following the completion of the 1517 Fund Adversarial Diligence Audit (`AUDIT_00` through `AUDIT_11`), the GIBBRN technical dossier was systematically reconstructed. 

Dossier V2 is not a superficial copy-edit; it is a **deep systems recalibration** that sharpens the company's research scope, corrects academic citations, hardens the security architecture, replaces naive mathematical models with formal survival analysis, and establishes a single canonical capital request of **\$285,000**.

---

## 2. Systematic Modification Provenance Ledger

Table 2.1 documents the exact lineage for every major architectural, scientific, and financial shift between V1 and V2.

### Table 2.1: Dossier V1 to Dossier V2 Modification Provenance

| Change ID | Dimension | Old Dossier V1 Position | Adversarial Audit Finding | Independent External Verification | New Dossier V2 Position | Scientific & Strategic Rationale |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CHG-001** | **Academic Citations** | Cited `M. A. W. M. et al., "Is Self-Reflection in LLMs Truly Monotonic?..." 2025` and invented ACL 2024 paper. | `AUDIT_02` (Table 2.1): Identified synthetic placeholder author and non-existent paper title (Severity S3). | Verified via arXiv, Google Scholar, and DBLP: paper does not exist. Genuine papers: Jie Huang et al. (ICLR 2024), Valmeekam et al. (NeurIPS 2023). | Completely removed synthetic references. Cites **Jie Huang et al. (ICLR 2024)** and **Valmeekam et al. (NeurIPS 2023)**. | Eliminates fatal academic credibility risk during technical diligence. |
| **CHG-002** | **MINJA Citation Metadata** | Cited as `Z. Chen et al., arXiv:2402.04944, 2024`. | `AUDIT_02` (Table 2.1): Wrong lead author and incorrect arXiv identifier (Severity S3). | Verified via arXiv:2503.03704: authors are Shen Dong, Shaochen Xu, et al. (NeurIPS). | Updated metadata to **Shen Dong et al., NeurIPS (arXiv:2503.03704)**. | Guarantees citation accuracy under investor source checking. |
| **CHG-003** | **Reliability Mathematics** | Modeled trajectory failure via naive geometric decay: $P_{\text{task}} = \prod p_i \approx p^d$. | `AUDIT_06` (Sec 1): Violates i.i.d. assumption; ignores Markovian error autocorrelation and recovery loops (Severity S3). | Empirical agent literature (AgentErrorBench) confirms errors cascade and hazard rates escalate conditionally. | Replaced with **Discrete Survival Analysis**: $S(k) = \prod_{i=1}^k (1 - h(i))$ and Kaplan-Meier estimation. | Adopts statistically sound mathematical foundations capable of surviving peer review. |
| **CHG-004** | **Subsystem Architecture** | Five separate conceptual subsystems (Spine, Authority, Admission, Gate, Recorder). | `AUDIT_05` (Sec 4): Identified functional overlap and inter-service latency drag (Severity S3). | Systems engineering principles: Spine and Recorder both append to PostgreSQL; Authority and Gate form a single policy enforcement point. | Consolidated into **Three Physical Engines**: (1) Causal State Spine, (2) Deterministic Effect Gate, (3) Experience Admission. | Eliminates architectural bloat and inter-process IPC overhead. |
| **CHG-005** | **Security Model: Parameter Smuggling** | Relied on capability tokens to authorize tool execution. | `AUDIT_05` (Sec 2.1): Red-team showed that authorized tools (`bash`) can execute smuggled payloads (`curl exfiltration`) (Severity S3). | Standard security principle (Saltzer-Schroeder): tool identity does not guarantee argument safety. | Coupled capability tokens with **gVisor (runsc) kernel sandboxing**, seccomp filtering, and network isolation. | Physically contains execution blast radius even if parameter payloads are compromised. |
| **CHG-006** | **Replay Boundaries** | Claimed universal Bounded Causal Replay across all external tool environments. | `AUDIT_05` (Sec 2.3): External environment entropy (changing APIs, timestamps) breaks bit-for-bit replay. | Classic distributed systems finding: non-deterministic side effects diverge without hermetic snapshots. | Formally separated **Hermetic Replay** (local sealed containers) from **Open-World Causal Audit** (divergence localization). | Prevents overpromising unachievable determinism on open-web environments. |
| **CHG-007** | **Research Scope (RQs)** | Planned execution across 8 equal research questions (RQ1–RQ8). | `AUDIT_07` (Sec 5): 8 RQs spread a pre-seed team too thin across peripheral fine-tuning and cross-framework tasks. | High-conviction pre-seed programs focus on proving a single causal chain before expanding scope. | Pruned to **Five Causally Chained Core RQs** (Core RQ1–RQ5). Secondary tracks deferred to non-binding exploratory status. | Guarantees that the central systems thesis is rigorously tested within 18 months. |
| **CHG-008** | **Capital Ask Framing** | Presented \$120k and \$285k plans as interchangeable funding options. | `AUDIT_07` & `AUDIT_08`: \$120k forces solo-founder burn, cuts compute by 70%, and eliminates engineering support (Severity S3). | 1517 Fund pre-seed check range is \$50k–\$1M (avg $\sim \$400\text{k}$). \$285k is scientifically credible. | Established **\$285,000 Target Plan as the primary ask**. Preserved \$120,000 strictly as a constrained fallback. | Projects operational seriousness and funds a viable two-person systems research team. |
| **CHG-009** | **Initial Commercial Wedge** | Described broadly as an "Agent State Integrity Layer" or "Agent Operating System." | `AUDIT_04`: Broad positioning risks competition with Temporal, DBOS, and Mem0 without a sharp wedge. | Enterprise enterprise buyers demand immediate security and authorization controls for agent tools. | Formally elevated the **Deterministic Effect Gate** as the primary pre-seed technical wedge. | Provides an immediate, high-value commercial hook for enterprise design partners. |
| **CHG-010** | **The Counter-Thesis** | Briefly mentioned alternative paradigms, but did not directly confront the Agentless critique. | `AUDIT_11` (The Kill Test): Strongest counter-case is that enterprises will prefer rigid deterministic DAGs over autonomous loops. | Xia et al. (Agentless) proves static pipelines outperform autonomous loops when tasks do not require branching. | Explicitly featured the **"Deterministic Pipeline + Frontier Model" Counter-Case** in `V2_01_RESEARCH_THESIS.md`. | Establishes the exact empirical conditions required to falsify or validate the company. |
| **CHG-011** | **Tone & Hype Scrub** | Used promotional language: *"the missing layer"*, *"physically impossible"*, *"patentable IP"*, *"deep defensible moat"*. | `AUDIT_01` & `AUDIT_04`: Promotional rhetoric undermines credibility with skeptical deep-tech investors. | 1517 Fund backs renegade builders grounded in technical reality, not venture marketing buzzwords. | Completely scrubbed hype words. Replaced with disciplined systems research terminology throughout. | Elevates dossier to authentic institutional research grade. |

---

## 3. Dossier V2 Document Inventory

Dossier V2 is structured into the following 13 cohesive documents:

1.  **[`V2_README.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_README.md)** — Master map, reading orders for investors vs. researchers, and project orientation.
2.  **[`V2_01_RESEARCH_THESIS.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_01_RESEARCH_THESIS.md)** — Problem definition, broad thesis vs. initial wedge, counter-thesis, and non-goals.
3.  **[`V2_02_EVIDENCE_LANDSCAPE.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_02_EVIDENCE_LANDSCAPE.md)** — Verified literature, SWE-agent vs. Agentless findings, competitive substitute matrix.
4.  **[`V2_03_STATE_SEMANTICS_AND_TRUST_MODEL.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_03_STATE_SEMANTICS_AND_TRUST_MODEL.md)** — Four-Class State Taxonomy (Design Hypothesis), trust roots, and formal invariants.
5.  **[`V2_04_ARCHITECTURE.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_04_ARCHITECTURE.md)** — The Three Physical Research Engines (Spine, Effect Gate, Admission Engine) and gVisor sandboxing.
6.  **[`V2_05_SECURITY_AND_FAILURE_MODEL.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_05_SECURITY_AND_FAILURE_MODEL.md)** — Parameter smuggling defenses, kernel isolation, TOCTOU leases, and failure modes.
7.  **[`V2_06_CORE_RESEARCH_PROGRAM.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_06_CORE_RESEARCH_PROGRAM.md)** — Five causally chained Core RQs and discrete survival hazard modeling for $\text{MDDD}_\tau$.
8.  **[`V2_07_18_MONTH_ROADMAP.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_07_18_MONTH_ROADMAP.md)** — Six checkpoint gates (M3–M18) with explicit Kill / Narrow / Pivot criteria.
9.  **[`V2_08_CAPITAL_PLAN.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_08_CAPITAL_PLAN.md)** — Primary \$285,000 budget vs. \$120,000 fallback, compute modeling, and capital-at-risk.
10. **[`V2_09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_09_NOVELTY_COMPETITION_AND_COMPANY_THESIS.md)** — Genuine novelty vs. commoditized plumbing, competitor matrix, and platform risks.
11. **[`V2_10_1517_TECHNICAL_BRIEF.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_10_1517_TECHNICAL_BRIEF.md)** — Executive 12-question diligence response for 1517 Fund.
12. **[`V2_RESEARCH_DECISION_LEDGER.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_RESEARCH_DECISION_LEDGER.md)** — Complete historical ADRs updated with V2 post-diligence decisions (AD-012 through AD-021).
13. **[`V2_DOSSIER_CHANGELOG.md`](file:///home/bernieweb3/Downloads/agenticbernie/gibbrn/V2_DOSSIER_CHANGELOG.md)** — This document (Systematic V1 $\to$ V2 provenance ledger).
