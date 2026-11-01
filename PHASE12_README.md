# Phase 12 — Account isolation groundwork (NOT live integration)

## Implemented in source
- `AccountScopedVault`: separate AES-GCM Android Keystore key and encrypted SharedPreferences namespace per verified account ID.
- Account-bound additional authenticated data (AAD), so ciphertext cannot be moved between accounts/fields.
- Explicit `clearAccount()` wipes that account namespace and its key after the retention policy is checked.

## Still NOT implemented
- AccountScopedVault is not wired into the demo UI or authenticated session. Existing `EncryptedVault`, `OfflineCatalog`, `SyncOutbox` and demo drafts remain unchanged.
- No authenticated ACI read-only gateway, production login, doctor/brand refresh or DCR submission.
- No verified Retrofit HTTP verbs, login DTOs, session handling or response models.
- No migration of prior drafts, offline cache freshness policy, background retry or reliable transactional outbox.
- Not compiled or tested on Android. Existing demo APK should be retained.

## Safe next engineering steps
1. Obtain redacted ACI Retrofit interface and DTOs through authorized analysis or ACI IT.
2. Verify authentication and read-only catalog API contracts without recording credentials or tokens.
3. Wire account-scoped storage to verified identity; design logout retention and migration.
4. Add atomic draft/outbox persistence, deduplication and tests.
5. Enable DCR write/sync only after staging approval and server idempotency contract.

The production password previously shared in chat should be rotated.
