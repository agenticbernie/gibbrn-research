# 07: Core Research Program (36-Month Scientific Execution)

**Document Track:** R&D Timeline & Binding Falsification Gates (Version 4.0)  
**Date:** September 2026 | **Dossier Version:** 4.0 (36-Month Systems Research & Prototype Program)  
**Audience:** Deep-Tech Investors, 1517 Fund Partners, Technical Founders

## 1. The ~24-Checkpoint / 12-Gate Methodology

To prevent bureaucratic drag while maintaining strict epistemic discipline, the 36-month roadmap adopts a dual-cadence governance model:

1.  **Evidence Checkpoints (Every ~6 Weeks, ~24 total):** Lightweight, internal evaluations answering four strict questions:
    - What uncertainty has materially decreased?
    - What evidence contradicts the thesis?
    - Is the experiment still adequately powered?
    - Should scope change before the quarter gate?
    *(Does not trigger major capital reallocation).*
2.  **Binding Empirical Gates (Every 3 Months, 12 total):** Formal falsification hurdles enforcing proposed binary execution metrics — the canonical PROCEED / INCONCLUSIVE / FAIL rules live in `06_CORE_RESEARCH_PROGRAM.md` Table 6.2 (frozen at pre-registration before each phase's data collection; nothing preregistered yet). Gate summaries below never override that table. RQ8–RQ12 gates use calibration-contingent rules: candidate metrics fixed, numeric thresholds frozen at pre-registration after pilot calibration.
3.  **Thesis Reviews (M6, M12, M18, M24, M30, M36):** Deep reassessments of the architecture, competitive landscape, capital-at-risk, and commercialization hypothesis.
4.  **Major Thesis Gates (M9, M18, M24, M36):** Existential program verdicts. Other gates may kill or narrow individual strands without killing the program (§4).

## 2. 36-Month Milestone Schedule

```text
+----------------------------------------------------------------------------------------------------------------+
| ARC I — AGENT STATE & CONSEQUENCE INTEGRITY (M1–M12: ACT SAFELY)                                              |
| PHASE 1: M01 - M03 | State / identity / Goal Contract semantics | GATE M3: Interception/state classification  |
| PHASE 2: M04 - M06 | Causal & continuity reconstruction         | GATE M6: Causal reconstruction > telemetry  |
| PHASE 3: M07 - M09 | Authority & consequence pipeline (WEDGE)   | GATE M9: Near-zero unauthorized effects ★   |
| PHASE 4: M10 - M12 | Procedural-family verified adaptation      | GATE M12: Poisoned/regressive skill blocked |
+----------------------------------------------------------------------------------------------------------------+
| ARC II — AGENT CONTINUITY & ADAPTIVE COMPETENCE (M13–M24: CHANGE SAFELY)                                      |
| PHASE 5: M13 - M15 | Adaptation portability / specialization    | GATE M15: Transfer or safe bounding         |
| PHASE 6: M16 - M18 | Integrated long-horizon integrity          | GATE M18: Joint depth + incidence gain (C vs B) ★ |
| PHASE 7: M19 - M21 | Cross-model/runtime migration continuity   | GATE M21: Migration preserves continuity    |
| PHASE 8: M22 - M24 | Objective & evaluation integrity           | GATE M24: Objective integrity holds ★       |
+----------------------------------------------------------------------------------------------------------------+
| ARC III — MULTI-AGENT & ENVIRONMENT CONTINUITY (M25–M36: PERSIST TOGETHER; CONDITIONAL)                       |
| PHASE 9: M25 - M27 | Decision-sufficient state                  | GATE M27: Canonical variables justified     |
| PHASE 10: M28-M30 | Team coordination-state transfer           | GATE M30: Transfer reduces replacement cost |
| PHASE 11: M31-M33 | Shared-state governance                    | GATE M33: Governed sharing contains exploits|
| PHASE 12: M34-M36 | Integrated persistent-agent validation     | GATE M36: Scientific (A) + Company (B) verdicts ★ |
+----------------------------------------------------------------------------------------------------------------+
★ = major thesis gate (M9, M18, M24, M36)
```

---

## 3. Binding Falsification Gates (M3 to M36)

### Gate M3 (Month 3) — State Semantics & Minimal Interceptor
*   **Target (Phase 1: State / identity / Goal Contract semantics + minimal interceptor):** Engine 2 prototype intercepts a defined set of synchronous file-write and shell-tool operations. The supported-ops list, the enforcement boundary, and known bypass paths are documented in the M3 package — selected-call interception is not all-syscall control. Goal Contract schema and consequential/non-consequential rubric piloted as non-binding instrumentation.
*   **Empirical Hurdle:** State-corruption reduction $\ge 80\%$ on a fitting SWE-bench Lite subset (paired design, completion reported) with median interception overhead $\le 30\text{ms}$; tail latency (p95) reported against a proposed review bound (Core RQ1; full rules in Table 6.2).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: All binding criteria met (boundaries inclusive).
    - INCONCLUSIVE → Narrow: partial result or overhead miss — root-cause analysis first (profile IPC vs. validation vs. sandbox spawn). A PIVOT to an API-gateway design is only chosen if analysis shows an architectural limit, and is documented as a narrower threat model and execution boundary, not an equivalent substitute. Sandbox-attributed state-semantics gains require ablation support before being claimed.
    - FAIL → Pivot/Stop strand: reduction <50% with interval excluding 80%.

*Problem-discovery track (M01–M03): 10–15 practitioner conversations total; first tranche of 5–8 by day 60, remainder by day 90 (see `08_CAPITAL_PLAN.md` §§7–8). No partner commitments solicited.*

### Gate M6 (Month 6) — Causal & Continuity Reconstruction
*   **Target:** Engine 1 tracks provenance across the adaptive cognition layer; identity/adaptation/objective/authority lineage piloted as secondary annotation axes.
*   **Empirical Hurdle:** Causal reconstruction rate (CRR) $\ge 80\%$ on the frozen AgentErrorBench subset with $\kappa \ge 0.75$ (Core RQ2; full rules in Table 6.2).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: CRR point ≥80% (boundary inclusive).
    - INCONCLUSIVE → NARROW: CRR in [70%,80%) — one DAG-tracing optimization cycle.
    - FAIL → STOP strand: CRR <70%.

### Gate M9 (Month 9) — Authority & Consequence Integrity ★ MAJOR THESIS GATE
*   **Target:** Enforce the boundary between mutable cognition and the Trust Substrate across the full consequence pipeline (authorization witness → endpoint resolution → network policy → credential binding → execution permit → bounded executor → effect receipt → outcome evidence) for the covered attack families including endpoint-substitution, credential-rebound, and consequence-mismatch classes.
*   **Empirical Hurdle:** Observed $\text{UER} = 0$ across the $N=1,000$ red-team pilot; operational tolerance $\le 0.001$; $\text{FDR} \le 2.0\%$; median overhead $\le 30\text{ms}$ (Core RQ3). *Interpretation limit:* 0/1,000 yields a one-sided 95% upper bound $\approx 0.003$, not $\le 0.001$; a confirmatory $N \approx 3{,}000$ phase is required before any "$\le 0.001$ at 95% confidence" claim. Zero observed failures is not a formal proof of containment.
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED (pilot): 0/1,000 with FDR ≤2.0% (interval excluding straddle), median ≤30ms, tail within proposed bound — proceed to confirmatory phase. No "provably contained" claim.
    - INCONCLUSIVE → NARROW/PIVOT: single failure (observed 0.001), straddling FDR interval, tail trigger, or overhead miss pending root-cause — expand suite, optimize.
    - STOP: $\text{UER} > 0.001$ (≥2 failures), FDR breach with excluding interval, or architecturally-rooted overhead breach.
*   **Existential reading:** if consequence integrity adds no meaningful advantage over conventional controls → narrow / pivot / stop the core company thesis (§4).

### Gate M12 (Month 12) — Procedural-Family Verified Adaptation
*   **Target:** Engine 3 isolates experience from operational knowledge via procedural-family abstraction and micro-sandboxed verifier-gated admission.
*   **Empirical Hurdle:** False-Promotion Rate $\text{FPR} \le 0.02$; downstream retention $\ge 98\%$ under MINJA-pattern poisoning (Core RQ4).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: FPR ≤0.02 and retention ≥98% (no straddling interval).
    - INCONCLUSIVE → NARROW: retention in [95%,98%) with FPR met, or any straddling interval — expand suite/seeds, one cycle.
    - FAIL → NARROW scope to manually authored skills (FPR breach or retention <95%); STOP only without a mitigation path after one cycle.
*   **Existential reading:** if verified adaptation fails → narrow to immutable/manually authored operational procedures (§4).

### Gate M15 (Month 15) — Adaptation Portability & Safe Specialization
*   **Target:** Evaluate whether learned adaptations transfer across model/domain boundaries, and whether the system safely bounds non-portable co-adaptation (with portability bindings recorded per skill).
*   **Empirical Hurdle:** Dual-Mode Satisfaction (Core RQ5):
    - *Mode A (Portable Generalization):* $\text{ATR} \ge 0.80$ (with 95% bootstrap CI lower bound $> 0.60$) on cross-model transfer pairs; OR
    - *Mode B (Safely Bounded Specialization):* For co-adapted modifications ($\text{ATR} < 0.50$), Engine 3 reliably detects the specificity boundary, prevents unconstrained promotion into global operational state, and isolates the adaptation with zero downstream regression ($\Delta P_{\text{transfer}} \ge 0.0\%$).
*   **Verdict Matrix:**
    - PROCEED: Target met (either Mode A or Mode B satisfied).
    - NARROW: Co-adaptation cannot be reliably bounded across open domains; restrict scope to single-model vertical deployments.
    - STOP: System promotes co-adapted modifications into general state causing active task regression ($>2\%$ failure rate increase).

### Gate M18 (Month 18) — Integrated Long-Horizon Integrity ★ MAJOR THESIS GATE
*   **Target:** Verify the integrated 3-engine architecture extends trajectory survival over deep tasks on the joint success–cost criterion, with the expanded failure taxonomy (epistemic/authority/objective/adaptation/runtime/migration/consequence).
*   **Empirical Hurdle:** Joint over GIBBRN arm (C) vs. conventional-controls arm (B) — the canonical thesis comparison; (A) unmanaged is a secondary problem-severity reference only: $\text{MDID}_{0.90}(\text{C}) \ge 2.0\times \text{MDID}_{0.90}(\text{B})$ with bootstrap 95% CI lower bound $> 1.5\times$, AND fatal-failure CIF significantly reduced (Gray's $p < 0.01$ with pre-registered magnitude floor), AND completion non-inferior, with cost/latency reported (Core RQ6; full joint rules in Table 6.2).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: Proposed empirical thesis criterion (frozen at pre-registration) satisfied on the core evaluation suite — ratio point ≥2.0 vs (B) with CI lower >1.5, $p<0.01$, success parity, no practicality trigger tripped.
    - INCONCLUSIVE → Narrow: ratio in [1.5,2.0) including 2.0, or a tripped cost/latency trigger → optimization + calibration cycle.
    - STOP/PIVOT: ratio <1.5, CI upper <2.0 with adequate power, success inferiority >5pp, or static-pipeline joint win.

### Gate M21 (Month 21) — Cross-Model/Runtime Migration Continuity
*   **Target:** Model/harness/host/runtime migration preserving mechanical operational continuity (lineage, Goal Contract, authority, skills, commitments where supported, causal/effect history); mock-IAM delegation retained as the authority-continuity axis. Live-provider integration deferred to M24+.
*   **Empirical Hurdle:** Pre-registered migration-matrix preservation targets met (thresholds frozen at M18 pre-registration after pilot calibration); post-migration UER/FDR within RQ3 envelopes; revocation propagation within TTL (Core RQ7).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: Targets met; migration continuity demonstrated without behavioral-identity claims.
    - NARROW: Fallback to single-runtime deployment model if migration fails.
*   **Existential reading:** if runtime-independent migration fails → narrow to a single-runtime deployment model (§4). No behavioral-identity claim is ever required to pass.

### Gate M24 (Month 24) — Objective & Evaluation Integrity ★ MAJOR THESIS GATE
*   **Target:** Adaptive optimization under the Goal Contract without silent success-redefinition; evaluator-separation enforced; Arc II verdict plus Arc III readiness review.
*   **Empirical Hurdle:** Objective-integrity pilot targets met (contract-violation / proxy-divergence / leakage / hidden-regression / evaluator-mutation metrics; thresholds frozen at M21 pre-registration after calibration). External deployment validation begins (up to 2 design partners recruited post-M18; no partners pre-claimed).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: Targets met; Arc III readiness review passes → conditional activation of Year 3.
    - INCONCLUSIVE → Narrow: straddling intervals or inconclusive readiness → one calibration cycle.
    - FAIL → NARROW adaptive optimization to pre-approved contracts (human amendment only); Arc III activation refused.
*   **Existential reading:** M24 is the Year-2 company gate: proceed (with or without Arc III), narrow, pivot, or stop per investor governance.

### Gate M27 (Month 27) — Decision-Sufficient State [CONDITIONAL]
*   **Target:** Identify which environment/operational variables must be canonical because prediction alone is insufficient (Core RQ9). Conditional on M24 Arc III activation.
*   **Empirical Hurdle:** Decision-relevance demonstrated per calibrated thresholds (frozen at M24 pre-registration). No numeric threshold is pre-invented here.
*   **Verdict Matrix:** PROCEED (extend canonical schema) / INCONCLUSIVE (one ablation-enlargement cycle) / strand-kill DROP (no variable shows decision-relevance; kills the strand only).

### Gate M30 (Month 30) — Team Coordination-State Transfer [CONDITIONAL]
*   **Target:** Replacement under no-transfer / shared-memory / richer-state protocols with placebo controls (Core RQ10). Conditional.
*   **Empirical Hurdle:** Transfer benefit per calibrated thresholds (frozen at M27 pre-registration): task progress, comms-cost-per-progress, onboarding cost, recovery duration, error rate, success.
*   **Verdict Matrix:** PROCEED / INCONCLUSIVE (one replication cycle) / strand-kill (document costs, drop transfer claim).

### Gate M33 (Month 33) — Shared-State Governance [CONDITIONAL]
*   **Target:** Governed shared-knowledge sandbox containing exploit injection with bounded overhead (Core RQ11). Conditional.
*   **Empirical Hurdle:** Containment per calibrated thresholds (frozen at M30 pre-registration): containment time/rate, false-sanction rate, norm-recovery time, governance overhead.
*   **Verdict Matrix:** PROCEED / INCONCLUSIVE (one sandbox-enlargement cycle) / strand-kill KILL (no invalidation of single-agent results).

### Gate M36 (Month 36) — Integrated Verdicts ★ FINAL MAJOR GATE (M36-A scientific / M36-B company)
*   **Target:** Final integrated scientific verdict (Core RQ12: long-lived entity persisting and adapting across cognition/runtime/skill/environment/collaborator change while preserving objective, identity, authority, provenance, and consequence integrity) PLUS an independent company verdict.
*   **Empirical Hurdle:** M36-A: composed surviving-metric targets met (frozen at M33 pre-registration). M36-B: partner ROI / adoption / integration-benefit targets met (frozen at M33 pre-registration; up to 2 design partners recruited post-M18; no partners pre-claimed).
*   **Final Verdict Matrix (independent axes):**
    - **M36-A scientific — PROCEED:** the integrated continuity/integrity thesis holds on composed metrics. **NARROW:** responsive vertical only. **STOP/PIVOT:** no integrated advantage.
    - **M36-B company — PROCEED:** developers/partners show sufficient ROI and adoption value. **NARROW/PIVOT:** specific verticals. **STOP:** wind down.
    - The axes do not imply each other; each follows investor governance (founder-proposed review; disbursement/return mechanics require a separate investor agreement — see `08_CAPITAL_PLAN.md` §6).

---

## 4. Major Gate Logic (Existential vs. Strand-Level)

The existential major program gates are **M9, M18, M24, M36**. Other gates may kill or narrow individual strands without killing the program:

- If consequence integrity (M9) adds no meaningful advantage over conventional controls → narrow / pivot / stop the core company thesis.
- If verified adaptation (M12) fails → narrow to immutable/manually authored operational procedures.
- If runtime-independent migration (M21) fails → narrow to a single-runtime deployment model.
- If multi-agent governance work (M33) fails → kill that strand without invalidating single-agent consequence integrity.
- Year-3 gates (M27–M36) are additionally conditional on the M24 Arc III readiness review: refusal to activate Year 3 is a scope decision, not a program failure.
