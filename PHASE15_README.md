# Phase 15 — Manual read-only ACI API probe

## Implemented
- Explicit manual login POST to `https://workplan.acibd.com/authenticate/login?access_point=...` with verified form field names `empcode`, `password`.
- If login returns top-level `access_token` and `token_type`, constructs an in-memory Authorization header and permits explicit GET `dcr-list`.
- No `dcr-add` request, automatic sync, token persistence, credential logging, or raw history display.
- HTTPS only, fixed host, no redirects, timeouts, capped response, HTTP status validation.

## Unverified / limits
- **`access_point` value has NOT been recovered**. User must obtain the correct value from ACI IT; do not guess.
- Login response nesting and token formatting have NOT been verified; this implementation fails closed if the top-level fields are absent.
- GET history confirms only an HTTP success and JSON-shaped response, not a specific DCR or record count.
- Existing offline draft store remains separate from authenticated session; no production writes enabled.
- No Gradle/Android SDK in this environment; source has NOT been compiled or installed. Build using your existing Android/GitHub workflow.
- Existing demo APK is not replaced. Rotate previously disclosed production password before use.
