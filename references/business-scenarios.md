# Business Scenarios

Use this matrix to route enterprise admin tasks to the right Ant Design patterns.

| Scenario | Primary Components | Production Requirements |
|---|---|---|
| Search list | `Form`, `Table`, `Space`, `Button`, `Tag` | URL/query state, server pagination, loading/empty/error, reset filters |
| CRUD page | `Table`, `Drawer` or `Modal`, `Form`, `Popconfirm` | stable rowKey, permission actions, submit loading, selection cleanup |
| Detail page | `Drawer`, `Descriptions`, `Tabs`, `Timeline` | skeleton/loading, audit trail, status tags, safe close |
| Approval workflow | `Table`, `Form`, `Modal`, `Timeline`, `Steps` | approval history, required comments, disabled states, irreversible confirmations |
| Batch operations | `Table`, `Modal.confirm`, `Alert` | selected row validation, partial failure handling, post-success cleanup |
| Import/export | `Upload`, `Button`, `Progress`, `Alert` | template download, file validation, progress, error report download |
| Settings form | `Form`, `Switch`, `InputNumber`, `Select` | dirty protection, optimistic update policy, rollback, audit fields |
| Dashboard | `Statistic`, `Card`, `Table`, chart library | stale data, refresh, drilldown, loading/empty/error, permission-limited views |
| CMS editor | `Form`, `Upload`, rich text editor, `Preview` | draft/publish separation, sanitization, image upload, autosave policy |
| Order/refund flow | `Descriptions`, `Table`, `Steps`, `Modal` | status transition guards, refund confirmation, immutable records |

## Implementation Notes

- Put filters close to the table they affect.
- Keep action columns predictable: view, edit, enable/disable, delete or revoke.
- Use status tags consistently and avoid color-only communication.
- Prefer drawers for contextual create/edit/detail flows from list pages.
- Persist query state in URL only when the project has that convention.

