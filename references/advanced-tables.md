# Advanced Tables

Use this reference for heavy or shared Ant Design tables.

## State

Keep these states explicit:

- filters
- sorter
- page
- page size
- total
- loading
- error
- selected row keys
- expanded rows
- column visibility, when user-configurable

## Query Mapping

Map Ant Design table parameters to backend API names in a helper function.

```ts
interface ApiQuery {
  pageNo: number
  pageSize: number
  orderBy?: string
  orderDirection?: 'asc' | 'desc'
}
```

## Selection

- Use `preserveSelectedRowKeys` only when cross-page selection is a product requirement.
- Clear selection after successful batch operations.
- Remove selected keys that no longer exist after refresh when appropriate.
- Validate selected row states before submitting batch actions.

## Performance

- Memoize columns for complex render functions.
- Avoid anonymous heavy renderers in large tables.
- Use virtualization only after verifying fixed columns, expandable rows, row height, and scroll behavior.
- Consider server aggregation instead of computing expensive summaries in the browser.

