# Premium Feature Management Workflow

This folder contains skill documentation for managing premium feature usage and authentication.

## Available Skills

- `login` — Authenticate to Premium Feature Management and obtain a token.
- `start-feature-usage` — Start usage for a premium feature.
- `stop-feature-usage` — Stop premium feature usage.
- `get-feature-usage` — Query active usage for a feature and entity.

## Recommended Sequence

1. Run the `login` skill to obtain credentials or token.
2. Use `start-feature-usage` when a premium feature begins running.
3. Use `get-feature-usage` to verify feature status.
4. Use `stop-feature-usage` when the feature should end.

## Base URL

The Postman collection defines `{{baseUrl}}` as:

```text
https://{{region}}.{{environment}}.evertz.io/{{service}}
```

Use your environment values for `region`, `environment`, and `service`.
