# Sanitization Rules

This package was written to be safe for GitHub handoff review.

## Removed Or Avoided

- API keys.
- Private access tokens.
- Passwords.
- OAuth client secrets.
- Supabase service-role keys.
- Raw private messages.
- Private customer lead data.
- Personal payment dispute details.
- Local absolute machine paths.
- Screenshots that may show private chats, emails, customers, or account data.

## Replaced With General Terms

| Sensitive Detail Type | Replacement |
| --- | --- |
| Personal/operator identity | Neutral operator wording. |
| Local machine paths | Relative source names or high-level descriptions. |
| PAT/API token values | "Private integration token" or "managed credential". |
| Raw chats/emails | Summarized asks and decisions only. |
| Customer conversation content | General issue categories. |
| Account IDs and workflow IDs | Omitted unless needed for private implementation docs. |

## Recommended Pre-Push Checks

Before pushing a wider repo to GitHub:

```bash
git status --short
rg -n "pit-|sk-|service_role|SUPABASE_SERVICE_ROLE|password|passwd|secret|token|Authorization: Bearer|client_secret|refresh_token" .
find . -name ".env" -o -name "*.pem" -o -name "*.key"
```

If the target repo will be public, also run a dedicated secret scanner such as `gitleaks` or GitHub secret scanning before pushing.

## Safe Publishing Boundary

This folder can be shared as a documentation starting point. The full operational repo should be treated as private unless a separate scrub pass is completed.
