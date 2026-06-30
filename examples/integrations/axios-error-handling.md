# Axios Error Handling

Use this only when the project uses Axios or an Axios-like request client.

Recommended mapping:

- 400 validation error: map fields or show form-level `Alert`.
- 401 unauthenticated: use existing auth flow.
- 403 unauthorized: disable/hide action and show permission feedback.
- 404 not found: contextual empty/result state.
- 409 conflict: show domain-specific conflict message.
- 500 server error: retryable error state.

```ts
interface ApiFieldError {
  field: string
  message: string
}

const mapFieldErrors = (errors: ApiFieldError[]) =>
  errors.map((error) => ({ name: error.field.split('.'), errors: [error.message] }))
```

Do not create a new Axios instance if the project already has one.

