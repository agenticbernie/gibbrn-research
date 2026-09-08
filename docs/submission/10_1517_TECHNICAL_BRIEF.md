# 10 — 1517 Fund Investor Technical Brief (Submission)

**Project Name:** GIBBRN  
**Document Track:** Executive Investor Diligence & Systems Brief  
**Date:** September 2026 | **Dossier Version:** 4.2 (36-Month Systems Research & Prototype Program)  
**Target:** 1517 Fund Investment Committee  
**Standard:** 12 Direct Diligence Responses (Post-Adversarial Diligence; V4-Evidence Update)

---

### 1. What is gibbrn?
**GIBBRN investigates continuity and integrity for long-lived adaptive agents.** Technically, it is a proposed framework-neutral persistent control plane designed to preserve canonical identity, authority, provenance, validated competence, objective integrity, and end-to-end consequence integrity as autonomous systems change models, runtimes, skills, tools, collaborators, and environments over time.

> **GIBBRN is a continuity and consequence-integrity substrate for adaptive agents: cognition may change, while identity, delegated authority, verified operational knowledge, and the chain from principal intent to external consequence remain externally governed and auditable.**

North star (retained): *Agents can change. Their integrity must persist.*

---

### 2. What changed in V4 (24-month V3 → 36-month V4)?
1.  **Positioning:** from "Agent State Integrity" to **continuity + integrity for long-lived adaptive agents**, with a new north-star RQ (change everything without losing identity/objective/competence/authority/consequence integrity). The V3 probabilistic-vs-canonical question is retained as subordinate RQ1.
2.  **Evidence:** September 6–8, 2026 delta — 13 newly verified evidence entries, prioritizing primary sources, across 7 clusters (persistent identity, procedural abstraction, verifier-gated execution, objective operationalization, multi-agent coordination, security-context continuity, decision-sufficient state). Full per-source establish / not-establish / implication analysis in `02_EVIDENCE_LANDSCAPE.md` §3.
3.  **Architecture discipline kept:** still **three physical engines** — Causal & Continuity State Spine; Deterministic Effect Gate / Consequence Integrity Pipeline (+ Tool Network Authority Broker design response); Procedural Skill Compilation & Verified Adaptation Engine. Goal Contract, migration, team-state, world-state, governance are conceptual layers, not new daemons.
4.  **Program shape:** 7 RQs / 8 gates → **12 RQs across 3 arcs / 12 quarterly gates / ~24 checkpoints**, with four major thesis gates (M9, M18, M24, M36). Year 3 is conditional on M24. New RQs carry candidate metrics with thresholds TBD at pilot calibration — no fabricated numbers.
5.  **Capital rebase (V4.2, founder-authorized):** **$450k current financing through M24**; **~$700k modeled program capitalization**; **~$250k M24-conditional Year-3 extension**. V3 $400k/$150k figures retained as history only (`08_CAPITAL_PLAN.md` Appendices H1–H3).

---

### 3. What is the narrow initial technical wedge?
**Deterministic Authority and Consequence Integrity.**
We are researching how an autonomous agent can change its probabilistic cognitive reasoning without silently changing what it is authorized to do in the external world — and whether the realized effect matches what was authorized. The wedge is an out-of-process reference monitor that intercepts proposed tool mutations, resolves endpoint/network/credential authority in the control plane (not the caller), binds bounded execution permits, contains execution in ephemeral gVisor micro-sandboxes, and reconciles effect receipts against authorization witnesses.

---

### 4. What empirical evidence supports the problem?
*   **Harness Architecture Sensitivity:** Yang et al. (NeurIPS 2024; SWE-agent) and Xia et al. (2024; Agentless) demonstrate that different agentic scaffolding architectures yield substantially different resolution rates on the same coding benchmark — differences on the order of tens of percentage points have been observed across the SWE-bench literature. These comparisons are not fully controlled experiments (scaffolding, prompting, and model selection co-vary), but the scale of sensitivity motivates gibbrn's investigation of harness-level state design as a significant variable.
*   **Reflection Instability:** Jie Huang et al. (ICLR 2024) and Valmeekam et al. (NeurIPS 2023) demonstrate that model self-reflection is non-monotonic and prone to ungrounded confirmation bias without external symbolic verification.
*   **Memory Poisoning:** S. Dong et al. (NeurIPS 2025; arXiv:2503.03704) demonstrate query-only memory injection (MINJA), reporting ~98.2% malicious-record injection and ~76.8% attack success averaged across evaluated agents and victim-target pairs (EHR, e-commerce, QA settings; configuration-dependent — not a universal rate).
*   **Harness Portability Deficit:** HarnessDev (Wu et al., arXiv:2609.01437, Sept 2026; 6 creators, 2,207 instances) finds generated harnesses lag human-engineered references on code/search while matching/exceeding on writing/ML experiments, with evolution gains shrinking on held-out tasks and exhibiting executor dependence — motivating RQ5.
*   **V4 additions (all preprints unless noted; see `02` §3 for limitations):** procedural-family transfer with execution-gated admission (SkillGLoW, +17.2 hard avg, 73.9→83.9% ALFWorld transfer); judge-advisory PROCTOR discipline (100% nominal vs 68% true case); mechanical migration continuity precedent (833 + 92 tests; behavioral invariance explicitly disclaimed); vague-goal operationalization gaps (Aspire, 520 hidden items, six goals); verifier-centric execution precedent with memory weakness signal (EmbodiedSkills, 86.20% / 97.40% execution, 12.5% memory tasks); security-context discontinuity framework (CONTINUITY, 2,560 attacks / 700 benign / 200 ambiguous); endpoint-authority confusion in the wild (CVE-2026-85666, OGX SSRF, CVSS 4.0 8.7 — narrow lesson, not a claim about MCP generally); team tacit-state costs (swaps +16–63% comms/unit progress); governance-relevant swarm behavior as a weak signal (100-agent case study — no society claims); decision-sufficient-state hypothesis grounding (Puffin-World 15M+1M; spectral-latent laziness finding); autonomous-construction humility (τ^τ-Bench 23.9% vs 82.2% reference).
*   **Who experiences this:** platform/infra engineers shipping agents with shell/API/DB access, DevOps teams managing long-horizon automation, and agent-framework maintainers handling authorization and memory lifecycle. *Problem-discovery interviews (10–15, M01–M03) are proposed to ground this characterization; no partners are pre-claimed.*

**Status and what is already done:** This dossier is a *pre-prototype research proposal*. No prototype benchmarks, measured gate results, customers, partners, or revenue are claimed. What exists is the falsifiable protocol suite (RQ1–RQ12), architecture specification, and gate criteria in this repository.

---

### 5. What remains unproven?
1.  Whether external checkpointing and rollback can jointly improve the failure–completion–depth profile (fatal-failure incidence down, completion non-inferior, interaction depth MDID₀.₉₀ ≥2.0× vs conventional controls) on non-deterministic tasks.
2.  Whether automated regression testing for candidate skills can run fast enough ($<60\text{s}$) and cheap enough ($<3\times$ task cost) to be viable in continuous operation.
3.  Whether enterprise developers will adopt an out-of-process control daemon over ad-hoc in-process scripts.
4.  Whether migration preserves mechanical continuity without behavioral-identity overreach (RQ7).
5.  Whether broad-objective operationalization holds under the Goal Contract without silent redefinition (RQ8).
6.  Whether Year-3 multi-agent/environment hypotheses survive their conditional gates (RQ9–RQ12).

---

### 6. Why might existing stacks be insufficient?
*   **Temporal / DBOS:** Temporal's documented model (deterministic workflow code + non-deterministic activities memoized in Event History) supports LLM-driven dynamic branching at runtime and durable recovery. What it does not by itself provide, per public documentation reviewed, is agent-specific semantic validation of why a model proposed a given side effect or whether its in-context authority was laundered.
*   **Mem0 / Letta:** Focus on semantic similarity retrieval; public documentation reviewed does not describe native support for regression testing, sandboxed validation, or provenance isolation before memory promotion — architecturally exposed to analogous persistent-memory poisoning unless separately mitigated (the cited MINJA evaluations did not test these specific implementations).
*   **Lakera Guard / Guardrails:** Rely on probabilistic natural-language classifiers to scan prompts and outputs, operating at the text inspection layer rather than enforcing deterministic kernel sandboxing or state constraints.
*   **CONTINUITY framework:** the closest intellectual precedent for composed-control integrity — but a preprint reference verifier, not a deployable product with skill governance, migration continuity, or evaluation integrity.

---

### 7. Why might existing stacks actually be sufficient (The Counter-Case)?
If enterprise computing rejects open-ended autonomous agent loops entirely and converges on **rigid, deterministic DAGs (the Agentless paradigm)** where models are called only for narrow, single-step extractions, static pipelines will suffice. gibbrn exists to test whether there is a valuable task territory requiring dynamic exploratory branching that static pipelines cannot solve. τ^τ-Bench tempers both extremes: autonomous construction is currently weak (23.9%), which neither proves pipelines suffice nor that autonomy needs no controls.

---

### 8. What exactly will be tested over 36 months?
Twelve research questions across three arcs (full protocols: `06_CORE_RESEARCH_PROGRAM.md`):
*   *Arc I — ACT SAFELY (M1–M12):* RQ1 (state classification, ≥80% corruption reduction); RQ2 (causal + continuity reconstruction, CRR ≥80%); RQ3 (authority + consequence integrity — zero observed unauthorized effects across a $N=1{,}000$ red-team pilot, confirmatory $N \approx 3{,}000$ before any ≤0.001 claim; three-arm controls); RQ4 (procedural-family verified adaptation, FPR ≤0.02, retention ≥98%).
*   *Arc II — CHANGE SAFELY (M13–M24):* RQ5 (portability ATR ≥0.80 or safe bounding); RQ6 (joint CIF + MDID₀.₉₀ ≥2.0× vs conventional-controls arm, C vs B canonical); RQ7 (migration continuity — mechanical, not behavioral; conformance probes + negative cases; thresholds calibrated at pilot); RQ8 (contract integrity + operationalization fidelity under Goal Contract; thresholds calibrated at pilot).
*   *Arc III — PERSIST TOGETHER, conditional (M25–M36):* RQ9 (decision-sufficient state); RQ10 (team continuity); RQ11 (shared-state governance); RQ12 (integrated validation). All thresholds calibrated at pilot; each strand independently killable.

*First experiment (Days 1–90, proposed; Phase 1: State Semantics + minimal interceptor):* minimal out-of-process interceptor for a defined set of synchronous file-write and shell-tool operations (supported-ops list + known bypass paths documented; not all-syscall control), overhead distribution (median + p95), RQ1 paired sample, first 200-attack RQ3 pilot slice, first tranche of 5–8 discovery interviews (of 10–15 total by day 90), Gate M3 evidence package. Full plan in `08_CAPITAL_PLAN.md` §16; no results claimed.*

---

### 9. What are the twelve research checkpoint gates?
*   **Gate M3:** Interception overhead $\le 30\text{ms}$; state exceptions reduced by $\ge 80\%$.
*   **Gate M6:** Causal failure attribution rate $\text{CRR} \ge 80\%$.
*   **Gate M9 ★ (Main Wedge):** Zero observed unauthorized effects across the $N=1{,}000$ pilot (95% upper $\approx 0.003$); false denials $\le 2.0\%$ with non-straddling interval ($N_{\text{benign}}=500$ planning assumption); median ≤30ms with tail within proposed bound. Single failure → Narrow/Pivot; $>0.001$ or confirmed FDR/latency breach → STOP. Full disjoint rules in Table 6.2.
*   **Gate M12:** False-Promotion Rate $\text{FPR} \le 0.02$; downstream retention $\ge 98\%$.
*   **Gate M15:** Dual-mode satisfaction on portability (either portable transfer $\text{ATR} \ge 0.80$, or verified safe specialization bounding co-adaptation with zero downstream regressions).
*   **Gate M18 ★ (Scientific Gate):** Joint over C-vs-B, all CIF-based (Aalen–Johansen): $\text{MDID}_{0.90}$ ratio ≥2.0× (CI lower $> 1.5\times$) AND fatal-failure CIF reduced (Gray's $p < 0.01$ + $\Delta F_1(k^*)$ floor) AND completion non-inferior AND practicality review; Table 6.2. RQ6 power TBD via competing-risk simulation.
*   **Gate M21:** Migration continuity preserves lineage/contract/authority/skills per calibrated thresholds (no behavioral-identity claim required); narrow to single-runtime on failure.
*   **Gate M24 ★ (Year-2 Company Gate):** Objective integrity holds per calibrated thresholds; Arc III readiness review decides Year-3 activation.
*   **Gate M27 [conditional]:** Decision-sufficient variables justified per calibrated thresholds.
*   **Gate M30 [conditional]:** Coordination-state transfer reduces replacement cost per calibrated thresholds.
*   **Gate M33 [conditional]:** Governed sharing contains exploits per calibrated thresholds.
*   **Gate M36 ★ (M36-A scientific / M36-B company, independent):** Integrated validation (A) plus partner ROI/adoption verdict (B).

---

### 10. What does the requested capital buy?
**GIBBRN is currently seeking USD 450,000 to finance the research program through Month 24** — Year 1 (Act Safely) and Year 2 (Change Safely), Gates M3–M24, ending at the Objective & Evaluation Integrity / Arc-III-readiness major gate. The modeled full 36-month program requires approximately USD 700,000 in total capitalization; the remaining approximately USD 250,000 is expected to be raised and deployed only if the Month-24 scientific and Arc-III-readiness gates justify Year-3 expansion. GIBBRN is not raising $700,000 now.

What the $450k buys, gate by gate (evidence per gate; binding rules in Table 6.2):
*   **M3 ($~55k cumulative):** typed-state separation verdict (≥80% corruption reduction?) + interceptor overhead envelope + supported-ops/bypass documentation.
*   **M6:** causal-reconstruction verdict (CRR ≥80%?) + lineage-instrument (LRA) baseline for RQ7/RQ8 design.
*   **M9 ★ (wedge):** consequence-integrity pilot (0/1,000 + per-family bounds + fault-injection axis) qualifying the $N\approx3{,}000$ confirmatory phase.
*   **M12:** verified-admission verdict (FPR ≤0.02, retention ≥98%) + abstraction-metric baseline (yield/transfer/compression).
*   **M15:** portability-or-safe-bounding verdict (ATR ≥0.80 or bounded specialization).
*   **M18 ★ (scientific):** joint CIF/depth/completion/cost/latency verdict (C vs B) with simulation-backed power.
*   **M21:** migration-continuity verdict (conformance probes + negative cases; single-runtime fallback if failed).
*   **M24 ★ (Year-2/readiness):** objective-integrity verdict (contract + fidelity) + Arc III readiness review + design-partner validation start.

Bottom-up composition of the $450k (Stage 1): founder $120k; engineering $70k; stats/annotation $25k; compute $55k; infra $36k; security/evaluation $35k; hardware $18k; legal/ops $14k; dissemination $9k; partner prep $8k; contingency $60k (full split in `08_CAPITAL_PLAN.md` Table 8.2). Gates are founder-proposed scientific review points, not investor-agreed disbursement tranches; any gated release, escrow, or return mechanics require a separate agreement. No capital preservation or return is promised.

---

### 11. What result kills the thesis?
*   **At M9:** If capability tokens and kernel sandboxing fail to stop unauthorized mutating effects ($\text{UER} > 0.001$) or consequence integrity shows no advantage over conventional controls → narrow / pivot / stop the core company thesis.
*   **At M18:** If the joint failure–completion–depth profile shows no advantage for the GIBBRN arm (C) over conventional controls (B) — MDID ratio miss, no CIF reduction, or completion inferiority.
*   **At M24:** If objective integrity fails uncontained (contract redefinition or proxy-gaming uncontained), or Arc II as a whole does not support proceeding.
*   **At M36-A / M36-B:** If the integrated scientific thesis fails (A), or developers/partners show no ROI and no adoption path (B) — each verdict independent.

If a major gate fails, **we will stop pursuing the broad company thesis and either wind down the program or pursue only a narrower direction if supported by evidence and investor governance.** We will not pivot to a generic AI wrapper. Strand-level failures (M12→manual skills; M21→single-runtime; M27–M33→kill strand) never automatically kill the program — except at the four major gates above.

---

### 12. What result would justify a subsequent seed round?
A subsequent institutional Seed round at M36 (with an interim defensibility check at M24) would become defensible if gibbrn demonstrates:
1.  The pipeline maintains zero observed unauthorized effects across the $N=1{,}000$ pilot *and* the to-be-preregistered $N \approx 3{,}000$ confirmatory phase (one-sided 95% upper $\le 0.001$), with per-family bounds reported, FDR and latency within bounds and three-arm incremental value over conventional controls.
2.  gibbrn-managed adaptive agents achieve a to-be-preregistered, practically meaningful joint improvement (fatal-failure CIF down per Gray's test with the $\Delta F_1(k^*)$ floor met, $\text{MDID}_{0.90} \ge 2.0\times$ vs the conventional-controls arm with bootstrap CI lower $> 1.5\times$, all CIF-based) with completion non-inferior and cost/latency against proposed practicality triggers.
3.  Learned skills and harnesses either exhibit portable cross-model transfer ($\text{ATR} \ge 0.80$) or are verifiably constrained via safely bounded specialization without contaminating global state — with abstraction value (yield, family transfer, compression) documented separately from admission safety.
4.  Migration preserves mechanical continuity (conformance probes pass; incompatible migrations safely refused) and objective integrity holds on both axes — contract intact AND operationalization faithful — per their calibrated thresholds.
5.  External deployment evaluations (up to 2 partners recruited post-M18) confirm integration effort, ROI signal, and live-authority validation (M36-B company verdict, independent of the M36-A scientific verdict). No partners are pre-claimed.

### Founder note — Bernie Nguyen

> I'm Bernie Nguyen, a Ho Chi Minh City–based engineer with an Information Technology engineering degree. I interned as a backend developer at CommandOSS and now work as a community developer across build-in-public, agentic AI, and Web3.
>
> Two experiences drive gibbrn. While using AI coding agents, I watched context compaction silently drop agreed requirements and constraints. During my internship, a coding agent edited other engineers' configuration while fixing an unrelated problem — colleagues reminded me of the change. Memory-poisoning research convinced me agent memory is an attack surface worth taking seriously; tracing state through LangGraph and AutoGen showed me debugging without lineage is painful. I have not independently reproduced a memory-poisoning attack, and I don't claim every state model is broken.
>
> My work is public: [ourdash](https://github.com/agenticbernie/ourdash), a typed Python SDK for Dash at v0.1.0 with deliberately narrow scope, and [AeroTwin AI](https://github.com/agenticbernie/aerotwin-ai), where I led backend, system design, and architecture for a local-first airline Ops copilot — Top 5 shortlisted in its Aviation track at Agentic AI Build Week 2026, per the team; parts of that repo remain planning or handoff, not production.
>
> I spend 4–6 hours daily on gibbrn (6–10 on some rest days), alongside other commitments. Unproven: whether external integrity controls extend agent survival under adversarial pressure — what this program tests, with kill criteria I will honor.

---

> **Agents can change. Their integrity must persist.**
