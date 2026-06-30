# Advanced Forms

Use this reference for complex Ant Design forms.

## Patterns

- Split large forms into sections with stable field names.
- Use `Form.List` for arrays and keep persisted row IDs when editing.
- Use `dependencies` or `shouldUpdate` for conditional fields.
- Use async validators only when client-side validation cannot decide the result.
- Map server errors to fields with `form.setFields`.
- Keep submit payload mapping explicit; do not send raw UI-only values.

## Create/Edit Separation

- Create mode starts from defaults.
- Edit mode initializes from fetched data.
- Switching edited records must reset stale fields.
- Closing a modal/drawer should reset or preserve intentionally.

## Server Error Mapping

```ts
form.setFields([
  { name: ['items', 0, 'sku'], errors: ['SKU is unavailable'] },
])
```

## Common Mistakes

- Relying on placeholders instead of labels.
- Mixing controlled input state with `Form` state without reason.
- Forgetting `valuePropName="checked"` for switches and checkboxes.
- Sending dayjs objects directly to the backend.
- Hiding validation errors inside inactive tabs.

