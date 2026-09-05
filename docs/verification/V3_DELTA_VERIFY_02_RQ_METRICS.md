# V3 Delta Verification: RQ Protocols and Metrics

**Date:** September 4, 2026  
**Target:** `docs/submission/06_CORE_RESEARCH_PROGRAM.md`

## Verification Checks Passed
- **ATR Metric Definition & Dual-Mode PASS (H6, H7):** Refined the Core RQ5 protocol to formally define the Adaptation Transfer Ratio (ATR), including explicit handling of positive, zero, and negative transfer edge cases. Introduced dual-mode evaluation at Gate M15: Mode A (Portable Generalization: $\text{ATR} \ge 0.80$, bootstrap CI lower bound $> 0.60$) and Mode B (Safely Bounded Specialization: when $\text{ATR} < 0.50$, Engine 3 reliably detects specificity, rejects unconstrained global promotion, and isolates the adaptation with zero downstream regression).
- **RQ7 Workload & IAM Protocol (H8):** Drafted a formal experimental workload for RQ7 involving 200 synthetic integration sessions across 3 IAM models (OIDC/OAuth 2.0, AWS IAM assume-role, scoped agentic IDP manifest) under 4 adversarial injection suites (50 token replays, 50 parameter-smuggled privilege escalations, 50 out-of-scope requests, 50 mid-trajectory asynchronous revocations) against the $\text{UER} \le 0.001$ threshold.
- **RQ Numbering & Causal Sequence (C6, H9):** Fully mapped and documented all seven Research Questions: RQ1 (State Classification), RQ2 (Causal Spine Reconstruction), RQ3 (Authority & Effect Gate), RQ4 (Verified Adaptation), RQ5 (Adaptation Portability & Safe Specialization), RQ6 (Long-Horizon Survival & MDDD), RQ7 (Cross-Model Replication & Delegated Trust Integration).
- **MDDD Survival Hazard Model:** Retained discrete survival analysis with Kaplan-Meier right-censoring and competing-risks sensitivity modeling.

**Status:** V3 DELTA VERIFIED

---

## ADDENDUM (September 5, 2026 review — do not delete)

Protocols above are retained; the following statistical limits were added to `06_CORE_RESEARCH_PROGRAM.md` after this report: three-arm (A/B/C) comparisons required for RQ3/RQ6; 0/1,000 → 95% upper ≈0.003 (confirmatory $N \approx 3{,}000$ for ≤0.001); 0/200 → upper ≈0.015 (mock-IAM pilot only, live deferred to M24); ATR denominator guardrail ($\Delta P_{\text{source}} \ge 5\text{pp}$) with selection-bias disclosure; MDDD bootstrap-CI requirement plus joint success/cost gate; power values labeled preliminary with effect-size assumptions; Table 6.2 gate-evidence mapping; "not yet preregistered" disclaimer.
