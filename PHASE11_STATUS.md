# Phase 11 — safe integration boundary

## Added
- `CatalogRefreshCoordinator`: validates complete authenticated doctor/brand reads before replacing offline cache. Existing offline cache remains on fetch failure.
- `SyncCoordinator`: manual pending-queue processing with strict request ID and server record ID acknowledgement checks; no record is marked synced from an HTTP status alone.

## Critical limitations
- **No live ACI connection is enabled.** The original Retrofit HTTP verbs, login payload, authentication/session protocol, response schemas and server acknowledgement format are still unverified.
- Production account credentials must not be embedded, replayed, or used in build pipelines. Rotate the password previously shared in chat.
- Do not test production DCR writes without ACI IT-approved staging and an idempotency/duplicate prevention contract.
- Existing encrypted catalog cache is not account-scoped, so this code must not be used to sync real multi-user production data until isolation and logout wiping are implemented.
- Not compiled or device tested in this environment.

## Next engineering work
1. Recover original Retrofit interface annotations and DTOs using authorized static APK analysis or get ACI IT redacted contract.
2. Add verified read-only authenticated transport and per-account encrypted cache, with logout wipe.
3. Build and test a read-only APK; then validate DCR submission only against approved staging.
