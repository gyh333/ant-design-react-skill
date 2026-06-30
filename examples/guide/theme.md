# Theme

Prefer Ant Design 5 tokens and algorithms before writing broad CSS overrides.

```tsx
import { ConfigProvider, theme } from 'antd'

export const ThemeProvider = ({ children }: { children: React.ReactNode }) => (
  <ConfigProvider
    theme={{
      algorithm: theme.defaultAlgorithm,
      token: {
        colorPrimary: '#1677ff',
        borderRadius: 6,
      },
      components: {
        Button: {
          controlHeight: 36,
        },
      },
    }}
  >
    {children}
  </ConfigProvider>
)
```

For dark mode, switch algorithms deliberately:

```tsx
algorithm: isDark ? theme.darkAlgorithm : theme.defaultAlgorithm
```

Avoid deep CSS selectors unless the project already uses them and tokens cannot express the requirement.

