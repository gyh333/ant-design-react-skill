# App Provider

Use Ant Design 5 `App` when feedback APIs need provider context, theme, locale, or prefix configuration.

```tsx
import { App, ConfigProvider } from 'antd'

export const Providers = ({ children }: { children: React.ReactNode }) => (
  <ConfigProvider>
    <App>{children}</App>
  </ConfigProvider>
)
```

Use inside components:

```tsx
import { App, Button } from 'antd'

export const SaveButton = () => {
  const { message } = App.useApp()

  return (
    <Button
      type="primary"
      onClick={() => {
        message.success('Saved')
      }}
    >
      Save
    </Button>
  )
}
```

Prefer local, context-aware APIs over globally imported static APIs when the app uses custom theme, locale, or prefix settings.

