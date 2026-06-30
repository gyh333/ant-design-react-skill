# Upload

Use controlled `fileList` when upload state belongs to a form.

```tsx
import { Upload } from 'antd'
import type { UploadFile, UploadProps } from 'antd'

export const DocumentUpload = ({
  fileList,
  onChange,
}: {
  fileList: UploadFile[]
  onChange: (fileList: UploadFile[]) => void
}) => {
  const beforeUpload: UploadProps['beforeUpload'] = (file) => {
    const isPdf = file.type === 'application/pdf'
    const isSmallEnough = file.size / 1024 / 1024 <= 10
    return isPdf && isSmallEnough
  }

  return (
    <Upload
      accept="application/pdf"
      fileList={fileList}
      beforeUpload={beforeUpload}
      onChange={({ fileList }) => onChange(fileList)}
      maxCount={1}
    >
      Upload PDF
    </Upload>
  )
}
```

Client validation is only a user experience layer. Keep server validation authoritative.

