# ManagementDCR22 — Phase 4 static API inventory and implementation boundary

## Source and provenance
Original APK: `ManagementDCR22_69d38d695aa201775471977.apk`  
SHA-256: `f86d5d06f807a8c0d1c8af2df2c9ed26898748209a4b64ebf0759f5da7144d67`  
Inspection: literal DEX string matching only; no backend calls, no credential use, no decryption.

## Verified route strings
- `authenticate/login`
- `doctor-info/{level}`
- `doctor-priority-info/{level1}/{doctorId}`
- `area-info/{level3}`
- `territory-info/{level2}/{SBID}`
- `region-brand-info/{SBId}`
- `dcr-list`
- `dcr-details/{dcrID}`
- `dcr-add`
- `my-dcr-dashboard`
- `general-info`
- `get-user-gift-list`

## What is NOT established
- HTTP verbs (GET/POST etc.), base path prefixes, request body schema, authentication token format, server response JSON, paging, error semantics, and doctor filtering rules.
- The mere presence of a route string does not prove that endpoint is currently active.
- Network traces confirm HTTPS host traffic, not individual API operations.

## Implementation delivered
- `app/src/main/java/com/example/managementdcr/api/ApiInventory.kt`: verified route constants and typed gateway boundary with an explicit unconfigured implementation.
- Phase 3C Compose prototype carried forward. No live API calls or real credentials.
- Corrected draft validation so an already-entered doctor can be saved as a local draft offline. It is never submitted.

## Important cautions
- The existing SharedPreferences draft store is not application-layer encrypted. Do not use real patient, doctor, or confidential production data in this prototype.
- Demo doctor entry and brand names are not verified backend records.
- Android Studio compilation and device tests have not been run.

## Next engineering gates
1. Recover Retrofit interface annotations or obtain redacted authorized staging requests to establish HTTP verbs and parameters.
2. Verify JSON contracts, errors, role scope, token handling, and refresh behavior.
3. Add secure credential storage and encrypted database with retention policy, then replace demo catalogs.
4. Test against staging, then compile signed debug/release APK with CI and device testing.
