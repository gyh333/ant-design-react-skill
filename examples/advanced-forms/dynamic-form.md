# Dynamic Forms

Use `Form.List` for dynamic arrays, and keep nested name paths explicit.

```tsx
import { Button, Form, Input, Space } from 'antd'

interface RuleForm {
  rules: Array<{ field: string; value: string }>
}

export const RuleEditor = () => {
  const [form] = Form.useForm<RuleForm>()

  return (
    <Form<RuleForm> form={form} layout="vertical" initialValues={{ rules: [{}] }}>
      <Form.List name="rules">
        {(fields, { add, remove }) => (
          <>
            {fields.map((field) => (
              <Space key={field.key} align="baseline">
                <Form.Item
                  {...field}
                  name={[field.name, 'field']}
                  rules={[{ required: true, message: 'Field is required' }]}
                >
                  <Input placeholder="Field" />
                </Form.Item>
                <Form.Item
                  {...field}
                  name={[field.name, 'value']}
                  rules={[{ required: true, message: 'Value is required' }]}
                >
                  <Input placeholder="Value" />
                </Form.Item>
                <Button danger onClick={() => remove(field.name)}>
                  Remove
                </Button>
              </Space>
            ))}
            <Button onClick={() => add()}>Add rule</Button>
          </>
        )}
      </Form.List>
    </Form>
  )
}
```

For production, add item-level IDs when editing persisted arrays, clarify remove behavior, and map server validation errors to nested paths.

