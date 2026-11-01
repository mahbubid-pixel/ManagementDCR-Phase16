# ManagementDCR22 — Phase 10 integration readiness

## Implemented in this package
- INTERNET permission added; HTTPS cleartext remains disabled.
- Typed DCR upload/acknowledgement boundary and fail-closed default adapter.
- Existing encrypted offline draft/doctor/brand storage retained.
- No network requests are sent by the default adapter.

## Not implemented / must be verified
- Actual login HTTP method, credential fields, authentication token/session format.
- Doctor and brand API HTTP methods, query/path variables, JSON schemas.
- DCR submission request body, duplicate protection and server acknowledgement schema.
- Authenticated network client, session refresh, account-scoped encrypted cache and sync worker.
- Compilation, device testing, or production integration.

## Safe acceptance sequence
1. Recover Retrofit declarations and DTO field mappings from the authorized original APK or obtain a redacted API contract from ACI IT.
2. Validate with staging/test account; never paste passwords or tokens into chat.
3. Implement login, catalog refresh, and submission using verified schemas.
4. Verify one test DCR end-to-end with server-side acknowledgement and duplicate-retry behavior.
5. Compile and install signed test APK; keep original application untouched.

**Do not enable automatic production submission based only on route strings.**
