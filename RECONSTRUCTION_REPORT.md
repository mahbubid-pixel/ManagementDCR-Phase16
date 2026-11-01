# ManagementDCR22 APK reconstruction — phase 1

## Evidence
Source: uploaded APK; inspected ZIP entries and compiled DEX class/type identifiers. This is static analysis, not a runtime UI capture or complete decompilation.

- APK ~7.3 MB; 3 DEX files; native `libconceal.so` across 5 architectures.
- Package namespace in DEX: `com.aci.managementdcr`.
- Confirmed UI classes: `ui/login/LoginActivity`, `ui/dashboard/DashboardActivity`, `ui/dcr/DcrListActivity`, `ui/dcr/DcrPlaceActivity`, `ui/dcr/MyDcrPlanActivity`.
- Confirmed dialog classes: `AddGiftDialog`, `AddPpmDialog`, `AddSampleDialog`, `DcrCommentDialog`.
- Confirmed binding/layout names: `ActivityLogin`, `ActivityDashboard`, `ActivityDcrList`, `ActivityDcrPlace`, `ActivityMyDcrPlan`, `RowDoctor`, `RowRxEntry`, `RowDcr`, `RowDcrPlan`, `RowBrands`.
- Data classes include `DoctorData`, `DoctorPriority`, `TerritoryData`, `AreaData`, `DcrData`, `DcrMaster`, `PlanData`, `RxSeenData`, `Gift`, `Sample`, `Ppm`, `UserResource`, `Token`.
- DCR viewmodel methods indicated by compiled names include `dcrAdd`, `dcrDetails`, `dcrPlan`, `doctorInfo`, `doctorPriorityInfo`, `territoryInfo`, `areaInfo`, `regionBrandInfo`, `userGiftList`, `specialAccessibleDates`.
- Embedded URL string: `https://workplan.acibd.com/`. No live endpoint or access has been tested.

## Proposed screen architecture
1. Login / session handling (requires authorized API integration).
2. Dashboard with actual server-provided KPIs.
3. DCR list and record detail, search/filter.
4. New/edit DCR with doctor, territory, visit metadata, Rx, gifts, samples, PPM, brand and comments.
5. DCR plan/calendar.
6. Doctor and territory lookup.
7. Resources and reporting.

## Current implementation
An independent Kotlin + Jetpack Compose Android Studio scaffold using a modern corporate blue/white design. It has local-preview navigation and a draft DCR form. **It is not a fully reconstructed app**: no real login, network operations, persistence, DCR submission, or exact workflow parity yet. The local preview accepts any nonblank user ID and password without verifying them; do not enter production credentials.

## Next steps
1. With permission, perform full manifest/resource decoding and controlled runtime testing against a test environment.
2. Extract exact screen fields, validations, navigation transitions and DTO/API contracts.
3. Implement secure login, repository interfaces, role-specific navigation, and authenticated API adapters.
4. Implement offline draft persistence, synchronization rules, server-side validation and error states.
5. Test screen parity, functional parity, accessibility, security and deployment signing.

## Build
Open folder in Android Studio with Android SDK 35 and JDK 17; Gradle sync then Run. Build has **not** been executed in this environment (Android SDK and Gradle unavailable).

## Legal/security boundary
Only integrate the company's production systems with appropriate authorization and test credentials. Do not reuse extracted signing keys, bypass access controls, or copy protected proprietary assets without permission.
