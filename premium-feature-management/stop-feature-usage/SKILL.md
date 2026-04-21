---
name: stop-feature-usage
description: Skill for stopping premium feature usage via POST /feature/usage/stop.
---

# Stop Feature Usage Skill

This skill documents how to stop usage for a premium feature in the Premium Feature Management service.

## API Endpoint

**Method:** POST
**URL:** `{{baseUrl}}/feature/usage/stop`

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
- Optional: `Authorization: Bearer <token>` if required by your environment.

## Example Curl

```bash
curl -X POST \
  "${BASE_URL}/feature/usage/stop" \
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

- Use the same `entity` and `feature` values as the corresponding start request.
- A successful stop request returns a `featureUsage` response with the usage state.
