# ManagementDCR22 — Phase 9 offline-first implementation

## Included in source
- Android Keystore AES-256-GCM encryption for new local DCR drafts, doctor/brand catalogs and upload queue.
- Offline doctor and brand selectors read from a verified encrypted catalog when available.
- Stable UUID for each queued DCR and an outbox status screen.
- Only an explicit matching server acknowledgement can change queue status to SYNCED.
- No live API calls, credential handling, or production submission.
- My Plan excluded. Original blue-and-white Compose UI preserved.

## Important limitations
- **No real doctor or brand catalogs are bundled**. The current fallback is demonstration data; verified authenticated catalog downloads are still needed.
- Sync Now is deliberately disabled. Automatic retry, idempotency negotiation, token refresh, endpoint schemas and error handling are not implemented until an authorized staging API contract is verified.
- Existing Phase 8 plaintext SharedPreferences drafts are **not automatically migrated**. Do not uninstall the previous app until existing demo drafts are no longer needed. Production data should not be used in the demo.
- A successful local draft save followed by a failed queue write could produce an unsynchronized local draft. A transactional Room database is recommended before production rollout.
- This source has **not been compiled or installed** here. Compile using Android SDK/Gradle and run tests on a device.

## Next development gates
1. Extract/verify actual API method signatures and authenticated responses from authorized staging.
2. Build encrypted Room transactional draft/outbox storage and migration.
3. Populate verified doctor and brand catalogs, filtered by server IDs and access controls.
4. Implement WorkManager sync with authenticated requests, retry/backoff, duplicate protection, server acknowledgements and logout data isolation.
5. Validate offline/online transitions, expired credentials, duplicate retries, data-loss scenarios and server rejections.
