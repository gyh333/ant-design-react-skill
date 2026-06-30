# Modal And Drawer

Use controlled open state and async confirm loading.

```tsx
import { useEffect, useState } from 'react'
import { Button, Drawer, Form, Input } from 'antd'

interface UserForm {
  name: string
}

export const UserDrawer = ({
  open,
  initialValues,
  onClose,
  onSubmit,
}: {
  open: boolean
  initialValues?: Partial<UserForm>
  onClose: () => void
  onSubmit: (values: UserForm) => Promise<void>
}) => {
  const [form] = Form.useForm<UserForm>()
  const [submitting, setSubmitting] = useState(false)

  useEffect(() => {
    if (open) form.setFieldsValue(initialValues)
    if (!open) form.resetFields()
  }, [form, initialValues, open])

  const submit = async () => {
    const values = await form.validateFields()
    setSubmitting(true)
    try {
      await onSubmit(values)
      onClose()
    } finally {
      setSubmitting(false)
    }
  }

  return (
    <Drawer
      title={initialValues ? 'Edit user' : 'Create user'}
      open={open}
      onClose={onClose}
      destroyOnClose
      extra={
        <Button type="primary" loading={submitting} onClick={submit}>
          Save
        </Button>
      }
    >
      <Form<UserForm> form={form} layout="vertical">
        <Form.Item<UserForm> name="name" label="Name" rules={[{ required: true }]}>
          <Input />
        </Form.Item>
      </Form>
    </Drawer>
  )
}
```

Add dirty-state protection when closing can discard meaningful user input.

