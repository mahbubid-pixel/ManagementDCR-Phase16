# Phase 3C — Same-form offline Doctor dropdown finding

## Verified observation
After a Doctor list appeared online, the user stayed on the **same** DCR form, switched to Airplane Mode, and reopened the dropdown. The list disappeared or produced an error. This is strong evidence that the dropdown operation is network-dependent, even without screen recreation. It does **not** prove the app makes an HTTP request on each tap: a connectivity guard, expired in-memory state, or another network-dependent check could also explain the result.

## Source changes
- DCR doctor section now displays online/offline status and provides an explicit **Recheck connectivity** action.
- Offline doctor demo entry is disabled and cleared when connectivity is rechecked as unavailable.
- Local draft validation prevents saving a new entry while the screen is known to be offline.
- No invented API endpoints, credentials, doctor data, or background traffic.

## Limitations
- Network availability is not server reachability.
- This project has not been compiled or device-tested.
- The manual demo doctor input is not a production doctor selector.
- Existing local draft storage uses unencrypted SharedPreferences; never use sensitive business or doctor data in this preview.
- A secure production cache should only be implemented after ACI data-retention rules and API schemas are established.

## Next practical step
Use the original APK's decompiled Retrofit ApiService declarations, with authorization, to extract exact paths and models offline. If phone-only, use an APK inspector/decompiler app locally; share only method signatures with secrets removed. Do not capture credentials or bypass TLS protections.
