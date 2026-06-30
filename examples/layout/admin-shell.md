# Admin Shell

Use existing layout wrappers when present. For new admin shells, keep navigation, content, and actions predictable.

```tsx
import { Breadcrumb, Layout, Menu } from 'antd'

const { Header, Sider, Content } = Layout

export const AdminShell = ({ children }: { children: React.ReactNode }) => (
  <Layout style={{ minHeight: '100vh' }}>
    <Sider width={240}>
      <Menu mode="inline" items={[]} />
    </Sider>
    <Layout>
      <Header />
      <Content style={{ padding: 24 }}>
        <Breadcrumb items={[]} />
        {children}
      </Content>
    </Layout>
  </Layout>
)
```

Production notes:

- Generate menus from route metadata only if the project already follows that pattern.
- Keep collapsed state and selected keys synchronized with routing.
- Keep permission filtering centralized.
- Avoid card-heavy landing-page composition for operational tools.

