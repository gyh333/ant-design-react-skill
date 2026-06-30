# Settings Form

Settings pages need dirty-state handling and clear save behavior.

```tsx
import { useEffect, useState } from 'react'
import { Button, Form, InputNumber, Switch } from 'antd'

interface SettingsForm {
  enabled: boolean
  retryLimit: number
}

export const SettingsPanel = ({
  data,
  onSave,
}: {
  data: SettingsForm
  onSave: (values: SettingsForm) => Promise<void>
}) => {
  const [form] = Form.useForm<SettingsForm>()
  const [saving, setSaving] = useState(false)

  useEffect(() => {
    form.setFieldsValue(data)
  }, [data, form])

  const save = async () => {
    const values = await form.validateFields()
    setSaving(true)
    try {
      await onSave(values)
    } finally {
      setSaving(false)
    }
  }

  return (
    <Form<SettingsForm> form={form} layout="vertical">
      <Form.Item<SettingsForm> name="enabled" label="Enabled" valuePropName="checked">
        <Switch />
      </Form.Item>
      <Form.Item<SettingsForm>
        name="retryLimit"
        label="Retry limit"
        rules={[{ required: true, type: 'number', min: 0, max: 10 }]}
      >
        <InputNumber min={0} max={10} />
      </Form.Item>
      <Button type="primary" loading={saving} onClick={save}>
        Save
      </Button>
    </Form>
  )
}
```

Production notes:

- Add dirty-state protection for navigation and close.
- Show audit fields such as updated user and updated time when available.
- Decide whether to save optimistically or after server confirmation.
- Roll back optimistic changes on failure.

