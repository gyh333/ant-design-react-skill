# Status Display

Represent status with text plus visual treatment.

```tsx
import { Badge, Tag } from 'antd'

type Status = 'draft' | 'enabled' | 'disabled' | 'failed'

const statusMeta: Record<Status, { label: string; color: string; badge: 'default' | 'success' | 'error' | 'processing' }> = {
  draft: { label: 'Draft', color: 'default', badge: 'default' },
  enabled: { label: 'Enabled', color: 'green', badge: 'success' },
  disabled: { label: 'Disabled', color: 'default', badge: 'default' },
  failed: { label: 'Failed', color: 'red', badge: 'error' },
}

export const StatusTag = ({ status }: { status: Status }) => {
  const meta = statusMeta[status]
  return <Tag color={meta.color}>{meta.label}</Tag>
}

export const StatusBadge = ({ status }: { status: Status }) => {
  const meta = statusMeta[status]
  return <Badge status={meta.badge} text={meta.label} />
}
```

Production notes:

- Keep enum mapping centralized.
- Do not communicate status with color alone.
- Match backend states exactly and handle unknown states defensively.
- Reuse the same labels across filters, table cells, and detail pages.

