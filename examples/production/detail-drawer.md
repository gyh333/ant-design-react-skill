# Detail Drawer

Use detail drawers to inspect records without losing table context.

```tsx
import { Descriptions, Drawer, Skeleton, Tag } from 'antd'

interface Detail {
  id: string
  name: string
  status: string
  updatedAt: string
}

export const DetailDrawer = ({
  open,
  loading,
  detail,
  onClose,
}: {
  open: boolean
  loading: boolean
  detail?: Detail
  onClose: () => void
}) => (
  <Drawer title="Detail" open={open} onClose={onClose} width={720}>
    {loading || !detail ? (
      <Skeleton active />
    ) : (
      <Descriptions bordered column={2}>
        <Descriptions.Item label="ID">{detail.id}</Descriptions.Item>
        <Descriptions.Item label="Name">{detail.name}</Descriptions.Item>
        <Descriptions.Item label="Status">
          <Tag>{detail.status}</Tag>
        </Descriptions.Item>
        <Descriptions.Item label="Updated at">{detail.updatedAt}</Descriptions.Item>
      </Descriptions>
    )}
  </Drawer>
)
```

Production notes:

- Fetch detail lazily when opened unless list data is already complete.
- Keep detail refresh independent from table refresh when needed.
- Include audit logs or operation history for regulated workflows.

