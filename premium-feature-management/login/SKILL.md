---
name: login
description: Skill for authenticating to the Premium Feature Management service using the signin endpoint.
---

# Premium Feature Management Login Skill

This skill documents how to sign in to Premium Feature Management and obtain a Bearer auth token, using the same login method as data-translation.

## API Endpoint

**Method:** POST
**URL:** `https://us-east-1.{{stage}}.api.evertz.io/authenticate/signin?tenant={{tenant}}`

**Environment → Tenant mapping:**
| Environment (`ENV`) | Tenant |
|---|---|
| `dev` | `evertz-tv` |
| `test` | `evertz-qa` |

## Authentication

- Uses HTTP Basic auth with `username` and `password`
- Default credentials: username = `bbhaskar`, password = `Hello@123`
- The endpoint returns an `IdToken` on successful authentication.
- Extract the `IdToken` and use it as `AUTH_KEY` for subsequent requests.
- Token expires in 1 hour.

## Headers

- `Content-Type: application/json`

## Example Curl

```bash
ENV=${ENV:-test}
TENANT=$([ "$ENV" = "dev" ] && echo "evertz-tv" || echo "evertz-qa")

curl -s -X POST \
  "https://us-east-1.${ENV}.api.evertz.io/authenticate/signin?tenant=${TENANT}" \
  -u "${USERNAME:-bbhaskar}:${PASSWORD:-Hello@123}" \
  -H "Content-Type: application/json"
```

## Usage

1. Set `ENV` to your environment (`dev` or `test`). Defaults to `test`.
2. Run the curl command — tenant is derived automatically from `ENV`.
3. Extract `IdToken` from the response.
4. Set `AUTH_KEY` to the token value.
5. Use `Authorization: Bearer $AUTH_KEY` for Premium Feature Management requests.

## Notes

- This matches the data-translation and stream-record login flow: authenticate via `/authenticate/signin?tenant=...`, then use the returned `IdToken` as a Bearer token.
- `evertz-tv` is used for `dev`, `evertz-qa` for `test`.
