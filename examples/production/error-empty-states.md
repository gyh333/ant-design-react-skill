# Error And Empty States

Production pages need explicit state rendering.

```tsx
import { Alert, Button, Empty, Spin } from 'antd'

export const StateBlock = ({
  loading,
  error,
  empty,
  onRetry,
  children,
}: {
  loading: boolean
  error?: Error
  empty: boolean
  onRetry: () => void
  children: React.ReactNode
}) => {
  if (loading) return <Spin />

  if (error) {
    return (
      <Alert
        type="error"
        showIcon
        message="Failed to load data"
        description={error.message}
        action={<Button onClick={onRetry}>Retry</Button>}
      />
    )
  }

  if (empty) return <Empty description="No data" />

  return <>{children}</>
}
```

Production notes:

- Distinguish permission empty, filter empty, and true no-data states.
- Keep retry actions close to the failed content.
- Avoid replacing the whole page with a spinner when only one panel is loading.

