# ManagementDCR22 — Phase 2

## Delivered
- Kotlin / Jetpack Compose Android Studio source project.
- Blue-and-white home screen with Dashboard, New Doctor Call Report, DCR History; **My Plan removed**.
- DCR form fields observed in user screenshots: Business, Region, Area, FME, Doctor, Priority, Last Call, Visit Date, Visit Time, Target Brand, Work With, Other, Doctor Comment, Your Observation.
- Cascading demo selectors; searchable multi-select Target Brand dialog with checked-state preservation and DONE confirmation.
- Basic input validation, review confirmation, in-memory draft saving, and local history.
- Dashboard totals and weekly local counts; no fabricated plan percentages.

## Important limitations
- **No production authentication, API calls, server submission, or persistent database.** Entries disappear when the app process restarts.
- Business/Region/Area/FME/Work With lists are explicitly DEMO data, not extracted production options.
- Nine brand names were transcribed from the provided screenshot; the complete catalog requires authorized backend mapping.
- Doctor, Priority, Last Call and weekly grouping semantics require further original-app/backend verification.
- Date/time use validated text inputs rather than native pickers in this phase.
- This source has not been compiled or device-tested in the provided environment. It is **not** an installable APK.

## Build
1. Open `ManagementDCR_Rebuild` in Android Studio with Android SDK 35 and JDK 17.
2. Allow Gradle sync and install the SDK/build dependencies.
3. Run the `app` configuration on an Android emulator or device (Android 8.0+).
4. Replace the mock catalogs with authorized endpoints and add authenticated persistence only after testing the API contract.

## Suggested Phase 3
- Authorized API contract discovery, secure token/session management, actual server-driven selector catalogs and doctor metadata, production DCR submission and history, real dashboard plans and period definitions, offline drafts and integration tests.
