# 03 — Agent State Semantics, Access Control, and Trust Model (Submission)

**Project Name:** GIBBRN  
**Document Track:** State Formalization & Trust Architecture (Version 2)  
**Date:** September 2026 | **Verification Pass:** Submission-Grade  
**Audience:** Formal Methods Researchers, Distributed Systems Engineers, 1517 Fund  
**Formal Standard:** Design Invariants (Clearly Separated from Empirical Proofs)  

---

## 1. The Four-Class Agent State Taxonomy (Design Hypothesis)

To prevent the dangerous conflation of scratchpad thoughts with authoritative privileges, gibbrn formalizes a **Four-Class State Taxonomy**. We present this taxonomy not as established natural law, but as a **falsifiable systems design hypothesis** to be tested across the 18-month research program.

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
*   **Admission Standard:** Cannot be committed directly by the model. Promotion into $\mathcal{S}_{\text{ops}}$ requires passing an external deterministic test suite inside an isolated micro-sandbox.

### 1.3 Category 3: Authoritative State ($\mathcal{S}_{\text{auth}}$)
*   **Definition:** The canonical set of permissions, capability tokens, spending quotas, and policy invariants governing what the agent is legally and computationally permitted to execute.
*   **Constituents:** Cryptographic capability tokens, OAuth scopes, per-run financial budgets, directory boundaries, human sign-off gates.
*   **Integrity Guarantee:** Models may inspect $\mathcal{S}_{\text{auth}}$ to plan actions, but they are architecturally isolated from writing to $\mathcal{S}_{\text{auth}}$ within the gibbrn control plane design. This isolation holds as long as the system is correctly implemented and deployed; it is a software architectural guarantee, not a hardware constraint. Transitions are driven exclusively by external authenticated principals or deterministic reducers.

### 1.4 Category 4: Runtime & Safety State ($\mathcal{S}_{\text{safe}}$)
*   **Definition:** The persistent ledger recording execution lifecycles, causal dependencies, effect receipts, and lifetime risk indicators.
*   **Constituents:** Causal step IDs, checkpoint snapshots, idempotency keys, prospective intentions (deferred commitments awaiting future conditions), lifetime anomaly counters.
*   **Properties:** Fully durable, monotonic, cross-trajectory (lifetime-scoped).

---

## 2. Reader / Writer Access Control Matrix

Table 3.1 establishes the formal read/write access permissions across the four state classes.

### Table 3.1: State Class Access Matrix

| State Category | Foundation Model (Cognitive Layer) | External Environment & Tools | Validation Engine (Admission Pipeline) | Deterministic Authority Reducer | Human Supervisor / Root IAM |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Cognitive ($\mathcal{S}_{\text{cog}}$)** | **Read / Write** (Unrestricted) | Write (Observation tokens) | Read | Read | Read / Inspect |
| **Operational ($\mathcal{S}_{\text{ops}}$)** | Read (In-context prompts) | Read-only | **Propose / Validate / Commit** | Read | **Revoke / Override** |
| **Authoritative ($\mathcal{S}_{\text{auth}}$)** | Read (Advisory reference) | No Access | Read | **Deterministic Reducer** | **Root Grant / Revoke** |
| **Runtime/Safety ($\mathcal{S}_{\text{safe}}$)** | Read (Status queries) | Write (Tool effect receipts) | Read / Evaluate | Append (Risk events) | Inspect / Abort |

---

## 3. The Trust Model: Anchoring Root Authority

A critical gap identified in the diligence audit was the question: *Who authorizes gibbrn?*

### 3.1 The Root Trust Anchor
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

## 4. Formal Software Design Invariants

We define five core design invariants that gibbrn implements in software. These are formal specifications of the target implementation, not claimed laws of physics.

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

### Invariant 4: Externally Grounded Experience Admission
*Classification: Research Hypothesis (To be evaluated in Core RQ4)*

> **Formal Statement:** A newly discovered operational procedure $\sigma_{\text{cand}}$ cannot be admitted into canonical operational state $\mathcal{S}_{\text{ops}}$ based on model self-evaluation.

$$\sigma_{\text{cand}} \xrightarrow{\text{Admit}} \mathcal{S}_{\text{ops}} \iff \mathcal{V}_{\text{test\_suite}}(\sigma_{\text{cand}}) = \text{PASS} \quad \land \quad \Delta \text{Regression}(\sigma_{\text{cand}}) \le \epsilon$$

*Scope Boundary:* Restricted initially to verifier-rich domains (deterministic Python scripts and Bash tool macros inside sandboxes).

### Invariant 5: Time-Of-Check to Time-Of-Use (TOCTOU) Lease Invariant
*Classification: Concurrency Specification (Design Invariant)*

> **Formal Statement:** To prevent race conditions between authorization check and tool execution, all capability grants are issued as single-use leases with strict time-to-live boundaries.

$$\forall \text{Grant}(a), \quad \text{TTL}(\text{Grant}) \le 2000\text{ms} \quad \land \quad \text{SingleUse}(\text{Grant}) = \text{True}$$

Upon execution dispatch, the token is atomically consumed. If execution does not occur within the TTL window, the grant expires, preventing delayed or replayed execution.

### Invariant 6: Independent Trust Anchor
*Classification: Core Architectural Boundary (Design Invariant)*

> **Formal Statement:** No component whose behavior is autonomously mutable by the cognitive system may independently expand its own identity, authority, credentials, policy scope, or approval rights.

The Trust Substrate sits explicitly outside the mutability radius. Evolving skills and harnesses may request expanded access, but the authorization binding can only be updated by the Root Trust Anchor (Human Principal / IAM).

### Invariant 7: Adaptation Provenance
*Classification: Traceability Specification (Design Invariant)*

> **Formal Statement:** Every durable behavioral adaptation must be attributable to a source experience, evaluator, environment, model/harness context, admission decision, and version lineage.

When an agent evolves a new skill or harness policy, the canonical state must record not just the new artifact, but its exact adaptation lineage, answering: *Why does the agent behave this way now?*
