# TypeScript Patterns

## Table Columns

```tsx
import type { TableProps } from 'antd'

interface Row {
  id: string
  name: string
}

const columns: TableProps<Row>['columns'] = [
  { title: 'Name', dataIndex: 'name' },
]
```

## Form Values

```tsx
import { Form } from 'antd'

interface Values {
  name: string
}

const [form] = Form.useForm<Values>()
```

## Upload

```tsx
import type { UploadFile, UploadProps } from 'antd'

const [fileList, setFileList] = useState<UploadFile[]>([])
const beforeUpload: UploadProps['beforeUpload'] = (file) => true
```

Use exported Ant Design types when available. Prefer local domain types for API payloads and table rows.

