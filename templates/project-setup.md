# Project Setup Template

Use this only for new projects or when the user explicitly asks for setup guidance.

## Recommended Defaults

- React 18+
- TypeScript
- Vite or the project's chosen framework
- Ant Design 5.x
- `@ant-design/icons`
- pnpm unless an existing lockfile says otherwise

## Provider Skeleton

```tsx
import { App, ConfigProvider } from 'antd'

export const Providers = ({ children }: { children: React.ReactNode }) => (
  <ConfigProvider>
    <App>{children}</App>
  </ConfigProvider>
)
```

## Validation

Add scripts according to the project conventions:

- typecheck
- lint
- build
- test, when a test runner is present

