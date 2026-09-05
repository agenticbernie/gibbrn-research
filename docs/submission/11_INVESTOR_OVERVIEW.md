# gibbrn — Investor Overview (One Page)

**Thesis in one line:** gibbrn investigates whether a framework-neutral control layer can preserve the integrity, authority, provenance, and recoverability of consequential agent state as autonomous agents operate and change over time.

**Status:** Pre-prototype, checkpoint-gated R&D proposal. No measured results, customers, partners, or revenue are claimed. Full protocols: `06_CORE_RESEARCH_PROGRAM.md`; gates: `07_24_MONTH_ROADMAP.md`; budget: `08_CAPITAL_PLAN.md`; diligence brief: `10_1517_TECHNICAL_BRIEF.md`.

---

## 1. What is the specific problem?
Long-lived agents conflate probabilistic model scratchpads with canonical system state. Four failure modes compound over deep trajectories: epistemic drift (lossy context compression), authority laundering (permissions rewritten inside prompt context), memory/skill poisoning (flawed heuristics persisted; e.g. MINJA query-only injection, Dong et al., NeurIPS 2025), and cascading state-dependent errors (early deviations escalate downstream hazard).

## 2. Who has this problem?
Platform/infra engineers shipping agents with shell, API, or database access; DevOps teams running long-horizon automation; agent-framework maintainers handling authorization, sandboxing, and memory lifecycle. Grounded via 10–15 proposed discovery interviews in M01–M03 (no partners pre-claimed).

## 3. What is gibbrn's insight and hypothesis?
**Insight:** the agent stack decouples into mutable cognition, execution substrate, and an externally governed trust substrate. **Hypothesis (H1):** on tasks requiring dynamic exploratory branching, a deterministic authority and state-integrity layer measurably extends trajectory survival and adaptation portability while maintaining near-zero unauthorized effects — without modifying model weights. **Null (H0):** no significant gain, or friction negates it. The sharpest counter-case (pre-wired static DAGs suffice) is the program's falsification test.

## 4. What exists today, and what evidence?
A specified architecture (three engines: Causal State Spine; Deterministic Effect Gate wedge — out-of-process interceptor + short-lived single-use leases + gVisor micro-sandboxes; Verified Adaptation Engine for verifier-rich Python/Bash skills), a 7-question falsifiable protocol suite (RQ1–RQ7), and 8 binding gates (M3–M24). Evidence for the *problem* comes from cited literature (reflection limits, MINJA, HarnessDev portability deficit); evidence for the *solution* does not yet exist — that is what the program buys.

## 5. What is still unknown?
Whether checkpoint/rollback doubles survival depth (MDDD₀.₉₀ ≥2.0×); whether regression-gated skill admission runs fast/cheap enough; whether developers adopt an out-of-process daemon; whether adaptations transfer or must be bounded (ATR); whether IAM-bound integrity holds live. Each maps to a proposed kill/narrow threshold in Table 6.2 — frozen at pre-registration before data collection; nothing is preregistered yet.

## 6. What is the first experiment (Days 1–90, proposed)?
Phase 1 (State Semantics + minimal interceptor): out-of-process interceptor for a defined set of synchronous file-write and shell-tool operations (supported-ops list + known bypass paths documented; not all-syscall control); overhead distribution (median + p95); RQ1 paired sample (200 SWE-bench Lite tasks); first 200-attack RQ3 pilot slice with Clopper-Pearson/Wilson bounds; first tranche of 5–8 discovery interviews (of 10–15 total by day 90); Gate M3 evidence package. Full plan in `08_CAPITAL_PLAN.md` §8.

## 7. Founder note — Bernie Nguyen

> I'm Bernie Nguyen, a Ho Chi Minh City–based engineer with an Information Technology engineering degree. I interned as a backend developer at CommandOSS and now work as a community developer across build-in-public, agentic AI, and Web3.
>
> Two experiences drive gibbrn. While using AI coding agents, I watched context compaction silently drop agreed requirements and constraints. During my internship, a coding agent edited other engineers' configuration while fixing an unrelated problem — colleagues reminded me of the change. Memory-poisoning research convinced me agent memory is an attack surface worth taking seriously; tracing state through LangGraph and AutoGen showed me debugging without lineage is painful. I have not independently reproduced a memory-poisoning attack, and I don't claim every state model is broken.
>
> My work is public: [ourdash](https://github.com/agenticbernie/ourdash), a typed Python SDK for Dash at v0.1.0 with deliberately narrow scope, and [AeroTwin AI](https://github.com/agenticbernie/aerotwin-ai), where I led backend, system design, and architecture for a local-first airline Ops copilot — Top 5 shortlisted in its Aviation track at Agentic AI Build Week 2026, per the team; parts of that repo remain planning or handoff, not production.
>
> I spend 4–6 hours daily on gibbrn (6–10 on some rest days), alongside other commitments. Unproven: whether external integrity controls extend agent survival under adversarial pressure — what this program tests, with kill criteria I will honor.

## 8. What does the capital buy?
**USD 400,000 / 24 months** (primary) or **USD 150,000 / 12-month pilot** (M3–M12 fallback, preliminary): founder compensation ($120k proposed), contingent engineering ($72k), compute ($62k), infra ($36k), hardware ($24k), red-team/evaluation ($18k), legal/IP ($9k), dissemination ($7k), reserve ($52k). Each gate publishes evidence per its to-be-preregistered protocol (planning map in Table 6.2; no protocol preregistered as of this dossier); failures trigger Narrow/Pivot/Stop with unspent funds subject to investor governance (separate agreement required; no return promised). 1517 fit: R&D/idea-through-Seed, deep-tech/sci-fi, "who over what"; first checks $50k–$1M per 1517fund.com.

> **Agents can change. Their integrity must persist.**
