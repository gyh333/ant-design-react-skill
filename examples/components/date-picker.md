# DatePicker

Verify the project's date value convention before editing date fields. Ant Design 5 usually works with dayjs values, but API payloads are often strings.

```tsx
import { DatePicker, Form } from 'antd'
import type { Dayjs } from 'dayjs'

interface FilterForm {
  createdAt?: [Dayjs, Dayjs]
}

export const CreatedAtRange = () => (
  <Form.Item<FilterForm> name="createdAt" label="Created at">
    <DatePicker.RangePicker allowClear />
  </Form.Item>
)
```

Map UI values to API payloads explicitly:

```ts
const toQuery = (values: FilterForm) => ({
  createdStart: values.createdAt?.[0]?.format('YYYY-MM-DD'),
  createdEnd: values.createdAt?.[1]?.format('YYYY-MM-DD'),
})
```

Production notes:

- Check locale configuration for `DatePicker`, `RangePicker`, and calendar-related components.
- Normalize timezone handling with the backend contract.
- Do not send dayjs objects directly to APIs.
- Preserve date range filters when paginating unless reset is intentional.

