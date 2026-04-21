---
name: start-feature-usage
description: Skill for starting premium feature usage via POST /feature/usage/start.
---

# Start Feature Usage Skill

This skill explains how to start usage for a premium feature in the Premium Feature Management service.

## API Endpoint

**Method:** POST
**URL:** `{{baseUrl}}/feature/usage/start`

## Request Body

```json
{
  "data": {
    "type": "featureUsage",
    "attributes": {
      "entity": "channel#<entity-id>",
      "feature": "<feature-name>"
    }
  }
}
```

## Headers

- `Content-Type: application/vnd.api+json`
- `Accept: application/vnd.api+json`
- Optional: `Authorization: Bearer <token>` if your deployment requires an auth token.

## Example Curl

```bash
curl -X POST \
  "${BASE_URL}/feature/usage/start" \
  -H "Content-Type: application/vnd.api+json" \
  -H "Accept: application/vnd.api+json" \
  -d '{
    "data": {
      "type": "featureUsage",
      "attributes": {
        "entity": "channel#445b9e70-8570-43a5-8b5c-44d478b033be",
        "feature": "live-event-control"
      }
    }
  }'
```

## Notes

- `entity` is typically a channel or tenant identifier.
- `feature` is the premium feature key.
- A successful request returns a `featureUsage` resource with a running status.
