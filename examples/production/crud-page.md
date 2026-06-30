# CRUD Page Pattern

A production CRUD page should keep query state, data state, selection state, and editor state explicit.

## Recommended Structure

- Filter form near the table.
- Table with stable `rowKey`, server-side pagination, loading, empty, and error states.
- Row actions with permission checks.
- Create/edit drawer or modal with typed form values.
- Delete confirmation with async loading or disabled repeated action.
- Batch actions that clear selection after success.

## State Model

```tsx
interface QueryState {
  keyword?: string
  status?: string
  page: number
  pageSize: number
}

interface PageState<T> {
  rows: T[]
  total: number
  loading: boolean
  error?: Error
}
```

Use the project's data fetching layer, such as TanStack Query, SWR, Redux Toolkit Query, Zustand plus a request client, or local hooks already present in the repository.

