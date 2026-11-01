# API contract verification worksheet (all unverified)

The route strings below were recovered in earlier static inspection. A route string alone does not verify method, headers, payload or current availability.

| Feature | Route string | Method | Auth | Request/response |
|---|---|---|---|---|
| Login | authenticate/login | UNKNOWN | UNKNOWN | UNKNOWN |
| Doctor catalog | doctor-info/{level} | UNKNOWN | UNKNOWN | UNKNOWN |
| Doctor priority | doctor-priority-info/{level1}/{doctorId} | UNKNOWN | UNKNOWN | UNKNOWN |
| Area | area-info/{level3} | UNKNOWN | UNKNOWN | UNKNOWN |
| Territory | territory-info/{level2}/{SBID} | UNKNOWN | UNKNOWN | UNKNOWN |
| Target brands | region-brand-info/{SBId} | UNKNOWN | UNKNOWN | UNKNOWN |
| DCR history | dcr-list | UNKNOWN | UNKNOWN | UNKNOWN |
| DCR detail | dcr-details/{dcrID} | UNKNOWN | UNKNOWN | UNKNOWN |
| DCR submission | dcr-add | UNKNOWN | UNKNOWN | UNKNOWN |
| Dashboard | my-dcr-dashboard | UNKNOWN | UNKNOWN | UNKNOWN |
| General | general-info | UNKNOWN | UNKNOWN | UNKNOWN |
| Gifts | get-user-gift-list | UNKNOWN | UNKNOWN | UNKNOWN |

## Evidence needed
Authorized staging request/response samples with all passwords, tokens, identifiers, and personal data redacted. Document status codes, paging, auth expiry, and access control. Do not probe or submit against production without explicit approval.
