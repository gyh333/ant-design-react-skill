# Modern Ant Design Notes

Use this file for Ant Design 5.x behavior, migration-sensitive APIs, and areas where agents often guess.

## Ant Design 5 Defaults

- Prefer `ConfigProvider` theme tokens over Less variable overrides.
- Prefer the `App` provider when using `message`, `notification`, or modal APIs that need context.
- Prefer `open` over legacy `visible` props.
- Prefer current `items` APIs where the installed version supports them.
- Use `dayjs` assumptions carefully; check the target project if it uses custom date handling.

## Provider Pattern

```tsx
import { App, ConfigProvider } from 'antd'
import { theme } from 'antd'

export const RootProviders = ({ children }: { children: React.ReactNode }) => (
  <ConfigProvider
    theme={{
      algorithm: theme.defaultAlgorithm,
      token: {
        borderRadius: 6,
      },
    }}
  >
    <App>{children}</App>
  </ConfigProvider>
)
```

Inside components:

```tsx
import { App } from 'antd'

const { message, modal, notification } = App.useApp()
```

## Verify Version-Sensitive Areas

- `Table` virtualization and scroll behavior.
- `Form.List` validation and nested name paths.
- `Upload` controlled `fileList` and custom request signatures.
- `Modal` and `Drawer` close behavior.
- `DatePicker` value type and locale configuration.
- token names and theme algorithms.
- new components such as `Flex`, `Splitter`, `Tour`, and `QRCode`.

