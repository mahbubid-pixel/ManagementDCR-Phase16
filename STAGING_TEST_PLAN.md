# Safe integration test plan

1. Confirm staging host, test account, and written permission to perform requests.
2. Verify login contract without logging credentials or storing plaintext passwords.
3. Verify cascading scope lists and doctor/brand mappings using synthetic test data.
4. Verify dashboard counts and weekly period definitions against staging reference values.
5. Verify draft stays local; a DCR is marked submitted **only after server confirmation**.
6. Test duplicate submissions, timeouts, token expiry, offline/reconnection, and unauthorized FME/doctor selection.
7. Check TLS validation, backup exclusions, encrypted local storage, and logout data clearing.
8. Build APK, install on test Android device, and record test evidence.
