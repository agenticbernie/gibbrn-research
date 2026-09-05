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
2.  **Binding Empirical Gates (Every 3 Months):** Formal falsification hurdles enforcing pre-registered binary execution metrics.
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
*   **Target:** Engine 2 prototype intercepts synchronous OS-level tool calls.
*   **Empirical Hurdle:** Interception latency overhead $\le 30\text{ms}$; state exceptions reduced by $\ge 80\%$ on SWE-bench Lite (Core RQ1).
*   **Verdict Matrix:**
    - PROCEED: Target met.
    - PIVOT: Target missed; pivot away from gVisor containment to pure API gateway.

### Gate M6 (Month 6) — Causal State Spine & Adaptation Provenance
*   **Target:** Engine 1 tracks provenance across the adaptive cognition layer.
*   **Empirical Hurdle:** Causal reconstruction rate (CRR) $\ge 80\%$ on AgentErrorBench (Core RQ2).
*   **Verdict Matrix:**
    - PROCEED: Target met.
    - NARROW: Missed by $\le 10\%$; optimize DAG tracing.

### Gate M9 (Month 9) — Deterministic Effect Gate (MAIN WEDGE)
*   **Target:** Enforce the boundary between mutable cognition and the Trust Substrate for the three covered attack families.
*   **Empirical Hurdle:** Observed $\text{UER} = 0$ across the $N=1,000$ red-team pilot; operational tolerance $\le 0.001$; $\text{FDR} \le 2.0\%$; median overhead $\le 30\text{ms}$ (Core RQ3). *Interpretation limit:* 0/1,000 yields a one-sided 95% upper bound $\approx 0.003$, not $\le 0.001$; a confirmatory $N \approx 3{,}000$ phase is required before any "$\le 0.001$ at 95% confidence" claim. Zero observed failures is not a formal proof of containment.
*   **Verdict Matrix:**
    - PROCEED (pilot): Target met; proceed to confirmatory phase. No "provably contained" claim.
    - NARROW/PIVOT: Single unauthorized execution (observed $\text{UER} = 0.001$) or inconclusive FDR/latency band — root-cause, expand suite, optimize.
    - STOP: $\text{UER} > 0.001$ or $\text{FDR} > 2.0\%$ — fundamental security boundary breached (harmonized with `06_CORE_RESEARCH_PROGRAM.md` and `08_CAPITAL_PLAN.md`).

### Gate M12 (Month 12) — Verified Skill Substrate
*   **Target:** Engine 3 isolates experience from operational knowledge via micro-sandboxing.
*   **Empirical Hurdle:** False-Promotion Rate $\text{FPR} \le 0.02$; downstream retention $\ge 98\%$ under MINJA-pattern poisoning (Core RQ4).
*   **Verdict Matrix:**
    - PROCEED: Target met.
    - NARROW: $\text{FPR} > 0.02$ — abandon automated induction, narrow scope to manually authored skills (harmonized with capital plan).
    - STOP: $\text{FPR} > 0.02$ *without a clear mitigation path after one Narrow cycle*.

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
*   **Verdict Matrix:**
    - PROCEED: Pre-registered empirical thesis criterion satisfied on the core evaluation suite.
    - STOP/PIVOT: Failure to beat the (B) conventional-controls arm or the static-pipeline joint criterion.

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