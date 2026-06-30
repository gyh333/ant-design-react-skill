# Permission Architecture

Use this reference for permission-aware Ant Design pages.

## Principles

- Backend authorization is authoritative.
- Frontend permissions improve UX but do not provide security.
- Keep permission checks centralized.
- Keep route, menu, button, and API permissions consistent.

## UI Patterns

- Disable actions when users should know the action exists but cannot currently use it.
- Hide actions when policy requires non-disclosure or the action is irrelevant.
- Explain disabled actions with tooltip or contextual copy when possible.
- Re-check permissions after status transitions and data refresh.

## Common Permission Surfaces

- route access
- menu visibility
- page-level action buttons
- table row actions
- batch actions
- field-level editability
- export/import access

## Review Checklist

- Does the page show actions the backend will reject?
- Are destructive actions protected by confirmation?
- Are batch actions validating mixed selected states?
- Are unauthorized empty states distinguishable from real empty data?

