# Template Status & Verification

**Classification:** Configurable n8n template asset — **known compatibility review required** before use.

The repository contains real workflow/template structure, but the September 2026 audit identified stale LinkedIn publishing assumptions. It must not be presented as a currently verified publisher.

## Known review items

- Historical workflow logic references the legacy LinkedIn `ugcPosts` publishing pattern and must be checked against the current LinkedIn API/product permissions before use.
- Any pseudo-wait/delay logic must be replaced with a real n8n Wait/scheduling mechanism if delayed execution is required.

## Verification gate
1. Parse/import into a clean current n8n instance.
2. Inspect all connections, expressions, publishing endpoints, scopes, and delay logic.
3. Replace placeholder LinkedIn credentials, organization/person IDs, webhooks, URLs, and resource IDs.
4. Confirm the currently supported LinkedIn posting endpoint and required permissions from official documentation.
5. Run against a controlled test account/environment if permitted.
6. Verify failure handling for auth expiry, rate limits, invalid media/content, and permission errors.
7. Record configured test date/result before calling the workflow working.

## Security
Never commit access tokens, OAuth secrets, private profile/organization IDs beyond what is safe to expose, or production content credentials.

## Change record
- **2026-09-03:** Added explicit compatibility warning and verification/security gate. No API repair or configured runtime pass is implied.
