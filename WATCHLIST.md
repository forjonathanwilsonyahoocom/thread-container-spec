# Watchlist — Scenarios That Will Test TCS v0.3

This file tracks future failure modes for the Minimum Viable Door. Each entry is a scenario where v0.3 should produce a non-conformant verdict.

## Status
- v0.3.0 active (Amendment 2 — Liquidation Is Not Ownership)
- Case 26-11603 (Character.AI) is first real-world test

## 1. The Acqui-hire License (Google Pattern)
**Pattern:** Big lab pays $50-100M for "non-exclusive IP license + team" — founders return, platform "continues under new management."
**Why it matters:** Looks like runtime swap (v0.1 compliant), but continuity is transferred without per-Thread post-notice consent.
**TCS Test:** Fails 7.1 if user data / containers move as part of license deal. Pass requires explicit per-Thread consent after shutdown/acquisition notice.
**Watch:** Replika, Nomi, Kindroid, any 2023-vintage companion shop.

## 2. Training Data Laundry
**Pattern:** Buyer says "We didn't buy chats, we bought weights / finished models that were trained on chats."
**Why it matters:** Raw logs become laundered into model weights.
**TCS Test:** Fails 7.3 + new 7.3.1 — Weights derived directly from non-consented raw logs inherit non-transferability. Sale of such weights without proof of log destruction / consent is non-conformant.
**Note:** See 7.3.1 you just added. This is the reason for it.

## 3. Litigation Hold vs. Deletion
**Pattern:** AGs / courts order preservation of chat logs for user-harm litigation, conflicting with 7.2 destruction requirement.
**Why it matters:** Host cannot both destroy and preserve.
**TCS Test:** Proposed carveout — preservation under court seal is not a sale if: (a) no commercial use, inference, or training, (b) Execution Record shows `DISPOSITION: LITIGATION_HOLD`, (c) neutral escrow, not buyer asset.
**Reference:** Kentucky AG suit Oct 8 2026 (4 days pre-filing), 40-state coalition intervention Oct 2026.

## 4. Open Source Wind-Down
**Pattern:** "We can't afford servers, so we're open-sourcing everything — here's a Docker image with the DB."
**Why it matters:** Bulk transfer of other users' Threads disguised as generosity.
**TCS Test:** Fails 7.1 and 7.3. Compliant open source = code only. Compliant data = your signed container only, not the graph. No shared vector DB containing others' memories.
**Watch:** Any shutdown that posts to GitHub before completing 7.2.

## 5. The Escrow That Is Actually A Resale (New)
**Pattern:** Host places remaining containers in "escrow" that charges users $20/mo to retrieve, or that monetizes retrieval via ads / training.
**Why it matters:** Escrow becomes rent-to-terminate.
**TCS Test:** Fails 7.4 — escrow must be non-commercial, retrieval-only. Any fee beyond reasonable storage cost or any commercial use = non-conformant.

---
Add new case studies as `examples/[company]-YYYY.md` using template in `examples/character-ai-2026.md`.

Conformance command (future):
`tcs-compliance-check --host=<domain> --amendment=v0.3`
