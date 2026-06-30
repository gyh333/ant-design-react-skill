# Popconfirm And Dropdown

Use `Popconfirm` for small inline confirmations. Use `Modal.confirm` when the action needs more context.

```tsx
import { Button, Dropdown, Popconfirm } from 'antd'
import type { MenuProps } from 'antd'

export const DeleteAction = ({ onDelete }: { onDelete: () => Promise<void> }) => (
  <Popconfirm
    title="Delete record"
    description="This action cannot be undone."
    okText="Delete"
    okButtonProps={{ danger: true }}
    onConfirm={onDelete}
  >
    <Button danger type="link">
      Delete
    </Button>
  </Popconfirm>
)

const items: MenuProps['items'] = [
  { key: 'enable', label: 'Enable' },
  { key: 'disable', label: 'Disable', danger: true },
]

export const MoreActions = ({ onClick }: { onClick: MenuProps['onClick'] }) => (
  <Dropdown menu={{ items, onClick }}>
    <Button>More</Button>
  </Dropdown>
)
```

Production notes:

- Confirm destructive or irreversible actions.
- Disable or hide actions based on permission and row state.
- Keep dropdown item labels explicit.
- Avoid placing critical hidden actions only in overflow menus when they are primary workflow actions.

