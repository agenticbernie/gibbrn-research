# 08: Expense Modeling & Capital-at-Risk

**Document Track:** Financial Modeling & Capital Allocation (Version 4.2 — Capital Rebase)  
**Date:** September 2026 | **Dossier Version:** 4.2.2 (36-Month Systems Research & Prototype Program)  
**Audience:** Deep-Tech Investors, 1517 Fund Partners, Technical Founders  

> **V4.2 CAPITAL STATUS — CANONICAL:** The V4 capital model is **rebased and founder-authorized** (see §15). All "capital unresolved / rebasing pending" language from V4–V4.1 is superseded in canonical sections and retained only in changelog/ledger history.
>
> **Current Financing Target:** USD 450,000 to fund GIBBRN through Month 24 and the Objective & Evaluation Integrity / Arc-III-readiness major gate.
>
> **Modeled 36-Month Program Capitalization:** approximately USD 700,000.
>
> **Conditional Year-3 Capital Requirement:** approximately USD 250,000 for Months 25–36, activated only if the Month-24 evidence supports proceeding with Arc III.
>
> GIBBRN is NOT raising $700,000 now. The $450,000 current financing and the ~$250,000 conditional extension must never be collapsed into a single "ask."

> **Governance note:** Milestone gates are *founder-proposed scientific review mechanisms*, not investor-agreed disbursement tranches, escrow terms, or return guarantees. Any gated disbursement, escrow, milestone-based wire schedule, clawback, or return mechanics require a separate written investor agreement. Scientific STOP/NARROW/PIVOT decisions govern research scope — not legally binding investor distributions unless separately contracted. This dossier invents no escrow terms, SAFE terms, valuation caps, or ownership percentages. No capital preservation or return is promised beyond "unspent funds remain subject to investor governance."

---

## 1. V4 Current Financing Target — USD 450,000 (M0–M24)

USD 450,000 is the amount GIBBRN is currently seeking. It funds Year 1 (Act Safely) and Year 2 (Change Safely): Gates M3–M24, the RQ3 security/consequence-integrity campaign (pilot + confirmatory), procedural adaptation experiments, cross-model/runtime continuity, long-horizon reliability experiments, Objective & Evaluation Integrity, and design-partner preparation plus early validation where scheduled.

The ask is not "24 months of burn." It finances the project to a scientifically meaningful decision boundary: the M24 major gate, where the program either earns Arc III or stops expanding. What each gate's evidence buys the investor is mapped in `10_1517_TECHNICAL_BRIEF.md` §8–§9; the binding decision rules live in `06_CORE_RESEARCH_PROGRAM.md` Table 6.2.

---

## 2. Modeled 36-Month Program Capitalization — Approximately USD 700,000

The table below is the founder-authorized bottom-up planning model for the complete 36-month program if all three Research Arcs proceed. Figures are planning allocations, not vendor quotes. The total reconciles exactly.

### Table 8.1 (V4 Canonical): 36-Month Bottom-Up Category Allocation

| Category | 36-Month Planning Allocation |
| :--- | ---: |
| Founder / Principal Researcher compensation ($5,000/mo × 36 mo) | $180,000 |
| Research engineering / contractor support (ramped to workload) | $120,000 |
| Statistics / annotation / research assistance | $35,000 |
| Model API / benchmark compute (frozen APIs + open-weight inference; no foundation-model training) | $80,000 |
| Sandbox / DB / storage / CI / observability infrastructure | $54,000 |
| External security / red-team / independent evaluation | $60,000 |
| Hardware / technical tooling (broad categories; no shopping list) | $25,000 |
| Legal / IP / company operations | $20,000 |
| Research dissemination / travel | $15,000 |
| Design-partner deployments (up to a small number of post-gate deployments) | $20,000 |
| Contingency / API-volatility / replication reserve (13.0%) | $91,000 |
| **TOTAL** | **$700,000** |

Arithmetic: $180k + $120k + $35k + $80k + $54k + $60k + $25k + $20k + $15k + $20k + $91k = **$700,000 exactly**. Reserve ratio: $91,000 / $700,000 = **13.0%**.

---

## 3. Category Notes (What Each Line Covers — and Does Not Claim)

*   **Founder compensation ($180,000):** USD 5,000/month × 36 months. This retains the V3 planning assumption rather than opportunistically increasing founder pay for the larger program. It is a founder-approved planning assumption — not described as market-rate, subsistence, salary-benchmark, or cost-of-living-derived.
*   **Research engineering ($120,000):** contractor support ramped to experimental workload: benchmark-harness implementation, infrastructure integration, experiment automation, multi-agent sandbox engineering, migration-test implementation. No hire is claimed as existing; no full-time employment is implied.
*   **Statistics / annotation / assistance ($35,000):** blinded trajectory annotation, third-reviewer adjudication, statistical consultation (including the RQ6 competing-risk design), preregistration review, data cleaning, manifest verification, manual taxonomy/family-equivalence adjudication. Kept separate from engineering: the dossier does not imply the founder alone can run every evaluation.
*   **Model API / benchmark compute ($80,000):** frozen commercial APIs and open-weight inference for RQ1–RQ6 runs, the RQ3 pilot + confirmatory campaigns, replication, regression reruns, RQ5 transfer matrices, RQ6 competing-risk experiments, the RQ7 migration matrix, RQ8 evaluation, and conditional RQ9–RQ12 multi-agent work. Explicitly NOT foundation-model pretraining or a general fine-tuning program. Exact RQ8–RQ12 trajectory counts remain TBD at calibration; the $80k line is therefore a planning envelope protected by contingency and recalibrated at research gates — no token totals are fabricated beyond the frozen workload model.
*   **Infrastructure ($54,000):** PostgreSQL, object storage, WAL/checkpoint retention, observability, CI runners, gVisor/sandbox hosts, artifact storage, ephemeral and multi-agent sandbox workloads, backup/recovery, security logging. A planning envelope; no vendor pricing quoted.
*   **Security / red-team / independent evaluation ($60,000):** deliberately protected from cuts — external security review, attack-suite review, RQ3 external red-team exercises, consequence-integrity audit, endpoint/network-authority testing, third-party reproduction attempts, Year-3 governance-sandbox review, independent scientific evaluation where useful. Independent evaluation matters because security/reliability claims cannot credibly rest entirely on founder-generated testing. No auditor is claimed as contracted.
*   **Hardware / tooling ($25,000):** broad categories only — workstations, justified local-inference hardware, test machines, networking/security test equipment, backup equipment, software/research tooling. No device list invented.
*   **Legal / IP / operations ($20,000):** setup, contracts, IP review, research licensing, accounting, basic compliance. No patent filing promised; the dossier's anti-IP-hype discipline stands.
*   **Dissemination / travel ($15,000):** submissions, conferences, technical meetings, partner travel where necessary. No venue acceptance claimed.
*   **Design-partner deployments ($20,000):** later-stage validation after M18/M24 — deployment engineering, environment integration, logging/observability, partner sandbox setup, security validation, evaluation support. No partner claimed as existing.
*   **Contingency / replication reserve ($91,000; 13.0%):** NOT free capital. Covers API price changes, replication, larger-than-planned samples, RQ6 power recalibration, RQ3 confirmatory enlargement, incident investigation, unanticipated infrastructure needs, and Year-3 multi-agent variance. Governed by the narrow-before-overspend rule: overruns narrow scope before any follow-on request.

---

## 4. Stage Allocation — USD 450,000 (M0–M24) + Approximately USD 250,000 (M25–M36)

Stage 1 is fixed at **USD 450,000**; Stage 2 consumes the remaining **approximately USD 250,000**. The line-item timing below models when costs occur: founder pay follows time; engineering ramps upward; Year-3 multi-agent, governance, and design-partner spend concentrate in Stage 2; security/evaluation spans both (early RQ3 + later external validation); contingency is deliberately NOT exhausted before M24. External language keeps "approximately" where timing is uncertain; internal arithmetic is exact.

### Table 8.2 (V4 Canonical): Stage Split (exact internally)

| Category | 36-Mo Total | Stage 1 (M0–M24) | Stage 2 (M25–M36) |
| :--- | ---: | ---: | ---: |
| Founder / Principal Researcher | $180,000 | $120,000 | $60,000 |
| Research engineering / contractor | $120,000 | $70,000 | $50,000 |
| Statistics / annotation / assistance | $35,000 | $25,000 | $10,000 |
| Model API / benchmark compute | $80,000 | $55,000 | $25,000 |
| Infrastructure | $54,000 | $36,000 | $18,000 |
| Security / red-team / evaluation | $60,000 | $35,000 | $25,000 |
| Hardware / tooling | $25,000 | $18,000 | $7,000 |
| Legal / IP / operations | $20,000 | $14,000 | $6,000 |
| Dissemination / travel | $15,000 | $9,000 | $6,000 |
| Design-partner deployments | $20,000 | $8,000 | $12,000 |
| Contingency / replication reserve | $91,000 | $60,000 | $31,000 |
| **TOTAL** | **$700,000** | **$450,000** | **$250,000** |

Column verification: Stage 1 sums to $450,000 exactly; Stage 2 sums to $250,000 exactly; every row reconciles to its Table 8.1 total.

---

## 5. Capital-at-Risk Model (Activity-Based Planning Estimates)

Burn is NOT assumed uniform: benchmark, red-team, annotation, and deployment phases spend faster than analysis/writing phases. Cumulative exposure below is an illustrative stage-level planning path (not a wire schedule, not a derived quarterly burn curve), keyed to the major thesis gates where defensible. Exact quarterly timing will be frozen in the operating budget after financing; until then no calculation beneath these gate-level figures is claimed.

### Table 8.3 (V4 Canonical): Cumulative Capital Exposure (illustrative stage-level path)

| Milestone Gate | Target Month | Cumulative Spend (est.) | Of Which Stage |
| :--- | :--- | ---: | :--- |
| **Gate M3** | Month 3 | ~$55,000 | Stage 1 |
| **Gate M6** | Month 6 | ~$110,000 | Stage 1 |
| **Gate M9 (Wedge) ★** | Month 9 | ~$170,000 | Stage 1 |
| **Gate M12** | Month 12 | ~$230,000 | Stage 1 |
| **Gate M15** | Month 15 | ~$285,000 | Stage 1 |
| **Gate M18 (Scientific) ★** | Month 18 | ~$345,000 | Stage 1 |
| **Gate M21** | Month 21 | ~$400,000 | Stage 1 |
| **Gate M24 (Year-2 / Readiness) ★** | Month 24 | **$450,000** | Stage 1 complete |
| **Gate M27** | Month 27 | ~$515,000 | Stage 2 (conditional) |
| **Gate M30** | Month 30 | ~$580,000 | Stage 2 (conditional) |
| **Gate M33** | Month 33 | ~$640,000 | Stage 2 (conditional) |
| **Gate M36-A / M36-B ★** | Month 36 | **~$700,000** | Program complete |

"Remaining" at any STOP means projected unspent funds subject to investor governance — not a committed return. The investor value at a STOP is the research evidence and artifacts, not capital recovery.

---

## 6. Conditional Capital Disposition (Founder-Proposed)

In the event of a metric failure at a binding gate, the founder proposes the disposition paths below. All rows defer to the canonical decision rules in `06_CORE_RESEARCH_PROGRAM.md` Table 6.2; summaries here never override that table.

### Table 8.4: Capital Disposition Matrix

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
| **Gate M21** | Migration-matrix preservation fails | NARROW to single-runtime deployment; defer live-provider validation. No new spend authorized beyond the rebased plan. |
| **Gate M24** | Objective-integrity pilot fails | NARROW adaptive optimization to pre-approved contracts; refuse Arc III activation. |
| **Gate M24** | Commercial checkpoint (non-binding; begins post-M18; NO verdict power) | Partner-interest signal tracked descriptively; no Narrow/Pivot/Stop consequence. The binding commercial verdict is M36-B. |
| **Gates M27–M33** | Strand thresholds missed | KILL the strand; preserve single-agent program scope. No program-level capital consequence beyond the rebased plan. |
| **Gate M36-A** | Integrated scientific validation fails | PIVOT or STOP the research thesis per investor governance. |
| **Gate M36-B** | External deployments fail ROI / adoption | NARROW/PIVOT to specific verticals or wind down per investor governance. Independent of M36-A. |

---

## 7. M24 Capital Decision — Evidence Gate AND Financing Decision Point

M24 is simultaneously the Objective & Evaluation Integrity major gate, the Arc III readiness review, and the future-financing decision point. Passing M24 does NOT automatically spend $250,000. It means the evidence supports *seeking and authorizing* the conditional Year-3 capital. Actual Year-3 financing remains subject to evidence, an updated cost basis, the founder's decision, and investor financing availability. Refusing Arc III activation is a scope decision, not a program failure — the M0–M24 research program stands on its own evidence.

---

## 8. M36-A / M36-B Capital Reporting

The independent verdict structure is preserved in capital reporting. Expenditure reporting at M36 distinguishes science (experiments, evaluation, replication), engineering/prototype, design-partner deployment, and commercialization validation — so commercial failure cannot retroactively invalidate scientific success, and scientific overreach cannot hide a useful commercial wedge behind Year-3 hypotheses.

---

## 9. Staged-Financing Rationale

The founder does not currently request the full ~$700k because: (1) Year 3 is scientifically conditional on M24; (2) RQ9–RQ12 must not be fully capitalized before M24 evidence exists; (3) $450k supplies adequate runway through the critical Year-2 decision point; (4) premature Year-3 financing would fund speculative work; (5) optionality is preserved if the program narrows after M9/M18/M24. Conversely, the founder does NOT prefer a $250k + $200k split of Stage 1: a forced financing event inside Arc II would create fundraising risk during the critical RQ5–RQ8 research stretch. The split below exists strictly as an investor-structured fallback.

---

## 10. Optional Constrained Financing Fallback (Investor-Structured Alternative — NOT Founder-Preferred)

```text
Close A: $250k — initial research / Year-1-heavy execution (through ~M12 + RQ3 pilot)
Close B: $200k — continuation through M24 after evidence review (M12-gate-gated)
Conditional Year-3 extension: ~$250k — M24-evidence-gated
Total: $700k
```

Close B must be conditioned on an evidence review at the M12 boundary at minimum; the dossier does not recommend quarterly capital tranches. Founder-preferred remains **$450k current financing + ~$250k M24-conditional extension**.

---

## 11. Reserve Policy and What Is Not Promised

*   The $91,000 (13.0%) reserve funds the M9 confirmatory $N \approx 3{,}000$ phase, RQ6 power-driven enlargement, RQ3 suite expansion, and API-volatility headroom — with ordered deferral (RQ5 pair-count expansion; RQ4 single-seed replication; second-tier replication) disclosed at review before any follow-on request. The program narrows rather than overspends.
*   Gates are scientific review points, not automatic disbursement tranches.
*   "Preserve remaining capital" means halting in-scope spend and presenting unspent funds for investor direction — not a guaranteed refund.
*   No revenue, customer, partnership, or follow-on financing outcome is promised. M36-A/M36-B "PROCEED" rows are defensibility conditions, not commitments that capital will be available.

---

## 12. Capital Efficiency Narrative

The program intentionally reuses mature infrastructure and concentrates capital on empirical falsification rather than foundation-model training: no pretraining, no GPU-cluster buildout, no general fine-tuning program. Foundation models are treated as interchangeable frozen cognitive substrates (commercial APIs + open weights) inside controlled experiments. Durable open-source infrastructure (PostgreSQL, gVisor, standard CI) is reused rather than rebuilt. The expensive lines are testing, security/red-teaming, replication, annotation, and long-horizon experiments — exactly where falsification lives.

---

## 13. Cost Uncertainty — Fixed Assumptions vs. Estimates vs. Conditional Spend

*   **Fixed planning assumptions:** founder compensation rate ($5k/mo); authorized totals ($450k current, ~$700k program, ~$250k conditional extension).
*   **Workload-sensitive estimates:** API/compute envelope ($80k, recalibrated at gates); external evaluation ($60k, scoped per campaign); annotation/assistance ($35k); replication draw on contingency.
*   **Conditional spend:** most RQ9–RQ12 costs, Year-3 design-partner deployment ($12k of the $20k line), and $31k of contingency sit behind the M24 decision. Uncertainty is disclosed here rather than hidden inside false precision.

---

## 14. Problem Discovery and External Contact (Early, Without Fabricated Partners)

No design partners, customers, or Letters of Intent are claimed. Problem discovery is front-loaded so technical choices track real deployment constraints:

*   **M01–M03 (within existing budget):** 10–15 discovery conversations total with platform/infra engineers, DevOps practitioners, and agent-framework maintainers about authorization, sandboxing, and memory-poisoning pain points — first tranche of 5–8 by day 60 (see §16), remainder by day 90. No partner commitment solicited; notes archived as evidence-checkpoint inputs.
*   **M04–M12:** consultative reviews of the Effect Gate API shape (integration effort: time-to-first-gated-tool, lines of integration code) with volunteer reviewers; no deployment or endorsement implied.
*   **Post-M18 only:** design-partner recruitment for M24 external validation begins *only if* the scientific gate passes. Live IAM provider validation (test tenants) occurs at M24, not earlier.

---

## 15. V4.2 Rebase Authorization Record (Supersedes the V4–V4.1 "Unresolved" Status)

The V4–V4.1 dossier deliberately carried no 36-month ask (AD-034): research scope, the V4.2 competing-risk methodology closure, and workload calibration were not yet mature enough to cost honestly. That integrity constraint is now discharged by founder authorization: the scientific design reached sufficient maturity (12 RQs frozen; CIF-based methodology closed; RQ8–RQ12 bounded as calibration-contingent envelopes), and the founder authorizes the §2–§4 model — **$450k current financing; ~$700k total program capitalization; ~$250k M24-conditional Year-3 extension** — as planning allocations, not cost guarantees. No scientific gate becomes a legal financing tranche (governance note, top of file). The budget remains a planning model subject to §13 uncertainty and §11 reserve discipline.

---

## 16. First 30–90 Day Experiment Plan (Within Existing Scope; Proposed — Not Completed)

*   **Days 1–30:** Freeze model tier versions and seeds; build minimal out-of-process interceptor for a defined set of synchronous file-write and shell-tool operations; publish the supported-ops list with the enforcement boundary and known bypass paths (selected-call interception — not all-syscall control); measure synchronous overhead distribution (binding target: median ≤30ms at M3; engineering stretch goal ≤14ms pre-execution; report p95 alongside the median); draft `gibbrn-auth-bench` manifest (attack families, per-family quotas, fault-injection axis, verdict rules) and draft RQ1/RQ3 pilot protocols for OSF pre-registration before data collection.
*   **Days 31–60:** Execute RQ1 planning-target sample (200 SWE-bench Lite multi-file tasks, paired design, completion reported) with multi-arm harness where feasible; run first 200-attack RQ3 pilot slice; conduct the first tranche of 5–8 discovery interviews; publish internal checkpoint memo (methods + raw counts, no thesis claims).
*   **Days 61–90:** Remaining interviews (to 10–15 total). Complete to Gate M3 evidence package: McNemar result for corruption reduction, overhead histogram (median + p95), RQ3 pilot UER/FDR/latency with Clopper-Pearson/Wilson bounds, supported-ops/bypass documentation, integration-effort log, and Narrow/Pivot/Proceed recommendation per Table 6.2. *This plan proposes work to be done; no results are claimed.*

---

## APPENDIX H1. [HISTORICAL — V3] The $400,000 / 24-Month Operating Budget (Superseded)

*Preserved V3 context (September 2026 review). This budget mapped to the superseded 24-month program (RQ1–RQ7, Gates M3–M24) and is NOT the V4 financing structure. Retained for provenance only.*

| Category | Item Description | 24-Month Allocation |
| :--- | :--- | ---: |
| **Human Capital** | Founder / Principal Researcher — proposed compensation ($5,000/mo × 24 mo) | $120,000 |
| **Human Capital** | Planned Hire / Contractor, part-time research engineering (contingent on funding; ~$3,000/mo equivalent) | $72,000 |
| **Compute** | Model Inference + Benchmark Compute | $62,000 |
| **Infrastructure** | Sandbox / DB / Observability (AWS/GCP) | $36,000 |
| **Operations** | Hardware / Tooling — unconfirmed allocation (no itemized list; no quotes claimed) | $24,000 |
| **Security** | Security / Red-Team / External Evaluation | $18,000 |
| **Operations** | Legal / Incorporation / IP | $9,000 |
| **Operations** | Research Dissemination / Travel | $7,000 |
| **Contingency** | Strategic Reserve / API Volatility Buffer (13.0%) | $52,000 |
| **TOTAL [V3 HISTORICAL]** | **$400,000** |

*Compensation amounts were proposed planning assumptions, not cost-of-living claims.*

## APPENDIX H2. [HISTORICAL — V3] The $150,000 Constrained Fallback (Superseded; Preliminary — Never Fully Costed)

*Preserved V3 context. A solo-founder 12-month pilot sketch for gates M3–M12 with minimal paired controls (≈1,450–1,750 evaluation units). Superseded by the V4 §10 fallback. Retained for provenance only.*

## APPENDIX H3. [HISTORICAL — V3] Cumulative Drawdown, Workload Arithmetic, and Planning Bases (Superseded)

*Preserved V3 context. The 24-month drawdown table (M3 $50k → M24 $400k), the Table 8.0 workload decomposition (≈4,600 primary + ≈3,300 confirmatory trajectories), and the §5 compute/infrastructure/security bases (including the narrow-before-overspend rule and ordered deferral list) are retained in git history and superseded by V4 §§2–§5 and §11. The narrow-before-overspend policy itself carries forward into V4 §11.*
