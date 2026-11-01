# Phase 16 — Android build workflow for read-only diagnostics

## What changed
- Added GitHub Actions workflow `.github/workflows/build-debug-apk.yml` to compile an installable debug APK in GitHub cloud, without requiring a PC or Android SDK on the user's phone.
- Uses Gradle 8.9, Android SDK 35, JDK 17; upload `app-debug.apk` as a workflow artifact.
- Retains the Phase 15 read-only ACI client. No production DCR submission path is enabled.

## Android-only build
1. Create a private GitHub repository and upload the **contents** of this ZIP at repository root (not the ZIP itself).
2. Open Actions > Build safe read-only diagnostic APK > Run workflow.
3. Download `ManagementDCR-Phase16-readonly-debug` artifact and extract/install the APK on Android.
4. Do not upload credentials to GitHub or store them in repository files.

## Not yet verified
- This runtime has no Android SDK/Gradle; workflow has not been executed and compilation has not been verified.
- `access_point` query value and token response structure remain unverified; a valid ACI login is not guaranteed.
- No live ACI production requests or submissions were performed.
- Never reuse the password disclosed in chat; rotate it first.
