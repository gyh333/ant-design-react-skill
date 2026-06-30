# Bulk Actions

Bulk actions need selection validation, confirmation, and partial failure handling.

```tsx
import { Alert, Button, Modal, Space } from 'antd'

export const BulkToolbar = ({
  selectedCount,
  loading,
  onClear,
  onDisable,
}: {
  selectedCount: number
  loading: boolean
  onClear: () => void
  onDisable: () => Promise<void>
}) => (
  <Alert
    type="info"
    showIcon
    message={
      <Space>
        <span>{selectedCount} selected</span>
        <Button size="small" onClick={onClear}>
          Clear
        </Button>
        <Button
          size="small"
          danger
          loading={loading}
          onClick={() => {
            Modal.confirm({
              title: 'Disable selected records?',
              content: 'This operation may affect active users.',
              okButtonProps: { danger: true },
              onOk: onDisable,
            })
          }}
        >
          Disable
        </Button>
      </Space>
    }
  />
)
```

Production notes:

- Validate selected records before submitting.
- Explain partial failures and preserve failed items when possible.
- Clear selection only after confirmed success or after records disappear from the current result set.
- Keep backend authorization authoritative.

