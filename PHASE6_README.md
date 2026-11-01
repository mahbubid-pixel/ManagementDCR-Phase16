# ManagementDCR22 — Phase 6: build and integration safety checkpoint

## Scope delivered
- Carried forward Phase 5 blue/white Compose preview, DCR form, local drafts, history and dashboard. My Plan remains excluded.
- Added `SubmissionPolicy.kt`: explicit local-draft vs confirmed-server-submission states and an off-by-default staging gate.
- Added repeatable source-integrity verification (`tools/verify_phase6.py`) and an integration acceptance checklist.
- Audited build prerequisites: Gradle/Android SDK are **not available** in this environment; no APK was compiled or installed.

## Important limitations
- This is an Android Studio **source ZIP**, not an APK.
- No production login, doctor data or DCR submission is connected.
- API methods and response contracts remain unverified.
- Existing offline drafts are stored in unencrypted SharedPreferences: use **demo data only**.
- `SubmissionPolicy` is a safety scaffold, not a working network client.

## How to build (on a machine with Android Studio)
1. Open the project folder in Android Studio (JDK 17, Android SDK 35).
2. Allow Gradle 8.7.3 / Kotlin 2.0.21 plugin resolution and sync.
3. Run `:app:assembleDebug` and install on a test device.
4. Verify all acceptance cases in `PHASE6_ACCEPTANCE.md` before considering a release.
5. Do not enable live API calls until request methods, schemas, auth and staging approval are independently verified.

No Gradle wrapper is included in this source project; Android Studio can import it using its configured Gradle distribution.
