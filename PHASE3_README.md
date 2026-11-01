# ManagementDCR22 Phase 3 — Offline persistence and integration readiness

## Implemented
- Kotlin/Jetpack Compose UI carried forward from Phase 2.
- Offline draft storage using private app SharedPreferences serialized as JSON. Drafts survive process restarts.
- Save confirmation only succeeds after the local storage commit; failure is reported.
- Offline DCR history and local dashboard counts reflect persisted drafts.
- My Plan excluded; Target Brand multi-selection retained.
- No server calls, login credential handling, or production submissions.

## Still required before a real backend integration
1. Authorized API documentation or staging endpoints, authentication method and test account handled on device.
2. Actual business/region/area/FME/doctor catalogs and doctor metadata.
3. Target brand and Work With master data, DCR payload schema, validation rules and idempotency behavior.
4. Dashboard weekly period definitions and actual planned-call counts.
5. Server-side DCR history and conflict resolution, token lifecycle, error handling, tests.

## Security and data limitations
- Offline drafts are stored in app-private preferences, **not encrypted at the application layer**; do not enter sensitive production data in this prototype.
- Uninstalling the app can remove local drafts. No sync or backup guarantee.
- The Android project has not been compiled or device tested in this environment.
- Android Studio with SDK 35 and JDK 17 is needed to build.
- Do not point this preview at the production server without API validation and permission.

## Build
Open the folder in Android Studio, sync Gradle and run the app configuration. No installable APK is included.
