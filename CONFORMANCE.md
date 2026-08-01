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

