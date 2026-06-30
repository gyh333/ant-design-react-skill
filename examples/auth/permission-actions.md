# Permission Actions

Follow the project's permission system. Do not invent a new one unless the user asks.

```tsx
import { Button, Space } from 'antd'

interface UserRow {
  id: string
  status: 'enabled' | 'disabled'
}

export const UserActions = ({
  row,
  canEdit,
  canDisable,
  onEdit,
  onDisable,
}: {
  row: UserRow
  canEdit: boolean
  canDisable: boolean
  onEdit: (row: UserRow) => void
  onDisable: (row: UserRow) => void
}) => (
  <Space>
    <Button type="link" disabled={!canEdit} onClick={() => onEdit(row)}>
      Edit
    </Button>
    <Button
      type="link"
      danger
      disabled={!canDisable || row.status === 'disabled'}
      onClick={() => onDisable(row)}
    >
      Disable
    </Button>
  </Space>
)
```

Production notes:

- Hide actions only when product policy requires it; disabled actions with explanations can be better for discoverability.
- Keep backend authorization authoritative.
- Keep destructive actions confirmed.

