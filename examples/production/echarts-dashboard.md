# ECharts Dashboard

Use the project's chart library if one already exists. Do not add ECharts just because this example mentions it.

```tsx
import { Card, Statistic } from 'antd'

export const KpiCard = ({
  title,
  value,
  loading,
}: {
  title: string
  value: number
  loading: boolean
}) => (
  <Card loading={loading}>
    <Statistic title={title} value={value} />
  </Card>
)
```

Production notes:

- Define chart container height explicitly.
- Resize charts when containers change size.
- Show loading, empty, error, and stale-data states.
- Preserve filters in drilldown links.
- Keep metric definitions and formatting centralized.

