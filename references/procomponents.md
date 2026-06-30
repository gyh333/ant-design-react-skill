# ProComponents And Ant Design Pro

Use this reference only when the target project already depends on Ant Design Pro, Umi, or `@ant-design/pro-components`, or when the user explicitly asks for it.

## Decision Rule

- If the project uses plain `antd`, do not introduce ProComponents by default.
- If the project already uses `ProTable`, `ProForm`, `PageContainer`, or Umi conventions, follow those abstractions instead of replacing them with raw `antd` components.
- Verify installed versions because ProComponents APIs vary across releases.

## Common Patterns

| Need | Likely Component |
|---|---|
| Search table | `ProTable` |
| Query form | `ProForm`, `ProFormText`, `ProFormSelect`, `ProFormDateRangePicker` |
| Page shell | `PageContainer` |
| Detail fields | `ProDescriptions` |
| Layout | Ant Design Pro layout or local layout wrapper |

## Production Notes

- Keep `request` functions typed and map API shape explicitly.
- Avoid hiding business rules inside column definitions when they belong in domain helpers.
- Keep action columns permission-aware.
- Check how the project handles route permissions, access control, and menu generation.
- Run the project's build/typecheck because ProComponents generic errors can be subtle.

