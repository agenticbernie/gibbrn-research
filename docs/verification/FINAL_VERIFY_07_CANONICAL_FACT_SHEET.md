# FINAL_VERIFY_07 — Canonical Fact Sheet

**Project:** GIBBRN Dossier V2  
**Purpose:** Single authoritative reference for every fact, number, and claim approved for use in SUBMISSION_*.md files  
**Audit Date:** September 2026  
**Status:** All items in this sheet have been verification-checked. Items marked ⚠️ carry explicit caveats that must appear when used.

> **SUPERSEDED SCOPE NOTICE (September 5, 2026 — do not delete):** This sheet describes the **V2 scope** (USD 285,000 / 18 months / 5 RQs) and is retained as history. The current canonical scope is **V3: USD 400,000 / 24 months / 7 RQs (RQ1–RQ7) / 16 checkpoints / 8 gates (M3–M24) / $150,000 fallback** (see `docs/submission/00_README.md`, AD-022/AD-023, changelog CHG-025). Do not cite V2 figures from this sheet as current. Engine 3 canonical name is now "Verified Adaptation Engine" (not "Experience Admission Engine").  

---

## Part A: Project Identity

| Fact | Canonical Value | Notes |
| :--- | :--- | :--- |
| Project name | gibbrn (lowercase) | Always lowercase in body text; may be GIBBRN in document headers/titles |
| Primary thesis | "gibbrn investigates Agent State Integrity for long-lived autonomous agents." | Verbatim |
| North-Star Principle | "Agents can change. Their integrity must persist." | Verbatim |
| Initial Technical Wedge | "Deterministic Authority and Effect Integrity" | The Effect Gate is the narrow Phase 1 wedge |
| Stage | R&D-stage technical hypothesis (pre-prototype) | Cannot imply customers, traction, validated results |
| Primary capital ask | USD 285,000 over 18 months | Budget assumption, not a negotiated figure |
| Constrained fallback | USD 120,000 | High-risk solo-founder scenario; severe scope loss |
| Team described | "Principal Systems Researcher + half-time Research Systems Engineer" | Not named in public documents |

---

## Part B: Architecture — Canonical Definitions

| Engine | Canonical Name | Key Components | Classification |
| :--- | :--- | :--- | :--- |
| Engine 1 | The Causal State Spine | PostgreSQL 16/SQLite WAL, Merkle DAG, SHA-256 parent chaining, checkpoint snapshots, effect receipts | Engineering Design |
| Engine 2 | The Deterministic Effect Gate | Out-of-process Rust/Go daemon, Unix domain socket IPC, single-use capability leases TTL ≤ 2000ms, gVisor micro-sandboxes, seccomp filters | Engineering Design — PRIMARY WEDGE |
| Engine 3 | The Experience Admission Engine | Git quarantine staging, 20-task regression suite, gVisor micro-sandbox runner, operational state promotion | Engineering Design |

**All engine specifications are ENGINEERING DESIGN TARGETS, not measured performance.**

---

## Part C: Canonical Citation References (Corrected)

| Reference Key | Corrected Citation | Status |
| :--- | :--- | :--- |
| MINJA / Dong2025 | S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, "Memory Injection Attacks on LLM Agents via Query-Only Interaction," *Proc. NeurIPS*, 2025. arXiv:2503.03704. | ✅ VERIFIED — **NeurIPS 2025**, NOT 2024 |
| AGENTERRORBENCH / Zhu2025 | Zhu et al., "Where LLM Agents Fail and How They can Learn From Failures," 2025. (AgentDebug / AgentErrorBench; 200 annotated failure trajectories from ALFWorld, GAIA, WebShop.) | ⚠️ Correct authorship; full arXiv ID to be confirmed at print |
| SWE-AGENT / Yang2024 | J. Yang, C. E. Jimenez, A. Wettig, K. Lieret, S. Yao, K. Narasimhan, and O. Press, "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering," *Proc. NeurIPS*, vol. 38, 2024. arXiv:2405.15793. | ✅ VERIFIED — first author is Yang, not Jimenez |
| AGENTLESS / Xia2024 | C. S. Xia, Y. Ding, L. Zhang, and T. Zhang, "Agentless: Demystifying LLM-based Software Engineering Agents," arXiv:2407.01489, 2024. | ✅ VERIFIED — first author is Chunqiu Steven Xia ("C. S. Xia") |
| SELFCORRECT / Huang2024 | J. Huang, X. Chen, S. Mishra, H. S. Zheng, A. W. Yu, X. Song, and D. Zhou, "Large Language Models Cannot Self-Correct Reasoning Yet," *ICLR*, 2024. | ✅ VERIFIED — title, venue, year, authors confirmed |
| PLANNING / Valmeekam2023 | K. Valmeekam, M. Marquez, S. Sreedharan, and S. Kambhampati, "On the Planning Abilities of Large Language Models: A Critical Investigation," *Proc. NeurIPS*, 2023. | ✅ VERIFIED — 4 authors in NeurIPS proceedings (A. Olmo in arXiv preprint only) |
| REFLEXION / Shinn2023 | N. Shinn, F. Cassano, E. Berman, A. Gopinath, K. Narasimhan, and S. Yao, "Reflexion: Language Agents with Verbal Reinforcement Learning," *Proc. NeurIPS*, 2023. | ✅ VERIFIED |
| OWASP-ASI06 | OWASP GenAI Security Project, "OWASP Top 10 for Agentic AI Applications," v1.0, December 2025. ASI06: Memory & Context Poisoning. | ✅ VERIFIED — official v1.0, December 2025 (not "community draft") |
| GPT4 / Achiam2023 | A. Achiam et al., "GPT-4 Technical Report," arXiv:2303.08774, 2023. | ✅ VERIFIED |
| GEMINI2023 | Gemini Team, "Gemini: A Family of Highly Capable Multimodal Models," arXiv:2312.11805, 2023. | ✅ VERIFIED |
| GENERATIVEAGENTS / Park2023 | J. S. Park et al., "Generative Agents: Interactive Simulacra of Human Behavior," *ACM UIST*, 2023. | ✅ VERIFIED |
| MEMGPT / Packer2023 | C. Packer et al., "MemGPT: Towards LLMs as Operating Systems," arXiv:2310.08560, 2023. | ✅ VERIFIED |
| AUTOGEN / Wu2023 | C. Wu et al., "AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation Framework," arXiv:2308.08155, 2023. | ✅ VERIFIED |
| FAITHFATE / Dziri2023 | N. Dziri et al., "Faith and Fate: Limits of Transformers on Compositionality," *Proc. NeurIPS*, 2023. | ✅ VERIFIED |
| PROMPTINJECT / Perez2022 | F. Perez and I. Ribeiro, "Ignore Previous Prompt: Attack Techniques For Language Models," arXiv:2211.09527, Nov 2022 (ML Safety Workshop, NeurIPS 2022). | ⚠️ CORRECTED Sept 2026 — earlier revisions listed arXiv:2305.14874, which is an unrelated paper |
| LAMPORT1978 | L. Lamport, "Time, Clocks, and the Ordering of Events in a Distributed System," *Commun. ACM*, vol. 21, no. 7, pp. 558–565, July 1978. | ✅ VERIFIED — classic |
| BERNSTEIN1987 | P. A. Bernstein, V. Hadzilacos, and N. Goodman, *Concurrency Control and Recovery in Database Systems*, Addison-Wesley, 1987. | ✅ VERIFIED — classic |

### REMOVED / RETIRED Citations

| Reference | Original Attribution | Status |
| :--- | :--- | :--- |
| "T. Xie et al., arXiv:2407.01505" | Attributed as AgentErrorBench | 🔴 REMOVED — incorrect author and arXiv ID |

---

## Part D: Approved Numerical Claims

| Claim | Canonical Value | Classification | Approved Use |
| :--- | :--- | :--- | :--- |
| Primary capital ask | USD 285,000 | FINANCIAL PLAN | V2_08, V2_10 |
| Constrained capital fallback | USD 120,000 | FINANCIAL PLAN | V2_08 |
| Principal stipend | $5,000/month ($90,000 total) | BUDGET ASSUMPTION | V2_08 |
| Engineer stipend | $3,000/month half-time ($54,000 total) | BUDGET ASSUMPTION | V2_08 |
| API compute budget | $48,000 (budget assumption at ~$4.50/1M tokens, September 2026) | BUDGET ASSUMPTION | V2_08 |
| Total inference tokens | ~10.63B across 13,200 trajectories | BUDGET CALCULATION | V2_08 |
| Capability token TTL | ≤ 2000ms | ENGINEERING TARGET | V2_03, V2_04, V2_05 |
| Effect Gate total latency | ≤ 14ms synchronous (≤ 30ms end-to-end) | ENGINEERING TARGET | V2_04, V2_07 |
| UER gate threshold | ≤ 0.001 (target: 0.000) | RESEARCH GATE CRITERION | V2_06, V2_07 |
| FDR gate threshold | ≤ 2.0% | RESEARCH GATE CRITERION | V2_06, V2_07 |
| State corruption reduction | ≥ 80% hypothesis | RESEARCH HYPOTHESIS | V2_06 |
| CRR hypothesis | ≥ 80% | RESEARCH HYPOTHESIS | V2_06 |
| Experience admission retention | ≥ 98% | RESEARCH HYPOTHESIS | V2_06 |
| MDDD doubling | ≥ 2.0× baseline | RESEARCH HYPOTHESIS | V2_06, V2_07, V2_10 |
| MINJA attack success | ">85% in evaluated configurations" | LITERATURE VALUE (Dong et al., NeurIPS 2025) — configuration-dependent | V2_02, V2_10 |
| Regression tasks | 20 canonical tasks per candidate skill | ENGINEERING DESIGN | V2_04, V2_07 |
| Sample sizes | RQ1:200, RQ2:150, RQ3:1000, RQ4:300, RQ5:150 | RESEARCH DESIGN | V2_06 |
| SWE-bench Lite total | 300 instances; 200-task subset used | BENCHMARK FACT | V2_06 |
| Agentless resolve rate | 32% on SWE-bench Lite with GPT-4o (gpt-4o-2024-05-13) | LITERATURE VALUE (Xia et al. 2024) | V2_02 |
| Seed round forecast | $3M–$4M, conditional on Gate M15 pass | FORECAST / SCENARIO | V2_10 |
| 1517 Fund check range | $50k–$1M (average ~$400k pre-seed) | HISTORICAL SECONDARY-SOURCE FACT | V2_10 context only |

---

## Part E: Approved Language Formulations

The following phrasing is pre-approved and correctly classified:

**For design invariants:**
> "Invariant X is a Core Architectural Specification (Design Invariant). This is a formal software specification of the target implementation, not a claimed law of physics."

**For research hypotheses:**
> "We hypothesize that... [stated as formal H1 with null H0]. This is a pre-registered research claim to be tested at Gate [Mx]."

**For engineering targets:**
> "All latency figures in this table are Engineering Design Targets established prior to experimental validation. Actual measured performance will be reported in Gate [Mx] deliverables."

**For budget assumptions:**
> "Budget assumptions as of September 2026. Token API pricing is sensitive to market changes; Scenario B in §4 addresses the inflation case."

**For competitor claims:**
> "[System X] public documentation, reviewed for this audit, does not describe native support for [feature Y]."

**For MINJA citation:**
> "Dong et al. (NeurIPS 2025) demonstrate that MINJA memory injection attacks achieve >85% success across evaluated configurations (medical/EHR, e-commerce, and QA agent settings), enabling query-only persistence of malicious instructions across sessions."

**For harness-sensitivity claim (replacing 27.4pp):**
> "Research across SWE-bench evaluations (Yang et al., NeurIPS 2024; Xia et al., 2024) demonstrates that different agentic scaffolding architectures yield substantially different resolution rates on the same benchmark — differences on the order of tens of percentage points have been observed in the literature. These comparisons are not fully controlled experiments; scaffolding, prompt design, and model selection co-vary. The magnitude of observed differences motivates gibbrn's investigation of harness-level state semantics as a significant independent variable."

---

## Part F: Terms That Are FORBIDDEN in Submission Files

| Forbidden Phrase | Reason | Replacement |
| :--- | :--- | :--- |
| "100% Verified Primary Literature" | Self-certifying; factually violated | "Primary-source evidence landscape" |
| "Zero Hallucinated Citations" | Self-certifying; factually violated (AgentErrorBench) | Remove entirely |
| "rendering credential theft impossible" | Absolute security claim without threat model scope | "substantially reduces exfiltration surface within scoped threat model" |
| "physically incapable" (re: model writing auth state) | Wrong epistemic qualifier | "architecturally isolated" |
| "zero concept of" (re: competitor capabilities) | Absolute competitor claim | "public documentation does not describe native support for" |
| "proves" (re: 27.4pp harness claim) | Overstates multi-paper observation | "demonstrates / suggests / is consistent with" |
| "Harness Dominance Effect (Causally Established)" | Invented label + overstatement | "Harness Architecture Sensitivity (Observed Across Literature) [GIBBRN label]" |
| "NeurIPS 2024" for Dong et al. MINJA | Year error | "NeurIPS 2025" |
| "T. Xie et al., arXiv:2407.01505" | Fabricated citation | Zhu et al. (2025) AgentDebug |
| ">70% of enterprise tasks" (unsourced) | Unsourced market claim | "majority of well-specified deterministic enterprise tasks (proportion not established by primary study)" |
| "Claude 3.5 Sonnet" (model name in experimental design) | Version hygiene violation | "Tier 2 Frontier Coding Model (version frozen at experiment start)" |
| "Gemini 2.0 Flash" (model name in experimental design) | Version hygiene violation | "Tier 2 Google Frontier Model (version frozen at M16)" |

---

> **Agents can change. Their integrity must persist.**
