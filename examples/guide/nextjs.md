# Next.js

Use this file when the target project uses Next.js. Inspect the local setup first.

## App Router

- Check whether the project already uses an Ant Design registry or style extraction setup.
- Keep client components explicit with `'use client'` when using interactive Ant Design components.
- Do not move large server-only logic into client components just to render Ant Design UI.
- Keep providers close to the app root when theme, locale, or feedback APIs must be global.

## Provider Example

```tsx
'use client'

import { App, ConfigProvider } from 'antd'

export const AntdProviders = ({ children }: { children: React.ReactNode }) => (
  <ConfigProvider>
    <App>{children}</App>
  </ConfigProvider>
)
```

## Validation

Run the project build after provider or SSR changes. Hydration and style-order issues may not appear in typecheck alone.

