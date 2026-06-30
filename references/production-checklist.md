# Production Checklist

Use this checklist for shared components, user-facing workflows, and enterprise admin pages.

## Project Fit

- Follow the existing framework: Vite, Next.js, Umi, Remix, or another local setup.
- Follow the existing package manager and lockfile.
- Reuse local request clients, permission helpers, layout components, hooks, and wrappers.
- Match existing file naming, route organization, state management, and styling conventions.

## Forms

- Type the form model and validation paths.
- Use `Form.useForm<T>()` when the component owns the form instance.
- Show submit loading and prevent duplicate submits.
- Map server validation errors to fields with `form.setFields` when possible.
- Define reset behavior for create/edit switching and modal/drawer close.
- Protect unsaved data when closing would discard user input.
- Do not rely on placeholders as labels.

## Tables

- Use a stable `rowKey`.
- Keep query state explicit: filters, sorter, page, page size, total, loading, selected rows.
- Use server-side pagination/filtering/sorting for large datasets.
- Clear selected rows after successful batch operations or data refresh when records disappear.
- Provide loading, empty, and error states.
- Make row actions permission-aware and keyboard accessible.
- Avoid rendering heavy custom cells without memoization or virtualization when the table is large.

## Modals And Drawers

- Keep `open` controlled.
- Use confirm loading for async submits.
- Avoid accidental dismiss for data-entry flows.
- Reset or preserve state intentionally.
- Confirm before closing when unsaved changes can be lost.
- Return focus or keep keyboard flow predictable after close.

## Uploads

- Validate file type, size, count, and business rules on the client for UX.
- Treat server validation as authoritative.
- Use controlled `fileList` when form state owns uploaded files.
- Handle progress, success, error, remove, preview, and retry states when relevant.
- Do not expose credentials or internal upload endpoints in examples.

## Feedback And State

- Use `App.useApp()` or context-aware APIs when the project uses Ant Design 5 provider patterns.
- Avoid repeated stacked messages during polling, retries, or batch actions.
- Include empty, loading, error, disabled, and permission states where users can encounter them.
- Use destructive confirmations for delete, revoke, cancel, and irreversible operations.

## Accessibility And UX

- Provide visible labels or `aria-label` for icon-only actions.
- Do not communicate status by color alone.
- Keep form errors associated with their fields.
- Ensure popovers, dropdowns, modals, and drawers remain keyboard usable.
- Preserve readable layouts on narrow screens; collapse dense filters and action bars deliberately.

