---
name: get-feature-usage
description: Skill for querying premium feature usage via GET /feature/usage.
---

# Get Feature Usage Skill

This skill explains how to query current premium feature usage for a specific entity and feature.

## API Endpoint

**Method:** GET
**URL:** `{{baseUrl}}/feature/usage`

## Query Parameters

- `entity`: The entity identifier, such as `channel#<id>` or `master`
- `feature`: The premium feature name, such as `live-event-control`

## Headers

- `Accept: application/vnd.api+json`
- Optional: `Authorization: Bearer <token>` if required by your deployment.

## Example Curl

```bash
curl -G \
  "${BASE_URL}/feature/usage" \
  -H "Accept: application/vnd.api+json" \
  --data-urlencode "entity=channel#445b9e70-8570-43a5-8b5c-44d478b033be" \
  --data-urlencode "feature=live-event-control"
```

## Notes

- The query can be used to validate whether a feature is currently running.
- Response returns a `featureUsage` object with `running` status and `message`.
