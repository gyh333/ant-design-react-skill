# Descriptions

Use `Descriptions` for read-only detail views.

```tsx
import { Descriptions, Tag } from 'antd'

interface UserDetail {
  name: string
  email: string
  status: 'enabled' | 'disabled'
  updatedAt: string
}

export const UserDescriptions = ({ user }: { user: UserDetail }) => (
  <Descriptions bordered column={2}>
    <Descriptions.Item label="Name">{user.name}</Descriptions.Item>
    <Descriptions.Item label="Email">{user.email}</Descriptions.Item>
    <Descriptions.Item label="Status">
      <Tag color={user.status === 'enabled' ? 'green' : 'default'}>{user.status}</Tag>
    </Descriptions.Item>
    <Descriptions.Item label="Updated at">{user.updatedAt}</Descriptions.Item>
  </Descriptions>
)
```

Production notes:

- Use skeleton/loading states before data arrives.
- Keep labels consistent with table columns and forms.
- Use status tags with text, not color alone.
- For long values, handle copy, wrapping, and empty placeholders intentionally.

