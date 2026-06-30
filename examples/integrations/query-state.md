# Query State

Prefer the project's established server-state tool. Do not introduce TanStack Query, SWR, Redux Toolkit Query, or Zustand unless the project already uses it or the user asks for it.

## Table Query Shape

```ts
interface TableQuery {
  keyword?: string
  status?: string
  page: number
  pageSize: number
  sortField?: string
  sortOrder?: 'ascend' | 'descend'
}
```

Map Ant Design table changes into the project's API query contract explicitly.

```ts
const handleTableChange: TableProps<Row>['onChange'] = (pagination, filters, sorter) => {
  // Convert Ant Design values to the backend query shape used by the project.
}
```

For shareable pages, sync query state with URL search params if the project already follows that pattern.

