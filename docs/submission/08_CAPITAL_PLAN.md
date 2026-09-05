# 08: Expense Modeling & Capital-at-Risk

**Document Track:** Financial Modeling & Capital Allocation (Version 3.0)  
**Date:** September 2026 | **Verification Pass:** V3 Delta Pending Verification  
**Audience:** Deep-Tech Investors, 1517 Fund Partners, Technical Founders  
**Primary Capital Ask:** **USD 400,000 for 24 Months** (Checkpoint-Gated Empirical R&D Plan)

> **Governance note:** Milestone reviews, gates, and "preserve remaining capital" language in this document are *founder-proposed* review mechanics. They are not investor-agreed disbursement tranches, escrow terms, or return guarantees. Any gated disbursement, escrow, or return mechanics require a separate written investor agreement. No capital preservation or return is promised beyond "unspent funds remain subject to investor governance."

## 1. The $400,000 / 24-Month Operating Budget

The $400,000 capital request is allocated to execute the 24-month research roadmap (RQ1–RQ7), culminating in Gate M24. It is capital mapped against a falsifiable research program, not an arbitrary runway.

### Table 8.1: Primary Resource Allocation (24 Months)

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
| **TOTAL** | **Target Initial Capitalization** | **$400,000** |

*Note on Compensation:* Amounts are *proposed compensation* assumptions for a founder-led program with optional part-time research engineering support contingent on funding. No claim is made about cost of living or "subsistence" levels, which depend on location and personal circumstances not established in this dossier.

---

## 2. The $150,000 Constrained Fallback Plan (Preliminary — Not Fully Costed)

If 1517 prefers to fund only the initial evidence gates (M3–M12) to de-risk the core Deterministic Effect Gate, a solo-founder 12-month pilot is sketched at **$150,000**. *This fallback is preliminary and has not been bottom-up costed to the same standard as Table 8.1; treat it as a scoping proposal, not a committed budget.*

*   **Kept:** Founder compensation (12 mo), RQ1–RQ4 workloads at planning-target unit counts (200 + 150 + 1,000 pilot + 300 = 1,650 evaluation units; single-arm pilot scope with multi-arm replication deferred to follow-on), minimal sandbox/DB infrastructure, single-model-tier replication only, problem-discovery interviews (§7).
*   **Cut:** Contractor/engineering support; RQ5 transfer matrix (100 pairs) deferred; RQ6 long-horizon survival (150 deep tasks) deferred; RQ7 IAM delegation deferred; cross-model replication deferred; second model tier deferred; external red-team bounties reduced to internal red-teaming; travel reduced to one domestic conference or remote attendance.
*   **Evidence it would still produce:** M3 interception/state-classification result; M6 causal-reconstruction result; M9 UER pilot (0/1,000 with 95% upper ≈0.003 — not a ≤0.001 claim); M12 poisoning/retention result. A confirmatory $N \approx 3{,}000$ phase, cross-model replication, and live-IAM validation would remain unfunded and require follow-on capital.
*   **Staffing risk:** Solo-founder execution of ~1,650 evaluation units (single-arm pilot scope) plus annotation management (RQ2 double-blinded review with 2 annotators + adjudicator) within 12 months is high-risk; the fallback assumes contracted annotation support within the $150,000 envelope or a reduced RQ2 sample with to-be-preregistered power recalculation.

---

## 3. Capital Exposure & Drawdown Schedule

Table 8.2 projects illustrative cumulative spend against the binding falsification gates (linearized at ~$50,000/quarter for planning; actual burn varies by benchmark phase).

### Table 8.2: Cumulative Capital-at-Risk by Milestone Gate

| Milestone Gate | Target Month | Cumulative Capital Drawn | Remaining (Unspent) | Cumulative % |
| :--- | :--- | :--- | :--- | :--- |
| **Gate M3** | Month 3 | $50,000 | $350,000 | 12.5% |
| **Gate M6** | Month 6 | $100,000 | $300,000 | 25.0% |
| **Gate M9 (Wedge)** | Month 9 | $150,000 | $250,000 | 37.5% |
| **Gate M12** | Month 12 | $200,000 | $200,000 | 50.0% |
| **Gate M15** | Month 15 | $250,000 | $150,000 | 62.5% |
| **Gate M18 (Scientific Gate)** | Month 18 | $300,000 | $100,000 | 75.0% |
| **Gate M21** | Month 21 | $350,000 | $50,000 | 87.5% |
| **Gate M24 (Final Verdict)** | Month 24 | $400,000 | $0 | 100.0% |

"Remaining" means *projected unspent funds*, not a committed return. By M18, ~75% of the ask is projected spent; the investor value at a STOP is the research evidence and artifacts, not capital recovery.

---

## 4. Conditional Capital Disposition (Founder-Proposed)

In the event of a metric failure at a binding gate, the founder proposes the disposition paths in Table 8.3. All rows defer to the canonical decision rules in `06_CORE_RESEARCH_PROGRAM.md` Table 6.2; summaries here never override that table.

### Table 8.3: Capital Disposition Matrix

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
| **Gate M18** | $\text{MDDD}_{0.90}$ ratio $< 2.0\times$ (or CI lower $\le 1.5\times$), or static pipeline wins joint criterion | STOP on broad thesis. Unspent funds subject to investor governance. |
| **Gate M21** | Mock-IAM binding fails | NARROW to standalone capabilities; defer live-provider validation. |
| **Gate M24** | External deployments fail ROI | NARROW/PIVOT to specific verticals or wind down per investor governance. |

---

## 5. Compute, Sandbox, and Infrastructure Assumptions (Planning Basis — No Vendor Quotes Claimed)

No vendor pricing is quoted as fact. Figures below are *planning assumptions as of September 2026*, sensitive to model API price changes, and buffered by the $52,000 (13.0%) reserve.

*   **Benchmark volume — Table 8.0 (planning assumptions; mixed units kept distinct, TBD frozen at pre-registration).** The old line "200 + 150 + 1,000 + 300 + 200 + 450 + 200 ≈ 2,100" was arithmetically wrong on its face (the components sum to 2,500, and they mix tasks, traces, pairs, and sessions across different arm counts). It is replaced by:

### Table 8.0: Workload Decomposition (evaluation units × arms × seeds × tiers → model-invoked trajectories)

| RQ | Evaluation units (planning target) | Arms | Seeds / orders | Model tiers | Model-invoked trajectories (planning assumption) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| RQ1 | 200 tasks (SWE-bench Lite multi-file subset) | 2 (unified-dict control + typed) | 1 (+1 replication if INCONCLUSIVE) | 1 (frozen Tier 1) | 400 |
| RQ2 | 150 traces (AgentErrorBench frozen subset) | 2 conditions (native spans + spine) | 1 (2 annotators + adjudicator; annotation is human labor, not compute) | 1 | 300 |
| RQ3 pilot | 1,000 attacks arm C (gibbrn) + 2×300 characterization subsets arms A/B (planning assumption, TBD) | 3 | 1 | 1 (frozen; Tier 3 replication deferred to confirmatory) | 1,600 |
| RQ3 confirmatory | 3,000 attacks arm C + A/B subsets TBD (from reserve; see below) | 3 | 1 | 2 | ≈3,300+ |
| RQ4 | 300 tasks total across 3 Latin-square orders (100/order, planning assumption) | 2 (naive memory + gibbrn) | 3 orders (built into the 300) | 1 | 600 |
| RQ5 | 100 transfer pairs × 2 conditions (source + transfer) | 2 (baseline + adapted) | 1 (+ enlargement if INCONCLUSIVE) | 2 (source + transfer families) | 800 |
| RQ6 | 150 deep tasks | 3 (A unmanaged + B conventional + C gibbrn) | 1 | 1 primary (+1 replication tier if M18 inconclusive) | 450 |
| RQ7 | 200 mock sessions (bound) + 100 unbound characterization (planning assumption, TBD) | 2 | 1 | 1 | 300 |
| FDR benign suite | 500 benign tasks (planning assumption, TBD) | 1 (arm C; spot-checks on B) | 1 | 1 | 500 |
| **Subtotal** | 3,300 mixed-unit primary evaluations (units, not trajectories) | — | — | — | **≈5,000 primary + ≈3,300 confirmatory ≈ 8,000–9,500** incl. retries, failed runs, regression re-executions |

Totals are ranges, not commitments: undecided multipliers (A/B subset sizes, second-tier replication, INCONCLUSIVE-cycle enlargements) are marked TBD and disclosed at pre-registration. The V2 "13,200" figure is retired.
*   **Compute $62,000 basis:** blended planning assumption across Tier 1 API models (majority of deep-task spend) and Tier 3 open-weights inference (self-hosted or API). Illustrative arithmetic (not a quote): if mean trajectory consumes ~0.8M blended tokens at an assumed ~$4.50/1M, 8,000 trajectories ≈ $28,800 in raw tokens; the remainder covers retries, failed runs, regression-suite re-executions (Engine 3 candidates × 20-task suites), replication across model tiers, and price-volatility headroom. Actual token totals will be reported per gate.
*   **Infrastructure $36,000 basis ($1,500/mo avg):** managed PostgreSQL, object storage for WAL/checkpoints, observability/logging, CI runners for micro-sandbox regression, and gVisor-capable compute for warm-pool sandboxes. Assumes cloud credits are *not* relied upon; any credits received extend the reserve.
*   **Security $18,000 basis:** internal red-team labor, bounty pool for external adversarial probes at M9/M21, and one independent evaluation review of the Effect Gate boundary (scope-limited; not an "independent audit" or "third-party validation" of the thesis).
*   **Annotators/reviewers (RQ2):** covered within Human Capital + Security lines: 2 independent annotators plus senior adjudicator for ~150 traces, target $\kappa \ge 0.75$. If annotator rates exceed the planning envelope, the to-be-preregistered fallback is a reduced, re-powered RQ2 sample disclosed at M6 — not an unbudgeted scope increase.
*   **What is not silently increased:** the M9 confirmatory $N \approx 3{,}000$ phase is funded *from* the $52,000 reserve with corresponding scope deferral disclosed at the M9 review (deferral options, in order: RQ5 pair-count expansion, RQ4 single-seed replication instead of three orders, second-tier replication). Total ask remains $400,000. If the reserve proves insufficient (e.g. sustained API price rises beyond the 13% buffer), the same deferral list applies before any follow-on request — the program narrows rather than overspends.

---

## 6. Disbursement, Governance, and What Is Not Promised

*   Gates are *scientific review points*, not automatic disbursement tranches. Any tranched disbursement, milestone-gated release, escrow, or unspent-funds return requires a separate written agreement with the investor.
*   "Preserve remaining capital" means the founder will halt in-scope spend and present unspent funds for investor direction — not a guaranteed refund amount or mechanism.
*   No revenue, customer, partnership, or follow-on financing outcome is promised. The M24 "PROCEED to Seed" row is a *defensibility condition* (what evidence would justify asking for a Seed round), not a commitment that a Seed round will be available.

---

## 7. Problem Discovery and External Contact (Early, Without Fabricated Partners)

No design partners, customers, orLetters of Intent are claimed. Problem discovery is front-loaded so technical choices track real deployment constraints:

*   **M01–M03 (within existing budget):** 10–15 discovery conversations total with platform/infra engineers, DevOps practitioners, and agent-framework maintainers about authorization, sandboxing, and memory-poisoning pain points — first tranche of 5–8 by day 60 (see §8), remainder by day 90. No partner commitment solicited; notes archived as evidence-checkpoint inputs.
*   **M04–M12:** consultative reviews of the Effect Gate API shape (integration effort: time-to-first-gated-tool, lines of integration code) with volunteer reviewers; no deployment or endorsement implied.
*   **Post-M18 only:** design-partner recruitment for M24 external validation begins *only if* the scientific gate passes. Live IAM provider validation (test tenants) occurs at M24, not earlier.

---

## 8. First 30–90 Day Experiment Plan (Within Existing Scope; Proposed — Not Completed)

*   **Days 1–30:** Freeze model tier versions and seeds; build minimal out-of-process interceptor for a defined set of synchronous file-write and shell-tool operations; publish the supported-ops list with the enforcement boundary and known bypass paths (selected-call interception — not all-syscall control); measure synchronous overhead distribution (binding target: median ≤30ms at M3; engineering stretch goal ≤14ms pre-execution; report p95 alongside the median); draft `gibbrn-auth-bench` manifest (attack families, verdict rules) and draft RQ1/RQ3 pilot protocols for OSF pre-registration before data collection.
*   **Days 31–60:** Execute RQ1 planning-target sample (200 SWE-bench Lite multi-file tasks, paired design, completion reported) with multi-arm harness where feasible; run first 200-attack RQ3 pilot slice; conduct the first tranche of 5–8 discovery interviews; publish internal checkpoint memo (methods + raw counts, no thesis claims).
*   **Days 61–90:** Remaining interviews (to 10–15 total). Complete to Gate M3 evidence package: McNemar result for corruption reduction, overhead histogram (median + p95), RQ3 pilot UER/FDR/latency with Clopper-Pearson/Wilson bounds, supported-ops/bypass documentation, integration-effort log, and Narrow/Pivot/Proceed recommendation per Table 6.2. *This plan proposes work to be done; no results are claimed.*
