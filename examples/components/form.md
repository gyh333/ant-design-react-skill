# Form

Use typed form values and explicit submit state.

```tsx
import { useState } from 'react'
import { Button, Form, Input } from 'antd'
import type { FormProps } from 'antd'

interface UserForm {
  name: string
  email: string
}

export const UserFormPanel = () => {
  const [form] = Form.useForm<UserForm>()
  const [submitting, setSubmitting] = useState(false)

  const onFinish: FormProps<UserForm>['onFinish'] = async (values) => {
    setSubmitting(true)
    try {
      await saveUser(values)
    } catch (error) {
      form.setFields([{ name: 'email', errors: ['Email is already used'] }])
    } finally {
      setSubmitting(false)
    }
  }

  return (
    <Form<UserForm> form={form} layout="vertical" onFinish={onFinish}>
      <Form.Item<UserForm>
        name="name"
        label="Name"
        rules={[{ required: true, message: 'Name is required' }]}
      >
        <Input autoComplete="name" />
      </Form.Item>

      <Form.Item<UserForm>
        name="email"
        label="Email"
        rules={[{ required: true, type: 'email' }]}
      >
        <Input autoComplete="email" />
      </Form.Item>

      <Button type="primary" htmlType="submit" loading={submitting}>
        Save
      </Button>
    </Form>
  )
}
```

Replace `saveUser` with the project's request helper. Keep server error mapping specific to the real API shape.

