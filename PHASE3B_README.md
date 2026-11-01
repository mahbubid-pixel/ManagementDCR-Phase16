# Phase 3B — Offline doctor-list discovery update

## Evidence
The original ManagementDCR22 Doctor dropdown populated quickly while online but showed no list or an error when Airplane Mode was enabled. This establishes network dependence in the tested sequence, not the endpoint, cache strategy, or whether requests occur on every tap.

## Source changes
- Added a manual device network-status indicator to the home screen (Android ConnectivityManager).
- Clearly distinguishes network availability from actual server connectivity; **no live API integration**.
- Existing offline draft persistence and preview UI are retained unchanged.
- Added ACCESS_NETWORK_STATE permission. No internet permission or production server access introduced.

## Proposed implementation after API validation
1. Fetch doctor master data from an authorized endpoint only after login and territory selection.
2. Display loading, empty, offline, and server-error states explicitly.
3. Use a protected, expiring on-device cache only if company policy allows storing doctor information.
4. Revalidate doctor and territory IDs before submission.
5. Save drafts separately from server-submitted records; prevent duplicate submission using a server-approved idempotency scheme.

## Remaining blockers
Exact endpoint paths, login protocol, response schemas, permissions, and server submission semantics are unknown. The APK source has not been compiled or tested on a device. Demo doctor entry remains manual, not a real dropdown. No doctor cache has been implemented because the permitted data fields and retention rules are unknown.

## Recommended next verification
With the app already open and doctor list loaded, toggle Airplane Mode without leaving the form, then reopen the list. Note whether an error is immediate or delayed; do not send credentials or doctor data.
