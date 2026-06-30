# Import And Export

Import/export flows need clear progress, validation, and failure reporting.

## Import Flow

- Provide template download.
- Validate file type and size before upload.
- Upload with progress.
- Show parsing result: total, success, failed.
- Provide downloadable error report for failed rows.
- Refresh table after successful import.

```tsx
import { Button, Upload } from 'antd'
import type { UploadProps } from 'antd'

export const ImportButton = ({ onImport }: { onImport: UploadProps['customRequest'] }) => (
  <Upload
    accept=".xlsx,.xls,.csv"
    showUploadList={false}
    customRequest={onImport}
    beforeUpload={(file) => {
      const allowed = /\.(xlsx|xls|csv)$/i.test(file.name)
      const smallEnough = file.size / 1024 / 1024 <= 20
      return allowed && smallEnough
    }}
  >
    <Button>Import</Button>
  </Upload>
)
```

## Export Flow

- Export using current query filters by default.
- Clarify whether export includes selected rows or all filtered rows.
- Show loading state for long exports.
- Handle async export jobs when the backend queues reports.
- Avoid exporting without permission checks.

