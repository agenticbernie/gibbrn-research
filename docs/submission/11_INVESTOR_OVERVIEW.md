# gibbrn — Investor Overview (One Page)

**Thesis in one line:** GIBBRN investigates continuity and integrity for long-lived adaptive agents — how they can change models, runtimes, skills, tools, collaborators, and environments while preserving canonical identity, authority, provenance, validated competence, objective integrity, and consequence integrity.

**Program:** 36-Month Systems Research & Prototype Program — 3 arcs, 12 RQs, 12 quarterly gates (M3–M36), ~24 checkpoints; four major thesis gates (M9, M18, M24, M36). Year 3 is conditional on M24.

**Status:** Pre-prototype, checkpoint-gated R&D proposal. No measured results, customers, partners, or revenue are claimed. Full protocols: `06_CORE_RESEARCH_PROGRAM.md`; gates: `07_36_MONTH_ROADMAP.md`; financing: `08_CAPITAL_PLAN.md` (V4.2 rebase); diligence brief: `10_1517_TECHNICAL_BRIEF.md`.

---

## 1. What is the specific problem?
Long-lived agents conflate probabilistic model scratchpads with canonical system state. Four failure modes compound over deep trajectories: epistemic drift (lossy context compression), authority laundering (permissions rewritten inside prompt context), memory/skill poisoning (flawed heuristics persisted; e.g. MINJA query-only injection, Dong et al., NeurIPS 2025), and cascading state-dependent errors (early deviations escalate downstream hazard). Continuity failures compound further: identity discontinuity across migration, silent objective redefinition, authority widening across transformations, consequence mismatch, and coordination-state loss on team change.

## 2. Who has this problem?
Platform/infra engineers shipping agents with shell, API, or database access; DevOps teams running long-horizon automation; agent-framework maintainers handling authorization, sandboxing, and memory lifecycle. Grounded via 10–15 proposed discovery interviews in M01–M03 (no partners pre-claimed).

## 3. What is gibbrn's insight and hypothesis?
**Insight:** the agent stack decouples into mutable cognition, execution substrate, and an externally governed trust substrate — and long-lived agents additionally need continuity across change. **Hypothesis (H1):** on tasks requiring dynamic exploratory branching, a deterministic authority and state-integrity layer measurably extends trajectory survival and adaptation portability while maintaining near-zero unauthorized effects and preserving mechanical continuity and objective integrity — without modifying model weights. **Null (H0):** no significant gain, or friction negates it. The sharpest counter-case (pre-wired static DAGs suffice) is the program's falsification test.

## 4. What exists today, and what evidence?
A specified architecture (three engines: Causal & Continuity State Spine; Deterministic Effect Gate / Consequence Integrity Pipeline wedge — out-of-process interceptor + Tool Network Authority Broker + short-lived single-use leases + gVisor micro-sandboxes + effect reconciliation; Procedural Skill Compilation & Verified Adaptation Engine for procedural-family Python/Bash skills under judge-advisory commit semantics), a 12-question falsifiable protocol suite (RQ1–RQ12), and 12 binding gates (M3–M36). Evidence for the *problem* comes from cited literature (reflection limits, MINJA, HarnessDev portability deficit, plus the September 2026 delta: SkillGLoW, PROCTOR, Enoch migration, Aspire, EmbodiedSkills, CONTINUITY, CVE-2026-85666, interchangeability, swarm governance signal, Puffin-World, spectral-latent, τ^τ-Bench — see `02_EVIDENCE_LANDSCAPE.md` §3); evidence for the *solution* does not yet exist — that is what the program buys.

## 5. What is still unknown?
Whether checkpoint/rollback jointly improves the failure–completion–depth profile (CIF-based: fatal-failure incidence down, completion non-inferior, MDID₀.₉₀ ≥2.0× vs conventional controls, C vs B canonical; RQ6 power TBD via simulation); whether regression-gated skill admission runs fast/cheap enough; whether developers adopt an out-of-process daemon; whether adaptations transfer or must be bounded (ATR); whether migration preserves mechanical continuity; whether objective integrity holds under adaptive optimization; whether Year-3 team/governance/state hypotheses survive conditional gates. Each maps to a kill/narrow threshold in Table 6.2 (RQ1–RQ7 numeric; RQ8–RQ12 calibrated at pilot) — frozen at pre-registration before data collection; nothing is preregistered yet.

## 6. What is the first experiment (Days 1–90, proposed)?
Phase 1 (State / identity / Goal Contract semantics + minimal interceptor): out-of-process interceptor for a defined set of synchronous file-write and shell-tool operations (supported-ops list + known bypass paths documented; not all-syscall control); overhead distribution (median + p95); RQ1 paired sample (200 SWE-bench Lite tasks); first 200-attack RQ3 pilot slice with Clopper-Pearson/Wilson bounds; first tranche of 5–8 discovery interviews (of 10–15 total by day 90); Gate M3 evidence package. Full plan in `08_CAPITAL_PLAN.md` §8.

## 7. Founder note — Bernie Nguyen

> I'm Bernie Nguyen, a Ho Chi Minh City–based engineer with an Information Technology engineering degree. I interned as a backend developer at CommandOSS and now work as a community developer across build-in-public, agentic AI, and Web3.
>
> Two experiences drive gibbrn. While using AI coding agents, I watched context compaction silently drop agreed requirements and constraints. During my internship, a coding agent edited other engineers' configuration while fixing an unrelated problem — colleagues reminded me of the change. Memory-poisoning research convinced me agent memory is an attack surface worth taking seriously; tracing state through LangGraph and AutoGen showed me debugging without lineage is painful. I have not independently reproduced a memory-poisoning attack, and I don't claim every state model is broken.
>
> My work is public: [ourdash](https://github.com/agenticbernie/ourdash), a typed Python SDK for Dash at v0.1.0 with deliberately narrow scope, and [AeroTwin AI](https://github.com/agenticbernie/aerotwin-ai), where I led backend, system design, and architecture for a local-first airline Ops copilot — Top 5 shortlisted in its Aviation track at Agentic AI Build Week 2026, per the team; parts of that repo remain planning or handoff, not production.
>
> I spend 4–6 hours daily on gibbrn (6–10 on some rest days), alongside other commitments. Unproven: whether external integrity controls extend agent survival under adversarial pressure — what this program tests, with kill criteria I will honor.

## 8. What does the capital buy?
**Current Financing Target:** **$450,000 through M24** — Year 1 + Year 2, Gates M3–M24, ending at the Objective-Integrity / Arc-III-readiness major gate.

**Modeled Full Program Capitalization:** **~$700,000 over 36 months.**

**Conditional Year-3 Extension:** **~$250,000, activated only if M24 evidence justifies Arc III** (RQ9–RQ12, external validation, M36-A scientific + M36-B company verdicts).

High-level Stage-1 use of funds ($450k): founder $120k; engineering $70k; stats/annotation $25k; compute $55k; infra $36k; security/evaluation $35k; hardware $18k; legal/ops $14k; dissemination $9k; partner prep $8k; contingency $60k (full bottom-up model: `08_CAPITAL_PLAN.md` §§2–§4). Each gate publishes evidence per its to-be-preregistered protocol (planning map in Table 6.2; no protocol preregistered as of this dossier); failures trigger Narrow/Pivot/Stop with unspent funds subject to investor governance (separate agreement required; no return promised). Gates are scientific review points, not financing tranches. 1517 fit: R&D/idea-through-Seed, deep-tech/sci-fi, "who over what"; first checks $50k–$1M per 1517fund.com.

## 9. Three-year progression

- **YEAR 1 — ACT SAFELY:** Can one adaptive agent act safely? (State, causality, authority + consequence, verified skills.)
- **YEAR 2 — CHANGE SAFELY:** Can that agent change safely? (Portability, survival, migration, objective integrity.)
- **YEAR 3 — PERSIST TOGETHER (conditional):** Can persistent agents operate together and remain governable? (Environment state, team continuity, governance, integration.)

> **Agents can change. Their integrity must persist.**
