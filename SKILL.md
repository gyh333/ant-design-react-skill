---
name: ant-design-react-skill
description: Build, modify, review, or troubleshoot production React applications that use Ant Design. Use for Ant Design installation, Vite or Next.js setup, antd v5 configuration, ConfigProvider, App provider, message/modal/notification APIs, forms, tables, drawers, modals, uploads, navigation, theming tokens, dark mode, i18n, Redux/Zustand/TanStack Query integration, TypeScript, accessibility, performance, and enterprise admin systems such as OA, MES, CRM, CMS, ERP, commerce, dashboards, and operations consoles.
---

# Ant Design React Skill

Use this skill for production-grade React + Ant Design work. Prefer the target project's conventions over generic examples. Default to React 18+, TypeScript, function components, hooks, Ant Design 5.x, Vite or Next.js, and CSS-in-JS/token-based theming unless the project proves otherwise.

## Operating Procedure

1. Inspect the project before editing: package manager, React version, `antd` version, framework, router, state/query layer, import strategy, theme setup, form/table abstractions, test/build scripts, and design conventions.
2. Identify the task type and read only the relevant files from the routing table.
3. Confirm version-sensitive APIs from the installed package or official Ant Design docs when exact prop/event behavior matters.
4. Implement using local patterns first. Do not paste examples verbatim when the project already has wrappers, hooks, request clients, layout components, or permission helpers.
5. Apply `references/production-checklist.md` for user-facing or shared components.
6. Run the narrowest useful validation available in the project, such as typecheck, build, lint, unit tests, or component tests. Report any validation that cannot run.

## Routing

| Task | Read first |
|---|---|
| Install or configure Ant Design | `examples/guide/installation.md`, `templates/project-setup.md` |
| antd v5 provider, App, message, modal, notification | `examples/guide/app-provider.md`, `references/modern-antd.md` |
| Next.js / SSR / App Router integration | `examples/guide/nextjs.md`, `references/modern-antd.md` |
| Theme tokens, dark mode, compact mode, CSS variables | `examples/guide/theme.md`, `references/theme-system.md`, `references/modern-antd.md` |
| i18n, Chinese locale, date locale | `examples/guide/i18n.md`, `references/modern-antd.md` |
| Form validation, form dialogs, dynamic forms | `examples/components/form.md`, `examples/advanced-forms/dynamic-form.md`, `references/advanced-forms.md`, `references/production-checklist.md` |
| Select, DatePicker, TreeSelect, Cascader | matching file under `examples/components/`, `references/component-index.md`, `references/modern-antd.md` |
| Tables, filters, pagination, row selection, bulk actions | `examples/components/table.md`, `examples/advanced-tables/search-table.md`, `references/advanced-tables.md`, `examples/production/crud-page.md`, `references/production-checklist.md` |
| Modal, Drawer, confirmation flows, detail panels | `examples/components/modal-drawer.md`, `examples/production/detail-drawer.md`, `references/production-checklist.md` |
| Uploads, import/export, file validation | `examples/components/upload.md`, `examples/production/import-export.md`, `references/production-checklist.md` |
| Status tags, descriptions, tabs, steps, dropdown actions | matching file under `examples/components/`, `references/component-routing.md` |
| Layout, menu, breadcrumbs, routed admin shell | `examples/layout/admin-shell.md`, `examples/router/route-menu.md` |
| Auth, permissions, protected actions | `examples/auth/permission-actions.md`, `references/permission-architecture.md`, `references/business-scenarios.md` |
| Dashboards, charts, KPI cards | `examples/production/dashboard.md`, `examples/production/echarts-dashboard.md`, `references/business-scenarios.md` |
| Approval, order/refund, CMS, settings, bulk actions | matching file under `examples/production/`, `references/business-scenarios.md`, `references/enterprise-patterns.md` |
| ProComponents / Ant Design Pro style projects | `references/procomponents.md`, inspect local dependencies before using |
| Enterprise admin scenarios | `references/enterprise-patterns.md`, `references/business-scenarios.md`, then matching files under `examples/production/` |
| Component choice, coverage, or missing examples | `references/component-index.md`, `references/component-routing.md`, `references/modern-antd.md` |
| TypeScript, refs, generic helpers, typed columns | `examples/typescript/patterns.md`, matching component example |
| Request state, Axios errors, TanStack Query | `references/request-error-handling.md`, matching file under `examples/integrations/`, `examples/production/crud-page.md` |
| Testing, accessibility, performance review | `references/testing-performance.md`, `references/production-checklist.md` |
| Troubleshooting or API precision | `examples/troubleshooting/common-issues.md`, `references/modern-antd.md`, inspect local `antd` package and installed types |
| Skill maintenance or release updates | `references/maintenance.md` |

When a row points to a directory or broad topic, read only the specific file needed for the task unless the user asks for a broad audit.

## Non-Negotiable Rules

- Use React and Ant Design. Do not suggest Vue, Ant Design Vue, or legacy antd APIs unless the target project already uses them.
- Prefer Ant Design 5.x patterns: `ConfigProvider` tokens, `App` provider for static feedback APIs, and current component APIs.
- Match the project package manager and framework. Prefer pnpm for new projects; if a lockfile exists, follow it.
- Respect local wrappers around `Table`, `Form`, `Modal`, `Drawer`, request hooks, permissions, and layout. Extend established abstractions before inventing new ones.
- Use controlled state deliberately for forms, tables, filters, modals, drawers, uploads, and selection.
- Do not invent props/events for newer components. Verify against installed types or official docs.
- Represent loading, empty, error, disabled, validation, permission, and responsive states in production flows.
- Avoid marketing-page visual patterns for admin or operational tools. Prefer dense, scannable, task-oriented layouts.

## Production Defaults

- Forms: typed model, explicit validation rules, submit loading, duplicate-submit prevention, server error mapping, reset behavior, and clear create/edit separation.
- Tables: stable `rowKey`, explicit query state, server-side pagination/filtering for large data, selection cleanup, empty/loading/error states, and accessible row actions.
- Modals and drawers: explicit open state, confirm loading, dirty-state protection when appropriate, focus/close behavior, and no accidental dismiss for data-entry flows.
- Uploads: validate type/size/count before upload, handle progress/error/success/remove/preview, keep controlled `fileList`, and never trust client validation alone.
- Feedback: use message, notification, modal confirm, and loading indicators intentionally; avoid repeated stacked messages during polling or batch operations.
- Theming: prefer Ant Design tokens and `ConfigProvider` over broad CSS overrides. Use scoped CSS only when token configuration cannot express the requirement.

## TypeScript Pattern

```tsx
import { Button, Form, Input } from 'antd'
import type { FormProps } from 'antd'

interface UserForm {
  email: string
  name: string
}

const UserEditor = () => {
  const [form] = Form.useForm<UserForm>()

  const submit: FormProps<UserForm>['onFinish'] = async (values) => {
    // submit typed form data
  }

  return (
    <Form<UserForm> form={form} layout="vertical" onFinish={submit}>
      <Form.Item<UserForm>
        name="email"
        label="Email"
        rules={[{ required: true, type: 'email' }]}
      >
        <Input autoComplete="email" />
      </Form.Item>
      <Button type="primary" htmlType="submit">
        Save
      </Button>
    </Form>
  )
}
```
