# Phase 6 acceptance checklist

## Build and security
- [ ] Android Studio sync succeeds with SDK 35 and JDK 17
- [ ] Debug APK compiles and launches on a test device
- [ ] Android backup is disabled and cleartext HTTP is disallowed
- [ ] No production credentials, tokens, or personal data are embedded
- [ ] Local draft storage replaced with approved encryption before real data

## UI and local workflows
- [ ] Home shows Dashboard, New DCR, History; no My Plan
- [ ] DCR dropdowns preserve selections and validate required fields
- [ ] Brand multi-select search, select, deselect and Done work
- [ ] Draft save survives process termination and app restart
- [ ] Draft is clearly labeled local and never shown as server-submitted
- [ ] Network loss does not produce a false success confirmation

## Staging integration (not yet implemented)
- [ ] HTTP methods and schemas recovered and independently verified
- [ ] Auth tokens stored securely and cleared at sign-out
- [ ] Doctor/FME authorization verified by backend
- [ ] Staging DCR submission tested with server-confirmed ID
- [ ] Duplicate submission and retry semantics tested
- [ ] Dashboard values reconciled against staging responses
