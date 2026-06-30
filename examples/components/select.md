# Select

Use `Select` for bounded option sets and remote search only when the API supports it.

```tsx
import { Select } from 'antd'

interface StatusOption {
  label: string
  value: 'enabled' | 'disabled'
}

const statusOptions: StatusOption[] = [
  { label: 'Enabled', value: 'enabled' },
  { label: 'Disabled', value: 'disabled' },
]

export const StatusSelect = ({
  value,
  onChange,
}: {
  value?: StatusOption['value']
  onChange: (value?: StatusOption['value']) => void
}) => (
  <Select
    allowClear
    placeholder="Select status"
    options={statusOptions}
    value={value}
    onChange={onChange}
  />
)
```

Production notes:

- Keep option values typed when they map to backend enums.
- Use `labelInValue` only when the surrounding state really needs labels.
- Debounce remote search and handle loading, empty, and error states.
- Avoid loading large unpaginated option lists into the browser.

