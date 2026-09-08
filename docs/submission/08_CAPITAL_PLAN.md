# 08: Expense Modeling & Capital-at-Risk

**Document Track:** Financial Modeling & Capital Allocation (Version 4.0)  
**Date:** September 2026 | **Dossier Version:** 4.0 (36-Month Systems Research & Prototype Program)  
**Audience:** Deep-Tech Investors, 1517 Fund Partners, Technical Founders  

> **V4 CAPITAL STATUS — READ FIRST:** The V4 36-month capital model is **explicitly unresolved and requires founder-approved rebasing. No new funding number is introduced in this dossier version.** Sections §§1–§5 below preserve the **V3 historical capital plan (USD 400,000 / 24 months; USD 150,000 / 12-month fallback)** as history and planning context — they are NOT the V4 36-month budget. Section §9 records the rebasing decision, the structural sequencing changes that are made without inventing numbers, and the exact founder authorization required. Do NOT scale $400,000 / 24 months into $600,000 / 36 months or any other extrapolated figure.

> **Governance note:** Milestone reviews, gates, and "preserve remaining capital" language in this document are *founder-proposed* review mechanics. They are not investor-agreed disbursement tranches, escrow terms, or return guarantees. Any gated disbursement, escrow, or return mechanics require a separate written investor agreement. No capital preservation or return is promised beyond "unspent funds remain subject to investor governance."

## 1. [HISTORICAL — V3] The $400,000 / 24-Month Operating Budget

*Preserved V3 context (September 2026 review). This budget mapped to the 24-month program (RQ1–RQ7, Gates M3–M24). It does not fund the V4 36-month program.*

The $400,000 capital request was allocated to execute the 24-month research roadmap (RQ1–RQ7), culminating in Gate M24. It was capital mapped against a falsifiable research program, not an arbitrary runway.

### Table 8.1: [HISTORICAL — V3] Primary Resource Allocation (24 Months)

| Category | Item Description | 24-Month Allocation |
| :--- | :--- | :--- |
| **Human Capital** | Founder / Principal Researcher — proposed compensation ($5,000/mo × 24 mo) | $120,000 |
| **Human Capital** | Planned Hire / Contractor, part-time research engineering (contingent on funding; ~$3,000/mo equivalent) | $72,000 |
| **Compute** | Model Inference + Benchmark Compute (see §5 assumptions) | $62,000 |
| **Infrastructure** | Sandbox / DB / Observability (AWS/GCP) (see §5 assumptions) | $36,000 |
| **Operations** | Hardware / Tooling — unconfirmed allocation (no itemized list; device categories TBD by founder before procurement; no quotes claimed) | $24,000 |
| **Security** | Security / Red-Team / External Evaluation | $18,000 |
| **Operations** | Legal / Incorporation / IP | $9,000 |
| **Operations** | Research Dissemination / Travel | $7,000 |
| **Contingency** | Strategic Reserve / API Volatility Buffer (13.0%) | $52,000 |
| **TOTAL** | **Target Initial Capitalization [V3 HISTORICAL]** | **$400,000** |

*Note on Compensation:* Amounts are *proposed compensation* assumptions for a founder-led program with optional part-time research engineering support contingent on funding. No claim is made about cost of living or "subsistence" levels, which depend on location and personal circumstances not established in this dossier.

---

## 2. [HISTORICAL — V3] The $150,000 Constrained Fallback Plan (Preliminary — Not Fully Costed)

*Preserved V3 context. This fallback scoped the initial evidence gates (M3–M12) of the 24-month program. It is not a V4 Year-1 budget.*

If 1517 prefers to fund only the initial evidence gates (M3–M12) to de-risk the core Deterministic Effect Gate, a solo-founder 12-month pilot is sketched at **$150,000**. *This fallback is preliminary and has not been bottom-up costed to the same standard as Table 8.1; treat it as a scoping proposal, not a committed budget.*

*   **Kept (minimal controls, reduced scale — not single-arm):** a fallback that dropped every control arm could not support its own comparative claims, so the pilot keeps the smallest control that each gate's comparison needs: RQ1 paired design on 200 tasks × 2 arms (pairing is inherent to the McNemar comparison); RQ2 on 150 traces × 2 presentation conditions with the same annotation team; RQ3 arm-C pilot of 1,000 attacks plus reduced A/B spot-checks (100 each, descriptive — full characterization deferred); RQ4 on a single Latin-square order (100 tasks) × 2 arms (naive memory + gibbrn; order-robustness deferred); benign suite reduced to 300 (planning assumption, TBD). ≈1,450–1,750 evaluation units total. Deferred: contractor support, RQ5 transfer matrix, RQ6 survival, RQ7 delegation, confirmatory $N\approx3{,}000$, second model tier, external bounties (internal red-teaming only), most travel.
*   **Cut:** Contractor/engineering support; RQ5 transfer matrix (100 pairs) deferred; RQ6 long-horizon survival (150 deep tasks) deferred; RQ7 IAM delegation deferred; cross-model replication deferred; second model tier deferred; external red-team bounties reduced to internal red-teaming; travel reduced to one domestic conference or remote attendance.
*   **Evidence it would still produce (pilot precision, not full-gate precision):** M3 paired corruption-reduction estimate with wider intervals; M6 reconstruction result on the frozen subset; M9 UER pilot bound on arm C (0/1,000 → 95% upper ≈0.003 — a single-arm statistic that stands without controls, but no ≤0.001 claim); M12 retention vs. the minimal naive-memory control at reduced precision. No relative-effectiveness verdict beyond what these reduced samples support; full multi-arm replication, order-robustness, and the confirmatory phase require follow-on capital.
*   **Staffing risk:** Solo-founder execution of ~1,450–1,750 evaluation units plus annotation management (RQ2 double-blinded review with 2 annotators + adjudicator) within 12 months is high-risk; the fallback assumes contracted annotation support within the $150,000 envelope or a further-reduced RQ2 sample with to-be-preregistered power recalculation.

---

## 3. [HISTORICAL — V3] Capital Exposure & Drawdown Schedule

*Preserved V3 context. The 24-month drawdown below does not describe V4 capital-at-risk; see §9 for the structural update.*

Table 8.2 projects illustrative cumulative spend against the binding falsification gates (linearized at ~$50,000/quarter for planning; actual burn varies by benchmark phase).

### Table 8.2: [HISTORICAL — V3] Cumulative Capital-at-Risk by Milestone Gate (24-Month Program)

| Milestone Gate | Target Month | Cumulative Capital Drawn | Remaining (Unspent) | Cumulative % |
| :--- | :--- | :--- | :--- | :--- |
| **Gate M3** | Month 3 | $50,000 | $350,000 | 12.5% |
| **Gate M6** | Month 6 | $100,000 | $300,000 | 25.0% |
| **Gate M9 (Wedge)** | Month 9 | $150,000 | $250,000 | 37.5% |
| **Gate M12** | Month 12 | $200,000 | $200,000 | 50.0% |
| **Gate M15** | Month 15 | $250,000 | $150,000 | 62.5% |
| **Gate M18 (Scientific Gate)** | Month 18 | $300,000 | $100,000 | 75.0% |
| **Gate M21** | Month 21 | $350,000 | $50,000 | 87.5% |
| **Gate M24 (V3 Final Verdict — historical)** | Month 24 | $400,000 | $0 | 100.0% |

"Remaining" means *projected unspent funds*, not a committed return. By M18, ~75% of the ask was projected spent; the investor value at a STOP is the research evidence and artifacts, not capital recovery.

---

## 4. Conditional Capital Disposition (Founder-Proposed)

In the event of a metric failure at a binding gate, the founder proposes the disposition paths in Table 8.3. All rows defer to the canonical decision rules in `06_CORE_RESEARCH_PROGRAM.md` Table 6.2; summaries here never override that table. V4 rows (M21–M36) reference strand-level dispositions that spend no invented capital — they describe scope consequences, not dollar amounts.

### Table 8.3: Capital Disposition Matrix (V4-extended; dollar figures apply to V3 historical tranches only)

| Falsification Gate | Metric Failure | Founder-Proposed Disposition |
| :--- | :--- | :--- |
| **Gate M3** | Reduction in [50%,80%), or overhead miss | INCONCLUSIVE → Narrow: root-cause first (profile IPC/validation/sandbox). PIVOT to API gateway only if analysis shows an architectural limit — documented as a narrower threat model, not an equivalent substitute. |
| **Gate M3** | Reduction <50% (interval excluding 80%) | Pivot strand (re-scope taxonomy) or Stop; preserve unspent capital. |
| **Gate M6** | $\text{CRR}$ in [70%,80%) | INCONCLUSIVE → NARROW: optimize DAG tracing for one cycle. |
| **Gate M6** | $\text{CRR} < 70\%$ | STOP strand; preserve unspent capital subject to investor governance. |
| **Gate M9** | Observed $\text{UER} = 0.001$ (single failure in pilot) | NARROW/PIVOT: root-cause, expand attack suite, no "$\le 0.001$" claim. |
| **Gate M9** | $\text{UER} > 0.001$ on red-team suite, or $\text{FDR} > 2.0\%$ | STOP: fundamental security boundary breached. Unspent funds subject to investor governance. |
| **Gate M12** | False-Promotion Rate $> 0.02$ | NARROW scope to manually authored skills; STOP only if no mitigation path after one Narrow cycle. |
| **Gate M15** | $\text{ATR} < 0.50$ without safe bounding, or global regression $> 2\%$ | NARROW to single-model vertical; STOP only on uncontained regression. |
| **Gate M18** | $\text{MDID}_{0.90}$ ratio point $< 1.5\times$ (C vs B), or CI upper bound $< 2.0\times$ with adequate power, or no significant CIF reduction with adequate power, or completion inferior $>5\text{pp}$, or static pipeline wins joint criterion | STOP on broad thesis. Unspent funds subject to investor governance. |
| **Gate M21** | Migration-matrix preservation fails | NARROW to single-runtime deployment; defer live-provider validation. No new spend authorized beyond the rebased plan (see §9). |
| **Gate M24** | Objective-integrity pilot fails | NARROW adaptive optimization to pre-approved contracts; refuse Arc III activation. |
| **Gate M24** | Commercial checkpoint (non-binding; begins post-M18; NO verdict power) | Partner-interest signal tracked descriptively; no Narrow/Pivot/Stop consequence. The binding commercial verdict is M36-B. |
| **Gates M27–M33** | Strand thresholds missed | KILL the strand; preserve single-agent program scope. No program-level capital consequence beyond the rebased plan. |
| **Gate M36-A** | Integrated scientific validation fails | PIVOT or STOP the research thesis per investor governance. |
| **Gate M36-B** | External deployments fail ROI / adoption | NARROW/PIVOT to specific verticals or wind down per investor governance. Independent of M36-A. |

---

## 5. [HISTORICAL — V3] Compute, Sandbox, and Infrastructure Assumptions (Planning Basis — No Vendor Quotes Claimed)

*Preserved V3 context. Workload arithmetic below covers RQ1–RQ7 of the 24-month program. Year-2 migration/objective-integrity workloads (RQ7-expanded, RQ8) and all Year-3 workloads (RQ9–RQ12) are NOT costed here — costing them requires the §9 rebasing.*

No vendor pricing is quoted as fact. Figures below are *planning assumptions as of September 2026*, sensitive to model API price changes, and buffered by the $52,000 (13.0%) reserve.

*   **Benchmark volume — Table 8.0 (planning assumptions; mixed units kept distinct, TBD frozen at pre-registration).** The old line "200 + 150 + 1,000 + 300 + 200 + 450 + 200 ≈ 2,100" was arithmetically wrong on its face (the components sum to 2,500, and they mix tasks, traces, pairs, and sessions across different arm counts). It is replaced by:

### Table 8.0: [HISTORICAL — V3] Workload Decomposition (evaluation units × arms × seeds × tiers → model-invoked trajectories)

| RQ | Evaluation units (planning target) | Arms | Seeds / orders | Model tiers | Model-invoked trajectories (planning assumption) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| RQ1 | 200 tasks (SWE-bench Lite multi-file subset) | 2 (unified-dict control + typed) | 1 (+1 replication if INCONCLUSIVE) | 1 (frozen Tier 1) | 400 |
| RQ2 | 150 traces (AgentErrorBench frozen subset) | 2 presentation conditions (native spans + spine) | 1 (2 annotators + adjudicator) | 1 | 300 — model invocations cover only the automated-reconstruction condition and blinding paraphrase checks (planning assumption); the traces themselves pre-exist and human annotation is labor, not compute |
| RQ3 pilot | 1,000 attacks arm C (gibbrn) + 2×300 characterization subsets arms A/B (planning assumption, TBD) | 3 | 1 | 1 (frozen; Tier 3 replication deferred to confirmatory) | 1,600 |
| RQ3 confirmatory | 3,000 attacks on arm C + ≈300 A/B subset reruns, all on the frozen Tier 1 (from reserve; Tier-3 replication is a separate deferred decision, not inside this count) | 3 | 1 | 1 | ≈3,300 |
| RQ4 | 300 tasks total across 3 Latin-square orders (100/order, planning assumption) | 2 (naive memory + gibbrn) | 3 orders (built into the 300) | 1 | 600 |
| RQ5 | 100 transfer pairs × 2 conditions (source + transfer) | 2 (baseline + adapted) | 1 (+ enlargement if INCONCLUSIVE) | 1 per condition (source condition runs on the source model, transfer on the transfer model — tiers designate, not multiply; full-cross execution of every combo on both models would be 800 and is deferred unless an INCONCLUSIVE cycle requires it) | 400 |
| RQ6 | 150 deep tasks | 3 (A unmanaged + B conventional + C gibbrn) | 1 primary (+1 replication tier if M18 inconclusive) | 1 | 450 |
| RQ7 | 200 mock sessions (bound) + 100 unbound characterization (planning assumption, TBD) | 2 | 1 | 1 | 300 |
| FDR benign suite | 500 benign tasks (planning assumption, TBD) | 1 (arm C; spot-checks on B) | 1 | 1 | 500 |
| **Subtotal** | 3,300 mixed-unit primary evaluations (units, not trajectories) | — | — | — | **≈4,600 primary + ≈3,300 confirmatory ≈ 8,000–9,000** incl. retries, failed runs, regression re-executions |

Totals are ranges, not commitments: undecided multipliers (A/B subset sizes, second-tier replication, INCONCLUSIVE-cycle enlargements) are marked TBD and disclosed at pre-registration. The V2 "13,200" figure is retired.
*   **Compute $62,000 basis [V3 HISTORICAL]:** blended planning assumption across Tier 1 API models (majority of deep-task spend) and Tier 3 open-weights inference (self-hosted or API). Illustrative arithmetic (not a quote): if mean trajectory consumes ~0.8M blended tokens at an assumed ~$4.50/1M, 8,000 trajectories ≈ $28,800 in raw tokens; the remainder covers retries, failed runs, regression-suite re-executions (Engine 3 candidates × 20-task suites), replication across model tiers, and price-volatility headroom. Actual token totals will be reported per gate.
*   **Infrastructure $36,000 basis ($1,500/mo avg) [V3 HISTORICAL]:** managed PostgreSQL, object storage for WAL/checkpoints, observability/logging, CI runners for micro-sandbox regression, and gVisor-capable compute for warm-pool sandboxes. Assumes cloud credits are *not* relied upon; any credits received extend the reserve.
*   **Security $18,000 basis [V3 HISTORICAL]:** internal red-team labor, bounty pool for external adversarial probes at M9/M21, and one independent evaluation review of the Effect Gate boundary (scope-limited; not an "independent audit" or "third-party validation" of the thesis).
*   **Annotators/reviewers (RQ2):** covered within Human Capital + Security lines: 2 independent annotators plus senior adjudicator for ~150 traces, target $\kappa \ge 0.75$. If annotator rates exceed the planning envelope, the to-be-preregistered fallback is a reduced, re-powered RQ2 sample disclosed at M6 — not an unbudgeted scope increase.
*   **What is not silently increased:** the M9 confirmatory $N \approx 3{,}000$ phase is funded *from* the $52,000 reserve with corresponding scope deferral disclosed at the M9 review (deferral options, in order: RQ5 pair-count expansion, RQ4 single-seed replication instead of three orders, second-tier replication). Total ask remains $400,000. If the reserve proves insufficient (e.g. sustained API price rises beyond the 13% buffer), the same deferral list applies before any follow-on request — the program narrows rather than overspends.

---

## 6. Disbursement, Governance, and What Is Not Promised

*   Gates are *scientific review points*, not automatic disbursement tranches. Any tranched disbursement, milestone-gated release, escrow, or unspent-funds return requires a separate written agreement with the investor.
*   "Preserve remaining capital" means the founder will halt in-scope spend and present unspent funds for investor direction — not a guaranteed refund amount or mechanism.
*   No revenue, customer, partnership, or follow-on financing outcome is promised. The M36-A / M36-B "PROCEED" rows are *defensibility conditions* (what evidence would justify asking for a further round), not commitments that a round will be available.

---

## 7. Problem Discovery and External Contact (Early, Without Fabricated Partners)

No design partners, customers, or Letters of Intent are claimed. Problem discovery is front-loaded so technical choices track real deployment constraints:

*   **M01–M03 (within existing budget):** 10–15 discovery conversations total with platform/infra engineers, DevOps practitioners, and agent-framework maintainers about authorization, sandboxing, and memory-poisoning pain points — first tranche of 5–8 by day 60 (see §8), remainder by day 90. No partner commitment solicited; notes archived as evidence-checkpoint inputs.
*   **M04–M12:** consultative reviews of the Effect Gate API shape (integration effort: time-to-first-gated-tool, lines of integration code) with volunteer reviewers; no deployment or endorsement implied.
*   **Post-M18 only:** design-partner recruitment for M24 external validation begins *only if* the scientific gate passes. Live IAM provider validation (test tenants) occurs at M24, not earlier.

---

## 8. First 30–90 Day Experiment Plan (Within Existing Scope; Proposed — Not Completed)

*   **Days 1–30:** Freeze model tier versions and seeds; build minimal out-of-process interceptor for a defined set of synchronous file-write and shell-tool operations; publish the supported-ops list with the enforcement boundary and known bypass paths (selected-call interception — not all-syscall control); measure synchronous overhead distribution (binding target: median ≤30ms at M3; engineering stretch goal ≤14ms pre-execution; report p95 alongside the median); draft `gibbrn-auth-bench` manifest (attack families, verdict rules) and draft RQ1/RQ3 pilot protocols for OSF pre-registration before data collection.
*   **Days 31–60:** Execute RQ1 planning-target sample (200 SWE-bench Lite multi-file tasks, paired design, completion reported) with multi-arm harness where feasible; run first 200-attack RQ3 pilot slice; conduct the first tranche of 5–8 discovery interviews; publish internal checkpoint memo (methods + raw counts, no thesis claims).
*   **Days 61–90:** Remaining interviews (to 10–15 total). Complete to Gate M3 evidence package: McNemar result for corruption reduction, overhead histogram (median + p95), RQ3 pilot UER/FDR/latency with Clopper-Pearson/Wilson bounds, supported-ops/bypass documentation, integration-effort log, and Narrow/Pivot/Proceed recommendation per Table 6.2. *This plan proposes work to be done; no results are claimed.*

---

## 9. [V4] 36-Month Rebasing — Explicitly Unresolved (No New Ask)

**Decision:** the V4 36-month program (12 RQs, 12 gates, ~24 checkpoints, Years 1–3 per `07_36_MONTH_ROADMAP.md`) has **no authorized capital ask as of this dossier version.** The following are recorded without inventing salaries, compute costs, contingency reserves, or fundraising numbers:

1.  **Every capital assumption tied to 24 months is identified:** Table 8.1 categories and 24-month allocations; Table 8.2 drawdown through M24; Table 8.0 workloads for RQ1–RQ7; §5 compute/infra/security bases; the §2 fallback envelope. All are marked [HISTORICAL — V3] above and remain valid only as history and calibration context.
2.  **No linear extrapolation is authorized:** $400,000 / 24 months is NOT scaled to $600,000 / 36 months or any other figure. Year-3 workloads (multi-agent sandboxes, governance experiments, integrated deployments) have no cost basis in this dossier, and Year-2 migration/objective-integrity expansions (RQ7-expanded, RQ8) are scoped but not costed.
3.  **Structural sequencing changes made without inventing numbers:**
    - Capital-at-risk logic extends gate-by-gate through M36: each gate's Narrow/Pivot/Stop/Kill disposition (§4) is defined as a *scope* consequence; dollar exposure per gate awaits the rebased model.
    - The M24 Arc III readiness review (§4 of `07_36_MONTH_ROADMAP.md`) doubles as a capital-gating review: Year-3 scope activates only with justified evidence AND authorized funding.
    - The narrow-before-overspend rule (§5, V3) carries forward as policy: pilot overruns narrow scope before any follow-on request.
4.  **Founder authorization required (see AD-034):** a rebased 36-month capital model — bottom-up staffing, compute (including RQ8–RQ12 workloads), infrastructure, security/red-team, operations, and reserve — with a stated base ask and any fallback envelope. Until that authorization lands, every investor-facing file states the ask as unresolved rather than quoting a number.
5.  **If internal consistency requires a current public number** (e.g., an overview table that cannot show a blank), the file cites the V3 historical ask with an explicit [HISTORICAL — V3; V4 REBASING PENDING] flag — never a silent substitution. See `11_INVESTOR_OVERVIEW.md` §8 and `10_1517_TECHNICAL_BRIEF.md` §10 for the flagged presentation.
