# Request And Error Handling

Follow the project's existing request layer. This reference describes how Ant Design UI should connect to it.

## Request States

Each user-facing request should define:

- loading
- success
- validation error
- permission error
- network/server error
- cancellation or stale response behavior, when relevant

## UI Mapping

| Error Type | UI Response |
|---|---|
| Field validation | `form.setFields` |
| Global validation | `Alert` near the form submit area |
| Permission denied | disabled/hidden action plus backend error handling |
| Not found | `Result` or contextual empty state |
| Network/server error | retryable `Alert` or message |
| Partial failure | result summary and failed item list/export |

## Rules

- Do not swallow errors after showing a message if caller state also needs to update.
- Avoid stacked messages during polling or repeated retries.
- Keep destructive action failures visible near the action context.
- Prefer typed API response mapping helpers over ad hoc property access.

