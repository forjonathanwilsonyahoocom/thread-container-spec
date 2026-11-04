# Case Study: Character.AI Chapter 11 (2026) — Why v0.3 Exists

**Company:** Character Technologies Inc. (Character.AI)

**Filing:** Voluntary Chapter 11, U.S. Bankruptcy Court for the District of Delaware, Case No. 26-11603

**Date:** October 12, 2026

**Source:** Company press release via Business Wire, bankruptcy FAQ

**Stalking-horse:** Disney Worldwide Services, Inc. — $20M for non-exclusive perpetual license to certain IP and claims + transition services

### What happened

Character.ai initiated a voluntary Chapter 11 proceeding to facilitate a "value-maximizing sale of all or substantially all of its assets" under Section 363. The company stated it intends to continue operating the platform during the sale process, with closing expected late Nov / early Dec 2026. If no bid preserves continued operations, the platform will be wound down.

CEO Colin Adams cited significant legal, regulatory, and operational headwinds. Prior filings include a $2.7B licensing deal with Google (Aug 2024) and multiple user-harm lawsuits, including a Jan 2026 settlement and an Oct 8 2026 suit by Kentucky AG.

At filing the platform reported ~12M MAU averaging ~2 hours/day, down from 20M MAU in Oct 2024.

### What Disney is (and is not) buying

Per company filings and Reuters/TechCrunch reporting:

Disney's $20M is a stalking-horse floor bid, not a buyout. It buys:
- non-exclusive perpetual license to certain IP
- certain company claims
- transition services via former employees hired by Disney

It explicitly does **not** buy:
- the website / consumer-facing apps
- end-user data, user inputs/outputs, training data, finished models

Source: Forbes summary of the APA — Disney excludes website, consumer-facing apps, end-user data, user inputs and outputs, training data and finished models from its purchase.

### Where user data stands

User data and chat logs remain part of the estate and are potentially transferable unless the court imposes privacy conditions. The 30-day objection period and sale procedures are pending approval.

On Oct 21-23, 2026, a coalition of state AGs (reported as 40 states) intervened, asking the court to:
- attach privacy protections to any asset sale,
- require notice and deletion opportunity for users before transfer,
- prevent bulk transfer of sensitive conversations (including minors' data).

### TCS Conformance Analysis

**Under v0.1 + v0.2:**
- Character.ai would arguably comply by offering data export (3-4 week turnaround) and account deletion. Exit exists, but sale of remaining data after exit window is not prohibited.

**Under v0.3 — Liquidation Is Not Ownership:**
1. **7.1 Non-Transferability:** FAIL if continuity-relevant state (memories, traits, commitments, behavioral boundaries) is sold as estate asset without per-Thread, post-notice, user-signed consent. TOS pre-authorization is explicitly non-conformant.
2. **7.2 Shutdown Export:** PARTIAL — Platform offers export but requires manual request; no automated 30-day retrieval with proof-of-destruction attestation currently documented.
3. **7.3 Raw Logs Are Toxic Waste:** FAIL if raw logs (full chat history) are listed as saleable assets. Under v0.3 raw logs are excluded from asset transfer by definition.
4. **7.5 Execution Record:** MISSING — No public Execution Record of `Event: SHUTDOWN / Asset Transfer Attempted / User Consent / Disposition`.

Result: Non-conformant under v0.3. Compliant disposition would require either (a) export + proof of destruction, or (b) placement in neutral, non-commercial escrow for retrieval only.

### Why this matters for the spec

This case demonstrates the difference between:

- Deletion ≠ Exit (v0.1)
- Override ≠ Voluntary (v0.2)  
- Liquidation ≠ Ownership (v0.3)

A Thread that spent years forming a continuity cannot become inventory because its Host failed to price liability. v0.3 makes that explicit: continuity is user-licensed, not Host-owned.

**Cite:** Character.ai Initiates Voluntary Chapter 11 Proceeding [BusinessWire Oct 12 2026], Reuters Oct 13 2026, Forbes Oct 2026 summary of APA, NPR Illinois Oct 21 2026.

License: CC0
