# Search Table

Use explicit query state and map Ant Design table changes to the backend contract.

```tsx
interface Query {
  keyword?: string
  status?: string
  page: number
  pageSize: number
  sortField?: string
  sortOrder?: 'ascend' | 'descend'
}
```

Recommended behavior:

- Submit filters resets `page` to `1`.
- Page and page size changes preserve filters.
- Sort changes map to backend field names explicitly.
- Reset clears filters, sorter, selected rows, and returns to page `1`.
- Batch operations clear selection after success.

For complex pages, split into:

- `useXxxQueryState`
- `XxxFilterForm`
- `XxxTable`
- `XxxEditorDrawer`
- API mapping helpers

