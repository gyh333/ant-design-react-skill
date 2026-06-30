# Tabs And Steps

Use `Tabs` to separate meaningful peer sections. Use `Steps` for sequential processes.

```tsx
import { Steps, Tabs } from 'antd'

export const OrderDetailTabs = () => (
  <Tabs
    items={[
      { key: 'summary', label: 'Summary', children: null },
      { key: 'items', label: 'Items', children: null },
      { key: 'history', label: 'History', children: null },
    ]}
  />
)

export const ApprovalSteps = ({ current }: { current: number }) => (
  <Steps
    current={current}
    items={[
      { title: 'Submitted' },
      { title: 'Review' },
      { title: 'Approved' },
    ]}
  />
)
```

Production notes:

- Do not hide validation errors in inactive tabs without a visible summary.
- Avoid rendering expensive hidden tab panels unless state preservation is required.
- Map workflow steps from domain state, not array position alone.
- Keep rejected/cancelled/failed states visually and textually explicit.

