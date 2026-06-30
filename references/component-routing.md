# Component Routing

Use this file when choosing Ant Design components or deciding which local example to read.

| Need | Prefer | Notes |
|---|---|---|
| Data entry | `Form`, `Input`, `Select`, `DatePicker`, `InputNumber`, `Checkbox`, `Radio`, `Switch` | Keep labels explicit and validation typed. |
| Search/filter toolbar | `Form`, `Space`, `Button`, `Grid`, `Flex` | Collapse advanced filters in dense admin pages. |
| Data listing | `Table`, `Pagination`, `Empty`, `Spin`, `Alert` | Use server-side query state for large datasets. |
| Detail view | `Descriptions`, `Card`, `Drawer`, `Tabs` | Use drawers for contextual details without losing list context. |
| Create/edit flow | `Modal` or `Drawer` + `Form` | Use confirm loading and reset behavior. |
| Confirmation | `Modal.confirm`, `Popconfirm` | Use `Popconfirm` for small inline actions and modal confirm for heavier context. |
| Feedback | `message`, `notification`, `Modal`, `Result` | Prefer context-aware APIs under `App` in antd v5. |
| Navigation | `Menu`, `Breadcrumb`, `Tabs`, `Dropdown` | Keep route metadata and permission state centralized. |
| File handling | `Upload` | Use controlled `fileList` when bound to a form. |
| Layout | `Layout`, `Grid`, `Flex`, `Space`, `Splitter` | Avoid decorative card-heavy layouts for operational tools. |
| Metrics | `Statistic`, `Progress`, `Table`, chart library | Pair with loading/empty/error states. |
| Status display | `Tag`, `Badge`, `Typography.Text` | Use text plus color; keep enum mapping centralized. |
| Hierarchical selection | `TreeSelect`, `Cascader`, `Tree` | Verify value shape and lazy loading needs. |
| Date filters | `DatePicker`, `RangePicker` | Convert dayjs values to API payloads explicitly. |

## Verify Before Use

Check installed `antd` types or official docs before using newer or version-sensitive components and props, including:

- `App`
- `Flex`
- `Splitter`
- `Watermark`
- `Tour`
- `QRCode`
- `FloatButton`
- `Segmented`
- `Table` virtual scrolling
- `Form.List`
- design token algorithms
- CSS variable mode
