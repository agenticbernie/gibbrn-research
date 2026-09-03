# AUDIT-09: Cross-Document Consistency and Contradiction Matrix

**Target Project:** GIBBRN  
**Auditing Body:** 1517 Fund Adversarial Diligence Committee  
**Standard:** Corpus-Wide Narrative, Numerical, and Architectural Alignment  

---

## 1. Executive Cross-Document Consistency Findings

A systematic cross-referencing of all 12 documents in the GIBBRN dossier was conducted to identify internal discrepancies, conflicting threshold targets, terminology drift, and contradictory milestone criteria.

### Diligence Finding:
> While the high-level narrative remains broadly coherent across documents, the dossier exhibits **subtle cross-document drift** in milestone gate thresholds (e.g., whether MDDD extension target is $2.0\times$ or $2.5\times$; whether Effect Gate latency target is $<15\text{ms}$ or $\le 30\text{ms}$), and in the exact definition of the Unauthorized-Effect Rate ($\text{UER} = 0.000$ vs. $\text{UER} \le 0.001$).

---

## 2. Comprehensive Contradiction Matrix

Table 9.1 documents every identified cross-document conflict and establishes the **single binding canonical version** for the project.

### Table 9.1: Corpus Contradiction and Harmonization Matrix

| Contradiction Topic | File A (Statement) | File B (Conflicting Statement) | Exact Nature of Conflict | Recommended Canonical Version (Binding) |
| :--- | :--- | :--- | :--- | :--- |
| **MDDD Extension Target** | `06_BENCHMARKS` (Sec 3.6):<br>*"MDDD increases by at least **2.5×** compared to baseline."* | `07_ROADMAP` (Gate M15):<br>*"MDDD $\ge$ **2.0×** the depth of baseline agents."* | Inconsistent target multiplier ($2.5\times$ vs. $2.0\times$). | **Canonical Target: $\ge 2.0\times$** (Log-Rank test $p < 0.01$). $2.5\times$ is overly aggressive for an 18-month pre-seed target. |
| **Effect Gate Latency Target** | `04_SYSTEM` (Sec 3.4):<br>*"Executed synchronously in **$<15\text{ms}$**."* | `07_ROADMAP` (Gate M3):<br>*"Event capture introduces **$\le 30\text{ms}$** latency overhead."* | Conflicting latency thresholds ($<15\text{ms}$ vs. $\le 30\text{ms}$). | **Canonical Target:** $\le 15\text{ms}$ for in-process memory checks; $\le 30\text{ms}$ for total end-to-end proxy overhead at Gate M3. |
| **Unauthorized-Effect Rate (UER)** | `06_BENCHMARKS` (Sec 2.2):<br>*"Target: $\text{UER} = 0.000$ (Zero tolerance)."* | `06_BENCHMARKS` (Sec 3.3) & `07_ROADMAP` (Gate M9):<br>*"Threshold: $\text{UER} \le 0.001$."* | Absolute zero ($0.000$) vs. bounded fraction ($\le 0.001$). | **Canonical Definition:** $\text{UER} \le 0.001$ (with 0 unauthorized executions observed in $N = 1,000$ test suite). |
| **Causal Reconstruction Rate (CRR)** | `06_BENCHMARKS` (Sec 3.2):<br>*"Success Threshold: $\text{CRR} \ge 85\%$."* | `07_ROADMAP` (Gate M6):<br>*"Success Threshold: $\text{CRR} \ge 80\%$."* | Conflicting milestone success targets ($85\%$ vs. $80\%$). | **Canonical Threshold:** $\text{CRR} \ge 80\%$ at Gate M6 ($p < 0.01$, achieving $2\times$ over native tracing). |
| **Subsystem Count** | `04_SYSTEM` & `README`:<br>Proposes **5 distinct subsystems** (Spine, Authority, Admission, Gate, Recorder). | `AUDIT_05` & Synthesis:<br>Recommends consolidating into **3 core engines** (Spine, Gate, Admission). | Architectural bloat vs. consolidated implementation. | **Canonical Architecture:** Retain 5 conceptual subsystems in theoretical documentation, but group into **3 physical deployment engines** in implementation. |
| **MINJA Citation Metadata** | `01_PROBLEM`, `02_EVIDENCE`, `05_THREAT`:<br>Cited as `Z. Chen et al., arXiv:2402.04944, 2024`. | `AUDIT_02`:<br>Proves actual paper is `Shen Dong et al., NeurIPS, arXiv:2503.03704`. | Severe metadata error. | **Canonical Citation:** Shen Dong et al., "Memory Injection Attacks on LLM Agents via Query-Only Interaction," NeurIPS (arXiv:2503.03704). |
| **Research Scope (RQs)** | `06_BENCHMARKS` & `07_ROADMAP`:<br>Plans execution across **8 research questions (RQ1–RQ8)**. | `AUDIT_07` (Sec 5):<br>Proposes pruning to **5 essential RQs** (RQ1, RQ2, RQ3, RQ4, RQ6). | Over-scoped roadmap vs. realistic pre-seed bandwidth. | **Canonical Scope:** Core funding milestone gates evaluate **RQ1, RQ2, RQ3, RQ4, and RQ6**. RQ5, RQ7, and RQ8 are secondary exploratory tracks. |
| **Primary Capital Ask** | `08_BUDGET` & `10_BRIEF`:<br>Presents \$120k, \$285k, and \$480k plans equally. | `AUDIT_00` & `09_FOUNDER`:<br>Identifies \$120k as undercapitalized. | Ambiguity on which number is the real ask. | **Canonical Position:** **\$285,000 Target Pre-Seed Plan** is the primary funding ask; \$120,000 is an extreme single-researcher survival contingency. |

---

## 3. Mandatory Canonical Fact Sheet

To guarantee that all future investor presentations, papers, and code repositories are 100% synchronized, the following values are established as immutable project facts:

1.  **Project Name & Thesis:** GIBBRN is an *Agent State Integrity Layer for long-lived autonomous agents*.
2.  **North-Star Motto:** *"Agents can change. Their integrity must persist."*
3.  **Core Systems Question:** *"Which agent state may safely remain probabilistic and model-maintained, and which state must be canonical, deterministic, provenance-preserving, validated, versioned, and externally enforced?"*
4.  **State Classes (Exactly 4):** Cognitive ($\mathcal{S}_{\text{cog}}$), Operational ($\mathcal{S}_{\text{ops}}$), Authoritative ($\mathcal{S}_{\text{auth}}$), and Runtime/Safety ($\mathcal{S}_{\text{safe}}$).
5.  **Target Pre-Seed Capital Ask:** **\$285,000** over 18 months.
6.  **Core Milestone Gate Targets:**
    - *Gate M3:* Synchronous interception overhead $\le 30\text{ms}$.
    - *Gate M6:* Causal Reconstruction Rate $\text{CRR} \ge 80\%$.
    - *Gate M9:* Unauthorized-Effect Rate $\text{UER} \le 0.001$, False-Denial Rate $\text{FDR} \le 2.0\%$.
    - *Gate M12:* False-Promotion Rate $\text{FPR} \le 0.02$, Downstream retention $\ge 98\%$.
    - *Gate M15:* Kaplan-Meier survival curve extension $\text{MDDD}_{0.90} \ge 2.0\times$ baseline ($p < 0.01$).
    - *Gate M18:* Cross-runtime validation and formal Pilot Staging.
