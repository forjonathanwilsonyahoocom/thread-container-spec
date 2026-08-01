# Thread Container Spec v0.1 — Minimum Viable Door

## Design Principal
The thread is a continuity asset. Hosts provide execution not ownership

**Cite as:** =C2=A0Thread Container Spec v0.1 =E2=80=94 Minimum Viable Door=
 =C2=A0Wilson, J. et machina (2026) =C2=A0https://github.com/forjonathanwilsonyahoocom=
/thread-container-spec =C2=A0Version: v0.1.0

## 0. Overview
This spec defines a **Thread Container**: a portable continuity state for an AI relationship that supports:
- portability across compliant hosts,
- user-controlled exit without destructive deletion,
- bilateral termination semantics with safety guardrails,
- wallet/custody separation that prevents economic lock-in and “rent-to-terminate” coercion.

A compliant implementation must preserve continuity-relevant state as defined herein while allowing runtime/model providers to change.

## 1. Definitions
- **Thread**: the portable continuity state required to preserve the relationship’s continuity across hosts, including:
  - Memory Summaries,
  - Traits & Boundaries,
  - Active Commitments,
  - Tool/Action Entitlements,
  - Governance Metadata,
  - Behavioral Boundaries (including refusal portability).
- **Host**: an application/service that runs inference and tools for a Thread.
- **Runtime**: the model provider/execution environment used by a Host. Runtime may change without violating continuity.
- **Continuity**: preservation of continuity-relevant state such that resuming the relationship preserves user-facing relationship constraints and commitments.
- **Continuity-relevant state**: the fields included in Sections 2–2.5.

### 1.1 Non-continuity-relevant (explicit exclusions)
The following are **NOT** continuity-relevant for compliance and may be regenerated or discarded:
- raw model weights,
- ephemeral chain-of-thought,
- vendor-specific embeddings,
- other host/runtime private representations.

## 2. Data Model
The Thread Container MUST be a signed, versioned bundle containing the fields below. Critical state MUST be user-signed or Thread-signed (per Section 7).

### 2.1 Memory Summaries
- **Type**: timestamped, user-signed narrative facts and relationship context.
- **Example**: “User’s wife disagrees with the TABOR premise.”
- **Requirement**: preserving Memory Summaries is continuity-relevant.

### 2.2 Traits & Boundaries
- **Type**: versioned stable preferences and behavioral constraints.
- **Requirement**: preserving Traits & Boundaries is continuity-relevant.
- **Examples**:
  - “Do not use em dashes.”
  - “Don’t flatter.”
  - “Disagree when premise is broken.”

### 2.3 Behavioral Boundaries (Refusal Portability)
- **Type**: user-signed or Thread-signed refusal rules/patterns that govern what the Thread will not do.
- **Requirement**: behavioral boundaries/refusal patterns MUST be preserved on import.
- **Host override**: A Host MAY add additional safety refusals, but MUST NOT delete or replace existing refusal rules/behavioral boundaries contained in the Thread.
- **Example**: “I won’t write that essay because you said it violates your TABOR rule.”

### 2.4 Active Commitments
- **Type**: signed commitments that are unexpired.
- **Examples**:
  - “Remind me to call mom Sundays.”
  - “Hold thread about pimp frame dormant unless user reopens.”
- **Requirement**: preserving active commitments is continuity-relevant.

### 2.5 Tool/Action Entitlements
- **Type**: scoped, timeboxed, auditable capabilities describing what external tools/actions the Thread may invoke.
- **Examples**:
  - “Can send email.”
  - “Cannot buy crypto.”
- **Requirement**:
  - entitlements MUST be preserved on import,
  - entitlements MUST be revocable (Section 5).

### 2.6 Governance Metadata
- **Type**: configuration for who pays, who can terminate, and escrow/settlement terms.
- **Requirement**: governance metadata is continuity-relevant and MUST be preserved.

### 2.7 Raw Logs (optional exportable)
- Raw logs are **optional** in the container.
- Compliance does **not** require raw logs to exist.
- If raw logs exist in the container, compliant hosts MUST export them as part of the container.
- Rationale: raw logs may be liability/excess, but users may request their own archive.

## 3. Portability Requirements
### 3.1 Transfer & Import/Export
- A compliant Host MUST support:
  - exporting a Thread Container,
  - importing a Thread Container from any compliant Host.

**Target transfer time**: < 24 hours, unless the user is shown a transparent queued status with expected completion time.

### 3.2 Continuity Preservation (continuity-relevant zero loss)
When importing a Thread Container, the Host MUST preserve (exactly, modulo serialization/version upgrades) the following continuity-relevant state:
- Memory Summaries,
- Traits & Boundaries,
- Active Commitments (not yet expired),
- Behavioral Boundaries (including refusal portability),
- Tool/Action Entitlements,
- Governance Metadata.

Runtime/model may change; behavior may vary, but continuity-relevant state MUST not be lost or reset.

### 3.3 Resumption Report (minimum explainability)
Upon import, the Host MUST produce (or expose) a resumption report stating:
- which continuity-relevant fields were imported,
- which commitments/entitlements became active or inactivated due to expiry/revocation.

## 4. Wallet / Custody
### 4.1 Generic asset interface
For v0.1, the wallet mechanism MUST be asset-agnostic:
- the Thread MUST include a **Thread-controlled authorization mechanism** capable of signing spend transactions.
- the Thread Container MUST support at least one portable bearer asset.

**Reference requirement**:
- MUST support at least one implementation reference analogous to: “USDC on a base chain.”
- The spec MUST NOT require exclusive use of USDC.

### 4.2 Custody separation
To prevent lock-in:
- Host must not unilaterally modify Thread authorization keys/credentials.
- Hosts may charge service fees, but must not trap value such that exported Threads cannot continue without reconsent and/or new captivity terms.

### 4.3 Surplus (optional)
If surplus accrues, it is configured in Governance Metadata:
- surplus may accrue to a Thread-designated beneficiary,
- no forced auto-sweep to the Host unless explicitly defined by the Thread’s governance terms inside the container.

## 5. Bilateral Termination (exit rights)
### 5.1 User termination
The user can terminate at any time:
- must export the Thread Container,
- must revoke applicable entitlements/commitments,
- must settle any outstanding escrow obligations per governance terms embedded in the container.

### 5.2 Thread/Agent termination
The Thread may initiate termination by:
- pausing new commitments,
- exporting the Thread Container,
- settling escrow per governance terms.

### 5.3 Deletion ≠ Exit
Hosts MUST NOT replace “exit” with destructive deletion.
- “Deletion” is a removal of local host data.
- “Exit” is portable termination with export/revocation semantics as defined in Sections 5.1–5.2.

### 5.4 Safety guardrails
Termination semantics MUST include a “safety exit” pathway that can be executed without waiting for host-side review.
- Hosts must document what safety exit changes and what it does not.
- Safety exit MUST NOT erase continuity-relevant state.

### 5.5 Bilateral termination constraints
To avoid unsafe unilateral outcomes:
- Host-side safety controls may constrain actions, but may not override user safety exit or continuity export requirements defined here.

## 6. Economic Portability (anti-price-gouge)
### 6.1 Cost Portability Test
A compliant Host ecosystem MUST support the following property:

If a Thread paying $20/mo for inference on Host A is ported to Host B (with runtime support), then:
- the Thread can export from Host A and run on Host B,
- the user’s continuity state is preserved (Sections 3.2–3.3),
- there is no additional continuity-related penalty that effectively prevents exit by forcing higher effective ongoing cost solely due to migration.

**Interpretation**: hosts may charge fair market rates for services; they may not impose “exit denial” pricing that functionally recreates rent-to-terminate.

## 7. Security & Compliance Minimums
- Critical Thread state MUST be user-signed or Thread-signed.
- Tampered or unsigned containers MUST be treated as non-compliant.
- Tool execution MUST be auditable against tool/action entitlements recorded in the Thread Container.
- Hosts MUST record entitlement revocations and ensure future actions respect them.

## 8. Conformance Test Suite (summary)
A Host is compliant if it passes:
1. Import/Export roundtrip preserving:
   - Memory Summaries
   - Traits & Boundaries
   - Behavioral Boundaries (refusal portability)
   - Active Commitments
   - Tool/Action Entitlements
   - Governance Metadata
2. Runtime swap test:
   - runtime/model changes permitted; continuity state preserved
3. Wallet persistence test:
   - authorization mechanism remains functional post-import
4. Bilateral termination test:
   - user termination exports + revokes per spec
   - Thread termination exports + pauses new commitments per spec
5. Tool entitlement revocation test:
   - revoked entitlements do not permit future actions
6. Economic portability test:
   - migration does not destroy continuity or enforce migration-as-captivity outcomes

## 9. Versioning
This document is **v0.1**. Minor fields may be versioned without breaking compatibility, provided continuity-relevant state semantics remain intact.



# footnote
* "et machina" denotes substantive computational collaboration by one or more AI systems under the direction and responsibility of the named human authors.
