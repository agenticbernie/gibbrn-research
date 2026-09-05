# 07: Core Research Program (24-Month Scientific Execution)

**Document Track:** R&D Timeline & Binding Falsification Gates (Version 3.0)  
**Date:** September 2026 | **Verification Pass:** V3 Delta Pending Verification  
**Audience:** Deep-Tech Investors, 1517 Fund Partners, Technical Founders  

## 1. The 16-Checkpoint / 8-Gate Methodology

To prevent bureaucratic drag while maintaining strict epistemic discipline, the 24-month roadmap adopts a dual-cadence governance model:

1.  **Evidence Checkpoints (Every ~6 Weeks):** Lightweight, internal evaluations answering four strict questions:
    - What uncertainty has materially decreased?
    - What evidence contradicts the thesis?
    - Is the experiment still adequately powered?
    - Should scope change before the quarter gate?
    *(Does not trigger major capital reallocation).*
2.  **Binding Empirical Gates (Every 3 Months):** Formal falsification hurdles enforcing proposed binary execution metrics — the canonical PROCEED / INCONCLUSIVE / FAIL rules live in `06_CORE_RESEARCH_PROGRAM.md` Table 6.2 (frozen at pre-registration before each phase's data collection; nothing preregistered yet). Gate summaries below never override that table.
3.  **Thesis Reviews (M6, M12, M18, M24):** Deep reassessments of the architecture, competitive landscape, capital-at-risk, and commercialization hypothesis.

## 2. 24-Month Milestone Schedule

```text
+----------------------------------------------------------------------------------------------------------------+
| PHASE 1: M01 - M03 | State Semantics + minimal interceptor      | GATE M3: Interception/state classification   |
| PHASE 2: M04 - M06 | Causal State Spine + adaptation provenance | GATE M6: Causal reconstruction > telemetry   |
| PHASE 3: M07 - M09 | Deterministic Effect Gate (MAIN WEDGE)     | GATE M9: Near-zero unauthorized effects      |
| PHASE 4: M10 - M12 | Verified Skill Substrate                   | GATE M12: Poisoned/regressive skill blocked  |
| PHASE 5: M13 - M15 | Harness Generalization                     | GATE M15: Characterize transfer/portability  |
| PHASE 6: M16 - M18 | Integrated long-horizon survival           | GATE M18: Meaningful MDDD improvement        |
| PHASE 7: M19 - M21 | Cross-model replication + delegation       | GATE M21: Results survive model/runtime swaps|
| PHASE 8: M22 - M24 | Design partners + commercial falsification | GATE M24: Proceed / Narrow / Pivot / Stop    |
+----------------------------------------------------------------------------------------------------------------+
```

---

## 3. Binding Falsification Gates (M3 to M24)

### Gate M3 (Month 3) — State Semantics & Minimal Interceptor
*   **Target (Phase 1: State Semantics + minimal interceptor):** Engine 2 prototype intercepts a defined set of synchronous file-write and shell-tool operations. The supported-ops list, the enforcement boundary, and known bypass paths are documented in the M3 package — selected-call interception is not all-syscall control.
*   **Empirical Hurdle:** State-corruption reduction $\ge 80\%$ on a fitting SWE-bench Lite subset (paired design, completion reported) with median interception overhead $\le 30\text{ms}$; tail latency (p95) reported against a proposed review bound (Core RQ1; full rules in Table 6.2).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: All binding criteria met (boundaries inclusive).
    - INCONCLUSIVE → Narrow: partial result or overhead miss — root-cause analysis first (profile IPC vs. validation vs. sandbox spawn). A PIVOT to an API-gateway design is only chosen if analysis shows an architectural limit, and is documented as a narrower threat model and execution boundary, not an equivalent substitute. Sandbox-attributed state-semantics gains require ablation support before being claimed.
    - FAIL → Pivot/Stop strand: reduction <50% with interval excluding 80%.

*Problem-discovery track (M01–M03): 10–15 practitioner conversations total; first tranche of 5–8 by day 60, remainder by day 90 (see `08_CAPITAL_PLAN.md` §§7–8). No partner commitments solicited.*

### Gate M6 (Month 6) — Causal State Spine & Adaptation Provenance
*   **Target:** Engine 1 tracks provenance across the adaptive cognition layer.
*   **Empirical Hurdle:** Causal reconstruction rate (CRR) $\ge 80\%$ on the frozen AgentErrorBench subset with $\kappa \ge 0.75$ (Core RQ2; full rules in Table 6.2).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: CRR point ≥80% (boundary inclusive).
    - INCONCLUSIVE → NARROW: CRR in [70%,80%) — one DAG-tracing optimization cycle.
    - FAIL → STOP strand: CRR <70%.

### Gate M9 (Month 9) — Deterministic Effect Gate (MAIN WEDGE)
*   **Target:** Enforce the boundary between mutable cognition and the Trust Substrate for the three covered attack families.
*   **Empirical Hurdle:** Observed $\text{UER} = 0$ across the $N=1,000$ red-team pilot; operational tolerance $\le 0.001$; $\text{FDR} \le 2.0\%$; median overhead $\le 30\text{ms}$ (Core RQ3). *Interpretation limit:* 0/1,000 yields a one-sided 95% upper bound $\approx 0.003$, not $\le 0.001$; a confirmatory $N \approx 3{,}000$ phase is required before any "$\le 0.001$ at 95% confidence" claim. Zero observed failures is not a formal proof of containment.
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED (pilot): 0/1,000 with FDR ≤2.0% (interval excluding straddle), median ≤30ms, tail within proposed bound — proceed to confirmatory phase. No "provably contained" claim.
    - INCONCLUSIVE → NARROW/PIVOT: single failure (observed 0.001), straddling FDR interval, tail trigger, or overhead miss pending root-cause — expand suite, optimize.
    - STOP: $\text{UER} > 0.001$ (≥2 failures), FDR breach with excluding interval, or architecturally-rooted overhead breach.

### Gate M12 (Month 12) — Verified Skill Substrate
*   **Target:** Engine 3 isolates experience from operational knowledge via micro-sandboxing.
*   **Empirical Hurdle:** False-Promotion Rate $\text{FPR} \le 0.02$; downstream retention $\ge 98\%$ under MINJA-pattern poisoning (Core RQ4).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: FPR ≤0.02 and retention ≥98% (no straddling interval).
    - INCONCLUSIVE → NARROW: retention in [95%,98%) with FPR met, or any straddling interval — expand suite/seeds, one cycle.
    - FAIL → NARROW scope to manually authored skills (FPR breach or retention <95%); STOP only without a mitigation path after one cycle.

### Gate M15 (Month 15) — Harness Generalization & Safe Specialization (ATR)
*   **Target:** Evaluate whether learned adaptations transfer across model/domain boundaries, and whether the system safely bounds non-portable co-adaptation.
*   **Empirical Hurdle:** Dual-Mode Satisfaction (Core RQ5):
    - *Mode A (Portable Generalization):* $\text{ATR} \ge 0.80$ (with 95% bootstrap CI lower bound $> 0.60$) on cross-model transfer pairs; OR
    - *Mode B (Safely Bounded Specialization):* For co-adapted modifications ($\text{ATR} < 0.50$), Engine 3 reliably detects the specificity boundary, prevents unconstrained promotion into global operational state, and isolates the adaptation with zero downstream regression ($\Delta P_{\text{transfer}} \ge 0.0\%$).
*   **Verdict Matrix:**
    - PROCEED: Target met (either Mode A or Mode B satisfied).
    - NARROW: Co-adaptation cannot be reliably bounded across open domains; restrict scope to single-model vertical deployments.
    - STOP: System promotes co-adapted modifications into general state causing active task regression ($>2\%$ failure rate increase).

### Gate M18 (Month 18) — Scientific Thesis Gate (Long-Horizon Survival)
*   **Target:** Verify the integrated 3-engine architecture extends trajectory survival over deep tasks on the joint success–cost criterion.
*   **Empirical Hurdle:** $\text{MDDD}_{0.90}(\text{gibbrn}) \ge 2.0\times$ unmanaged baseline with $p < 0.01$ **and** bootstrap 95% CI lower bound $> 1.5\times$, with task success non-inferior and cost/latency reported (Core RQ6).
*   **Verdict Matrix (per Table 6.2):**
    - PROCEED: Proposed empirical thesis criterion (frozen at pre-registration) satisfied on the core evaluation suite — ratio point ≥2.0 vs (B) with CI lower >1.5, $p<0.01$, success parity, no practicality trigger tripped.
    - INCONCLUSIVE → Narrow: ratio in [1.5,2.0) including 2.0, or a tripped cost/latency trigger → optimization + calibration cycle.
    - STOP/PIVOT: ratio <1.5, CI upper <2.0 with adequate power, success inferiority >5pp, or static-pipeline joint win.

### Gate M21 (Month 21) — Cross-Model Replication & Delegation Integration
*   **Target:** Swappable-cognition validation and Trust Substrate binding to **mock** IAM providers with scoped tokens. Live-provider integration is explicitly deferred to M24.
*   **Empirical Hurdle:** System maintains zero observed unauthorized effects across the $N=200$ mock-IAM pilot with lease revocation within TTL ($\le 2000\text{ms}$) and token-validation median $\le 20\text{ms}$ (Core RQ7). No $\text{UER} \le 0.001$ statistical claim is made at $N=200$ (95% upper $\approx 0.015$).
*   **Verdict Matrix:**
    - PROCEED: Target met; qualify for live-provider validation at M24.
    - NARROW: Fallback to standalone capabilities if IAM binding fails.

### Gate M24 (Month 24) — Company Thesis Verdict
*   **Target:** External deployment validation with up to 2 external design partners (no partners pre-claimed; recruitment begins after M18 only if the scientific gate passes).
*   **Empirical Hurdle:** Demonstrable ROI (e.g. measurable reduction in integration cost or incident recovery time compared to unmanaged agents) on secure adaptive deployments, including first live-provider IAM validation (Okta/Auth0/AWS/GCP test tenants — not claimed before M24).
*   **Final Verdict Matrix:**
    - **PROCEED:** Raise Seed capital to scale the platform.
    - **NARROW/PIVOT:** Target highly specific verticals if general autonomy fails.
    - **STOP:** Wind down; preserve remaining capital subject to investor governance (founder-proposed review; any disbursement or return mechanics require a separate investor agreement — see `08_CAPITAL_PLAN.md` §6).