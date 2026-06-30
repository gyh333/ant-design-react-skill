# TreeSelect

Use `TreeSelect` for hierarchical choices such as departments, categories, regions, or permissions.

```tsx
import { TreeSelect } from 'antd'

interface TreeNode {
  title: string
  value: string
  children?: TreeNode[]
}

export const DepartmentSelect = ({
  value,
  treeData,
  onChange,
}: {
  value?: string
  treeData: TreeNode[]
  onChange: (value?: string) => void
}) => (
  <TreeSelect
    allowClear
    showSearch
    treeDefaultExpandAll
    placeholder="Select department"
    treeData={treeData}
    value={value}
    onChange={onChange}
  />
)
```

Production notes:

- Use stable `value` fields; do not use labels as IDs.
- For large trees, prefer lazy loading or server search.
- Decide whether parent nodes are selectable.
- Keep permission and visibility filtering on the server or central domain layer when required.

