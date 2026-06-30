# Route Menu

Use this pattern when the project has route metadata and permission-aware menus.

```ts
interface RouteMeta {
  path: string
  title: string
  icon?: React.ReactNode
  permission?: string
  children?: RouteMeta[]
}
```

Menu generation rules:

- Filter by permission before rendering.
- Keep selected/open keys derived from the current route.
- Avoid duplicating route labels in separate menu config unless the project already does.
- Keep hidden routes out of the menu but still routable when required.

Always follow the project's router: React Router, Next.js routing, Umi, TanStack Router, or a local abstraction.

