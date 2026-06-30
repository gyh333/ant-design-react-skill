# Component Index

Use this file to understand local coverage and decide when to verify APIs against the installed `antd` package.

## Covered By Local Examples

| Area | Local File |
|---|---|
| Installation | `examples/guide/installation.md` |
| App provider and feedback context | `examples/guide/app-provider.md` |
| Theme tokens and dark mode | `examples/guide/theme.md` |
| Next.js setup notes | `examples/guide/nextjs.md` |
| i18n and locale | `examples/guide/i18n.md` |
| Form | `examples/components/form.md` |
| Dynamic form | `examples/advanced-forms/dynamic-form.md` |
| Table | `examples/components/table.md` |
| Search table | `examples/advanced-tables/search-table.md` |
| Modal and Drawer | `examples/components/modal-drawer.md` |
| Select | `examples/components/select.md` |
| DatePicker | `examples/components/date-picker.md` |
| TreeSelect | `examples/components/tree-select.md` |
| Cascader | `examples/components/cascader.md` |
| Descriptions | `examples/components/descriptions.md` |
| Tabs and Steps | `examples/components/tabs-steps.md` |
| Popconfirm and Dropdown | `examples/components/popconfirm-dropdown.md` |
| Status display | `examples/components/status-display.md` |
| Upload | `examples/components/upload.md` |
| Admin shell | `examples/layout/admin-shell.md` |
| Route menu | `examples/router/route-menu.md` |
| Permission actions | `examples/auth/permission-actions.md` |
| CRUD page | `examples/production/crud-page.md` |
| Dashboard | `examples/production/dashboard.md` |
| ECharts dashboard | `examples/production/echarts-dashboard.md` |
| Detail drawer | `examples/production/detail-drawer.md` |
| Bulk actions | `examples/production/bulk-actions.md` |
| Approval workflow | `examples/production/approval-workflow.md` |
| Import/export | `examples/production/import-export.md` |
| Settings form | `examples/production/settings-form.md` |
| Order/refund workflow | `examples/production/order-refund.md` |
| CMS editor | `examples/production/cms-editor.md` |
| Error and empty states | `examples/production/error-empty-states.md` |
| Query state | `examples/integrations/query-state.md` |
| Axios error handling | `examples/integrations/axios-error-handling.md` |
| TanStack Query | `examples/integrations/tanstack-query.md` |
| TypeScript | `examples/typescript/patterns.md` |
| Troubleshooting | `examples/troubleshooting/common-issues.md` |

## Verify Before Producing Production Code

Local examples are intentionally selective. Always inspect installed types or official docs for:

- Newer components or recently changed props.
- Components with complex value types: `DatePicker`, `RangePicker`, `TreeSelect`, `Cascader`, `Upload`, `Table`, `Form.List`, `Transfer`.
- Theme token names and component-level tokens.
- Static feedback APIs under custom theme, locale, prefix, or CSS variable mode.
- SSR integration and style extraction in Next.js or custom server rendering.

## Common Components Not Yet Fully Covered

- `AutoComplete`
- `Avatar`
- `Badge`
- `Breadcrumb`
- `Calendar`
- `Card`
- `Collapse`
- `Empty`
- `Flex`
- `FloatButton`
- `InputNumber`
- `List`
- `Menu`
- `Pagination`
- `Popover`
- `Result`
- `Segmented`
- `Skeleton`
- `Space`
- `Statistic`
- `Tag`
- `Timeline`
- `Tooltip`
- `Tour`
- `Transfer`
- `Tree`
- `Watermark`
