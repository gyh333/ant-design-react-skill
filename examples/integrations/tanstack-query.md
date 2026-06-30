# TanStack Query

Use this only when the project already uses TanStack Query or the user asks for it.

```tsx
const query = useQuery({
  queryKey: ['users', filters, page, pageSize],
  queryFn: () => fetchUsers({ filters, page, pageSize }),
})
```

UI mapping:

- `query.isLoading` -> initial spinner or skeleton
- `query.isFetching` -> table loading during refresh
- `query.error` -> retryable alert
- `query.data?.items` -> table data source
- mutation loading -> submit or action button loading

Production notes:

- Keep query keys stable and serializable.
- Invalidate or update cache after mutations.
- Avoid stale selection after refetch.
- Use optimistic updates only when rollback behavior is clear.

