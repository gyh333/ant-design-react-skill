# Installation

Inspect the project before installing anything.

## Package Manager

- If a lockfile exists, follow it.
- Prefer pnpm for new projects.
- Do not mix package managers unless the user asks for migration.

## Vite React

```bash
pnpm add antd @ant-design/icons
```

Minimal usage:

```tsx
import { Button } from 'antd'

export const App = () => <Button type="primary">Save</Button>
```

## Next.js

Check the installed Next.js version and existing styling setup. For App Router projects, verify whether the project already uses Ant Design registry support or a custom style extraction setup before adding one.

## Validation

After installation or configuration, run the project's narrowest useful validation:

- package manager install verification
- `typecheck`
- `lint`
- `build`
- smoke test the page that imports Ant Design

