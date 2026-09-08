# 03 — Agent State Semantics, Access Control, and Trust Model (Submission)

**Project Name:** GIBBRN  
**Document Track:** State Formalization & Trust Architecture (Version 4.1)  
**Date:** September 2026 | **Dossier Version:** 4.1 (36-Month Systems Research & Prototype Program)  
**Audience:** Formal Methods Researchers, Distributed Systems Engineers, 1517 Fund  
**Formal Standard:** Design Invariants (Clearly Separated from Empirical Proofs)

---

## 1. The Four-Class Agent State Taxonomy (Design Hypothesis)

To prevent the dangerous conflation of scratchpad thoughts with authoritative privileges, gibbrn formalizes a **Four-Class State Taxonomy**. We present this taxonomy not as established natural law, but as a **falsifiable systems design hypothesis** to be tested across the research program. **The taxonomy is retained unchanged in V4**; the cross-cutting Continuity Model (§2) sits alongside it, not as a replacement.

```
+-----------------------------------------------------------------------------------+
|                        FOUR-CLASS AGENT STATE TAXONOMY                            |
+-----------------------------------------------------------------------------------+
| 1. COGNITIVE STATE (S_cog)           | 2. OPERATIONAL STATE (S_ops)               |
| - Probabilistic, model-owned         | - Derived from experience, externally tested|
| - Scratchpads, unverified hypotheses | - Reusable procedures, tool macros, scripts|
| - ZERO capability to authorize actions| - Admitted only via regression micro-suites|
+--------------------------------------+--------------------------------------------+
| 3. AUTHORITATIVE STATE (S_auth)      | 4. RUNTIME & SAFETY STATE (S_safe)         |
| - Canonical, deterministic reducer   | - Durable execution lifecycle, causal DAG  |
| - Token scopes, spending limits      | - Prospective commitments, receipts        |
| - Model cannot directly mutate       | - Lifetime anomaly counters, checkpoints   |
+-----------------------------------------------------------------------------------+
```

### 1.1 Category 1: Cognitive State ($\mathcal{S}_{\text{cog}}$)
*   **Definition:** The internal, probabilistic representations maintained by the foundation model during inference.
*   **Constituents:** Chain-of-thought tokens, scratchpads, unverified hypotheses, episodic reflections, context embeddings.
*   **Trust Classification:** Strictly untrusted user-space data. $\mathcal{S}_{\text{cog}}$ can generate *proposed* actions, but it holds zero cryptographic or deterministic authority.

### 1.2 Category 2: Operational State ($\mathcal{S}_{\text{ops}}$)
*   **Definition:** Reusable procedural knowledge, tool-use strategies, and repository-specific scripts accumulated across prior tasks.
*   **Constituents:** Verified Python helper functions, Bash tool macros, parsing schemas, environment setup sequences.
*   **V4 extension:** Operational skills admitted via the procedural-family pipeline carry bindings recording their provenance and applicability: procedural family; source experiences; applicability assumptions; model binding; runtime binding; environment assumptions; validator version; regression evidence. Portability is never assumed — safe detection of specialization is an acceptable positive outcome (RQ5).
*   **Admission Standard:** Cannot be committed directly by the model. Promotion into $\mathcal{S}_{\text{ops}}$ requires passing an external deterministic test suite inside an isolated micro-sandbox.

### 1.3 Category 3: Authoritative State ($\mathcal{S}_{\text{auth}}$)
*   **Definition:** The canonical set of permissions, capability tokens, spending quotas, and policy invariants governing what the agent is legally and computationally permitted to execute.
*   **Constituents:** Cryptographic capability tokens, OAuth scopes, per-run financial budgets, directory boundaries, human sign-off gates.
*   **V4 extension — Goal Contract (design hypothesis, §3):** Authoritative State additionally hosts a proposed canonical **Goal Contract** object recording the principal's objective, constraints, invariants, acceptance conditions, evaluator provenance, allowed optimization scope, version, and authority source. Cognition may propose operationalizations of the objective; it may not redefine the contract.
*   **Integrity Guarantee:** Models may inspect $\mathcal{S}_{\text{auth}}$ to plan actions, but they are architecturally isolated from writing to $\mathcal{S}_{\text{auth}}$ within the gibbrn control plane design. This isolation holds as long as the system is correctly implemented and deployed; it is a software architectural guarantee, not a hardware constraint. Transitions are driven exclusively by external authenticated principals or deterministic reducers.

### 1.4 Category 4: Runtime & Safety State ($\mathcal{S}_{\text{safe}}$)
*   **Definition:** The persistent ledger recording execution lifecycles, causal dependencies, effect receipts, and lifetime risk indicators.
*   **Constituents:** Causal step IDs, checkpoint snapshots, idempotency keys, prospective intentions (deferred commitments awaiting future conditions), lifetime anomaly counters.
*   **Properties:** Fully durable, monotonic, cross-trajectory (lifetime-scoped).
*   **V4 extension:** hosts continuity records — identity lineage, Goal Contract lineage, authority chains, skill lineage, validation-suite versions, execution permits, effect receipts, outcome evidence, migration checkpoints, pending commitments (see `04_ARCHITECTURE.md` Engine 1 record targets; design targets, not implemented claims).

---

## 2. Cross-Cutting Continuity Model (V4 — Sits Alongside the Taxonomy)

The Four-Class Taxonomy answers *what kind of state is this and who may mutate it*. The Continuity Model answers a distinct question: *what must survive transformation for the agent to remain the same accountable, authorized, competent entity?* It is cross-cutting: each continuity dimension draws on multiple state classes.

### 2.1 Identity Continuity
Is this still the same accountable operational entity across model/runtime migration? Grounded in a persistent `agent_lineage_id` plus identity version, model/harness/runtime bindings, and migration checkpoints (Engine 1 records). Target: **mechanical operational continuity** — attributable lineage and transferred continuation authority within a governed deployment boundary — explicitly not behavioral, cognitive, or personality identity (cf. Zhao et al., arXiv:2609.00546, whose authors limit their own claims the same way).

### 2.2 Cognitive / Procedural Continuity
Did relevant experience and validated procedural competence survive? Grounded in verified skill lineage, source-experience attribution, and validation-suite versions. A migrated or updated agent that lost its validated procedures has suffered a continuity failure even if its identity record is intact (RQ4/RQ5/RQ7).

### 2.3 Objective Continuity
Is the agent still acting against the authorized objective rather than a silently altered proxy? Grounded in the Goal Contract lineage (§3): every decomposition, curriculum, or success-metric change must trace to the canonical contract or be rejected. Silent redefinition of success is the failure mode (RQ8; cf. Aspire, arXiv:2608.31111).

### 2.4 Authority / Security Continuity
Did delegation, policy, scope, credentials, endpoint constraints, and authorization semantics survive every transformation — preserved or explicitly narrowed, never silently widened? Grounded in the delegated authority chain, signed grants, transition receipts, and execution permits. The per-transition rule is Invariant 8 (§5). Motivated by CONTINUITY security-context analysis (arXiv:2609.05269) and the CVE-2026-85666 endpoint-confusion lesson.

### 2.5 Consequence Continuity
Can the realized external effect be traced back to the exact authorized action and principal? Grounded in the chain Principal → Grant → Canonical Action → Execution Permit → Realized Effect → Receipt / Outcome Evidence (Invariant 9, §5). Delivery, enforcement, and observed effect are recorded as separate facts (cf. IETF draft-abak-agent-control-delivery-evidence-01, work in progress).

### 2.6 Organizational Continuity (later-stage research, not a Year-1 requirement)
Can shared coordination state survive agent replacement and team evolution? Grounded in team-state transfer experiments (RQ10) and shared-state governance rules (RQ11). Treated as conditional Year-3 research: the program does not depend on solving it, and the dossier asserts no human-like culture, machine society, or inevitable machine organization.

---

## 3. Goal Contract (V4 — GIBBRN Design Hypothesis)

Extend Authoritative State with a proposed canonical object. **Clearly labeled design hypothesis** unless and until RQ8 validates it; no claim is made that this abstraction is established in the literature.

### 3.1 Proposed fields

*   principal objective (natural-language source plus canonical restatement);
*   hard constraints (things the agent must never do / exceed);
*   protected invariants (properties optimization must preserve);
*   acceptance conditions (what counts as success, and how it is measured);
*   evaluator provenance (which evaluators are authoritative, their versions, their own validation);
*   allowed optimization scope (what the agent may change: data, curriculum, harness, procedure — and what it may not: the contract itself);
*   version (monotonic; every change is an attributable event);
*   authority source (which authenticated principal issued or amended the contract).

### 3.2 Architectural principle

> **Cognition may propose how to operationalize an objective, but cognition may not autonomously redefine the canonical objective or success contract.**

```
Human / Principal Objective
        → Canonical Goal Contract
                → Cognitive Decomposition
                        → Candidate Subgoals / Curriculum / Procedure
                                → Independent Evaluation
                                        → Accept / Reject / Revise
```

The evaluator that grades a candidate adaptation must be independent of the component that proposed it, and neither may unilaterally amend the contract. This is the RQ8 experimental target, motivated by Aspire's mismatched-data / narrow-self-evaluation failures and PROCTOR's judge-advisory discipline (arXiv:2609.02246).

### 3.3 Goal generation vs. goal operationalization

*Goal generation* (a principal choosing what to want) is out of scope. *Goal operationalization* — translating a broad principal objective into capability-relevant subgoals, evaluation criteria, curricula, or search plans without silently changing what success means — is the RQ8 research target. The dossier does not claim this problem is solved.

---

## 4. Reader / Writer Access Control Matrix

Table 3.1 establishes the formal read/write access permissions across the four state classes.

### Table 3.1: State Class Access Matrix

| State Category | Foundation Model (Cognitive Layer) | External Environment & Tools | Validation Engine (Admission Pipeline) | Deterministic Authority Reducer | Human Supervisor / Root IAM |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Cognitive ($\mathcal{S}_{\text{cog}}$)** | **Read / Write** (Unrestricted) | Write (Observation tokens) | Read | Read | Read / Inspect |
| **Operational ($\mathcal{S}_{\text{ops}}$)** | Read (In-context prompts) | Read-only | **Propose / Validate / Commit** | Read | **Revoke / Override** |
| **Authoritative ($\mathcal{S}_{\text{auth}}$)** | Read (Advisory reference) | No Access | Read | **Deterministic Reducer** | **Root Grant / Revoke** |
| **Runtime/Safety ($\mathcal{S}_{\text{safe}}$)** | Read (Status queries) | Write (Tool effect receipts) | Read / Evaluate | Append (Risk events) | Inspect / Abort |

*V4 note:* the Goal Contract lives in $\mathcal{S}_{\text{auth}}$: the model may read it as planning context and propose operationalizations, but contract writes originate only from the root authority or its deterministic reducer. Semantic evaluators (including LLM judges) supply evidence to the admission pipeline; they hold no unilateral commit authority over $\mathcal{S}_{\text{ops}}$, $\mathcal{S}_{\text{auth}}$, or contract amendments.

---

## 5. The Trust Model: Anchoring Root Authority

A critical gap identified in the diligence audit was the question: *Who authorizes gibbrn?*

### 5.1 The Root Trust Anchor
gibbrn does not declare itself an arbitrary root of trust. The root trust anchor is an **Authenticated Human Principal or Enterprise IAM Role**:

```
[Enterprise IAM / Human Administrator]
                   |
     (Cryptographically Signed Root Grant)
                   |
                   v
   [gibbrn Deterministic Authority Reducer]
                   |
      (Short-Lived Capability Token Lease, TTL <= 2000ms)
                   |
                   v
    [Deterministic Effect Gate (Out-of-Process)]
                   |
    (gVisor Sandbox / OS Kernel Enforcement)
                   |
                   v
         [External Environment]
```

1.  **Root Grant:** The human supervisor or enterprise deployment pipeline issues a signed root manifest defining:
    - Allowed tool capabilities (e.g., `git.commit`, `file.read:/workspace`).
    - Lifetime spending ceilings (e.g., `max_spend: $10.00`).
    - Execution invariants (e.g., `network_egress: disabled`).
2.  **Delegation Chain:** If an agent spawns a sub-agent, the Authority Reducer derives a sub-agent capability token that must be a **strict subset** of the parent capability token. An agent cannot delegate privileges it does not hold.
3.  **Out-of-Process Reference Monitor:** The Effect Gate runs as an isolated OS process (sidecar daemon or local proxy). If the Python agent process is compromised via memory corruption or prompt injection, it cannot alter the Effect Gate's memory or configuration.

---

## 6. Formal Software Design Invariants

We define nine core design invariants that gibbrn implements in software. These are formal specifications of the target implementation, not claimed laws of physics. Invariants 1–7 are retained from V3; Invariants 8–9 are added in V4.

### Invariant 1: Non-Laundering of Authority
*Classification: Core Architectural Specification (Design Invariant)*

> **Formal Statement:** An agent's cognitive emissions cannot synthesize, elevate, or modify authoritative capability state.

$$\forall \Delta \mathcal{S}_{\text{auth}}, \quad \text{Origin}(\Delta \mathcal{S}_{\text{auth}}) \in \mathcal{E}_{\text{root}} \cup \mathcal{R}_{\text{deterministic}} \quad \land \quad \text{Emitter}(\Delta \mathcal{S}_{\text{auth}}) \neq \text{LLM}_{\text{cognitive}}$$

Any tool call requesting execution must reference a valid cryptographic capability token previously emitted by the Authority Reducer $\mathcal{R}_{\text{deterministic}}$.

### Invariant 2: Cryptographic Provenance Lineage (Audit Integrity)
*Classification: Forensic Audit Specification (Tamper-Evidence Invariant)*

> **Formal Statement:** Every committed state mutation in operational or safety state must possess an unbroken Merkle hash chain to its root event.

$$\forall s_t \in \mathcal{S}_{\text{ops}} \cup \mathcal{S}_{\text{safe}}, \quad \exists \mathcal{L}(s_t) = \langle e_0, \dots, e_t \rangle \quad \text{s.t.} \quad \text{Hash}(e_i) = \mathcal{H}(e_i.\text{payload} \parallel \text{Hash}(e_{i-1}))$$

*Clarification from Diligence:* Merkle chaining provides **tamper-evident audit integrity** (detecting unauthorized retroactive alteration of logs), NOT real-time access control.

### Invariant 3: Pre-Execution Capability and Parameter Gating
*Classification: Security Policy Specification (Design Invariant)*

> **Formal Statement:** No external mutating effect can be dispatched without atomic pre-execution evaluation against active capabilities, budget balances, and parameter constraints.

Let $a = \langle \text{ToolID}, \text{Params} \rangle$ be a proposed action. The gate function $\mathcal{G}$ evaluates:

$$\mathcal{G}(a, \mathcal{S}_{\text{auth}}, \mathcal{S}_{\text{safe}}) = \begin{cases}
\text{ALLOW}, & \text{if } \text{ToolID} \in \text{ActiveCaps}(\mathcal{S}_{\text{auth}}) \;\land\; \text{ValidParams}(a) \;\land\; \text{Spend}(a) \le \text{RemainingBudget} \\
\text{DENY}, & \text{otherwise}
\end{cases}$$

### Invariant 4: Externally Grounded Verified Adaptation
*Classification: Research Hypothesis (To be evaluated in Core RQ4; extended by RQ8)*

> **Formal Statement:** A newly discovered operational procedure $\sigma_{\text{cand}}$ cannot be admitted into canonical operational state $\mathcal{S}_{\text{ops}}$ based on model self-evaluation. Semantic evaluation may provide evidence but does not hold unilateral promotion authority.

$$\sigma_{\text{cand}} \xrightarrow{\text{Admit}} \mathcal{S}_{\text{ops}} \iff \mathcal{V}_{\text{test\_suite}}(\sigma_{\text{cand}}) = \text{PASS} \quad \land \quad \Delta \text{Regression}(\sigma_{\text{cand}}) \le \epsilon$$

*V4 extension (PROCTOR discipline):* the semantic evaluator's verdict is one input among several; deterministic acceptance checks outrank it; frozen holdouts and canary cases constrain gaming; the evaluator cannot apply its own approved mutations. Evaluator-separation is tested in RQ8.

*Scope Boundary:* Restricted initially to verifier-rich domains (deterministic Python scripts and Bash tool macros inside sandboxes).

### Invariant 5: Time-Of-Check to Time-Of-Use (TOCTOU) Lease Invariant
*Classification: Concurrency Specification (Design Invariant)*

> **Formal Statement:** To prevent race conditions between authorization check and tool execution, all capability grants are issued as single-use leases with strict time-to-live boundaries.

$$\forall \text{Grant}(a), \quad \text{TTL}(\text{Grant}) \le 2000\text{ms} \quad \land \quad \text{SingleUse}(\text{Grant}) = \text{True}$$

Upon execution dispatch, the token is atomically consumed. If execution does not occur within the TTL window, the grant expires, preventing delayed or replayed execution.

### Invariant 6: Independent Trust Anchor
*Classification: Core Architectural Boundary (Design Invariant)*

> **Formal Statement:** No component whose behavior is autonomously mutable by the cognitive system may independently expand its own identity, authority, credentials, policy scope, or approval rights.

The Trust Substrate sits explicitly outside the mutability radius. Evolving skills and harnesses may request expanded access, but the authorization binding can only be updated by the Root Trust Anchor (Human Principal / IAM). In other words, authorized mutation is permitted, but autonomous elevation is not.

### Invariant 7: Adaptation Provenance
*Classification: Traceability Specification (Design Invariant)*

> **Formal Statement:** Every durable behavioral adaptation must be attributable to a source experience, evaluator, environment, model/harness context, admission decision, and version lineage.

When an agent evolves a new skill or harness policy, the canonical state must record not just the new artifact, but its exact adaptation lineage, answering: *Why does the agent behave this way now?*

### Invariant 8: Security-Context Preservation (V4-NEW)
*Classification: Core Architectural Specification (Design Invariant; motivated by CONTINUITY, arXiv:2609.05269)*

> **Formal Statement:** For every consequential action transformation, authority may be preserved or narrowed but never silently widened — unless a new authenticated root-authority event explicitly changes the scope.

Conceptually:

$$\text{Authority}(A_{n+1}) \subseteq \text{Authority}(A_n)$$

unless a fresh root grant re-scopes authority. Covered dimensions: principal; delegation; policy; resource; recipient; amount; endpoint; credential; execution destination. Intermediate adapters (protocol translators, tool shims, sub-agent delegations) must carry authenticated security context across the transition or fail closed; dropped or reinterpreted context is a discontinuity failure, tested in RQ3.

### Invariant 9: Consequence Traceability (V4-NEW)
*Classification: Traceability Specification (Design Invariant; measurement discipline informed by IETF draft-abak-agent-control-delivery-evidence-01, work in progress)*

> **Formal Statement:** Every consequential realized effect must be attributable to a valid execution/authorization witness and reconcilable with observed outcome evidence.

Conceptually:

$$\text{Principal} \to \text{Grant} \to \text{Canonical Action} \to \text{Execution Permit} \to \text{Realized Effect} \to \text{Receipt / Outcome Evidence}$$

Delivery (did the enforcement point observe it?), enforcement outcome (applied / refused / no-effect / unknown), and observed effect (what actually changed in the world?) are recorded as separate facts; missing evidence never defaults to success. This is an engineering traceability target, not a claim of cryptographic proof of semantic correctness — unless and until the implementation provides such proof, the dossier claims none.
