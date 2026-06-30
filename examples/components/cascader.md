# Cascader

Use `Cascader` for ordered hierarchical selection such as region, category path, or organization path.

```tsx
import { Cascader } from 'antd'
import type { CascaderProps } from 'antd'

interface Option {
  value: string
  label: string
  children?: Option[]
}

export const RegionCascader = ({
  options,
  value,
  onChange,
}: {
  options: Option[]
  value?: string[]
  onChange: (value: string[]) => void
}) => (
  <Cascader<Option>
    options={options}
    value={value}
    onChange={(value) => onChange(value as string[])}
    placeholder="Select region"
  />
)
```

Production notes:

- Confirm whether the backend expects the full path, leaf ID, or both.
- Use lazy loading for large hierarchies.
- Keep path labels for display when detail pages need readable names.
- Validate required paths at the form level.

