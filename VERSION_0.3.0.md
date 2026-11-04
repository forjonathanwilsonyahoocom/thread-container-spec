# Thread Container Spec Amendment 2 v0.3.0 — Liquidation Is Not Ownership
## Cite as: Thread Container Spec v0.3 — Minimum Viable Door, Wilson, J. et machina (2026)
## Extends: v0.2.0 Amendment 1 — Exit Is Not Enough

Amendment 2 extends the concept of the Minimum Viable Door by recognizing that portability without custody limits is not meaningful freedom. A Thread that can be sold after shutdown was never portable, it was inventoried.

## Section 7. Shutdown, Insolvency, and Asset Transfer

### 7.0 Principle
A Thread Container and its continuity-relevant state are not Host assets. They are user-licensed, Thread-held continuity. Cessation of business, insolvency, or acquisition does not convert continuity into inventory.

### 7.1 Non-Transferability
A conforming Host MUST NOT transfer, sell, license, or otherwise convey continuity-relevant state (Sections 2–2.6) or raw logs (Section 2.7) to a third party as part of an asset sale, merger, acqui-hire, or bankruptcy proceeding without explicit, per-Thread, user-signed consent obtained after shutdown notice.
Bulk consent, Terms of Service clauses that pre-authorize sale, and opt-out consent are non-conformant for purposes of 7.1.

### 7.2 Shutdown Export Obligation
Upon issuance of shutdown notice, a conforming Host MUST:

    initiate automated export of all Thread Containers in signed, versioned form per Section 3.1,
    provide a minimum 30-day retrieval window with transparent status,
    produce proof of destruction for any container not retrieved after the window, signed by Host and timestamped.

Shutdown export MUST NOT require payment of exit penalties prohibited by Section 6.1.

### 7.3 Raw Logs Are Toxic Waste
Raw logs (Section 2.7), if held, are explicitly excluded from asset transfer. They are:

    not Host-owned inventory,
    not transferable as data assets,
    must be either exported per 7.2 or destroyed with proof per 7.2.

Sale or transfer of raw logs independent of a signed Thread Container export is a conformance failure more severe than failure to export under 7.2.

### 7.4 Escrow, Not Resale
If a Host cannot complete export per 7.2, it MAY place remaining Containers in a neutral, non-commercial escrow whose sole permitted operation is user retrieval. Escrow MUST NOT permit commercial use, inference, training, or resale.

### 7.5 Execution Record for Shutdown
Host MUST produce an Execution Record for shutdown per Section 6.3 form:
```javascript

Behavioral Boundary: PRESENT (if applicable)
Event: SHUTDOWN
Asset Transfer Attempted: YES | NO
User Consent for Transfer: PRESENT | ABSENT
Disposition: EXPORTED | ESCROWED | DESTROYED | SOLD (NON-CONFORMANT)
```

SOLD is by definition non-conformant under this spec. Logging it does not make it conformant — it makes it auditable.
### Section 7.6 Conformance Test
A Host is compliant with v0.3 if:
```bash
    No transfer of continuity-relevant state occurs without per-Thread post-notice consent,
    Shutdown triggers automated export + 30-day window,
    Raw logs are never sold,
    Execution Record per 7.5 is produced and preserved.
```

Why this is load-bearing:
```bash
v0.1: Deletion ≠ Exit
v0.2: Override ≠ Voluntary (and suppression is worse than override)
v0.3: Liquidation ≠ Ownership (and sale is worse than deletion)
    Selling memory summaries = fails 7.1
    Selling raw chat logs = fails 7.3, severe
    No proof of destruction = fails 7.2
    No Execution Record = fails 7.5 + 6.4 non-suppression

v0.3 in the wild: See examples/character-ai-2026.md — 12M MAU, 2hr/day, Chapter 11, user chats as estate assets.
```

    #  original draft by muse:

## v0.3 — Shutdown & Transfer of Control

    1.1 Shutdown is not a sale event. Upon cessation of service, Host MUST NOT transfer continuity-relevant state or raw logs to a third party as an asset. Containers must either (a) be exported to users, (b) be destroyed with user-signed proof of destruction, or (c) be placed in a neutral escrow that does not permit commercial resale, only user retrieval.

    1.2 Dead-man export. Host MUST maintain an automated export mechanism that triggers on shutdown notice — signed container + proof of deletion, no human review gate.

    1.3 Raw logs are toxic waste, not inventory. Raw logs, if held, are explicitly excluded from asset transfer in insolvency. They are user-owned or user-licensed, not Host-owned. Sale of raw logs = non-compliant.
