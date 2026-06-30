# Table

Keep table query state explicit and use a stable `rowKey`.

```tsx
import { Table } from 'antd'
import type { TableProps } from 'antd'

interface UserRow {
  id: string
  name: string
  email: string
  status: 'enabled' | 'disabled'
}

const columns: TableProps<UserRow>['columns'] = [
  { title: 'Name', dataIndex: 'name' },
  { title: 'Email', dataIndex: 'email' },
  { title: 'Status', dataIndex: 'status' },
]

export const UserTable = ({
  data,
  loading,
  total,
  page,
  pageSize,
  onPageChange,
}: {
  data: UserRow[]
  loading: boolean
  total: number
  page: number
  pageSize: number
  onPageChange: (page: number, pageSize: number) => void
}) => (
  <Table<UserRow>
    rowKey="id"
    columns={columns}
    dataSource={data}
    loading={loading}
    pagination={{
      current: page,
      pageSize,
      total,
      showSizeChanger: true,
      onChange: onPageChange,
    }}
  />
)
```

For production tables, add explicit filter state, sorter mapping, error/empty handling, permission-aware actions, and selection cleanup after batch operations.

