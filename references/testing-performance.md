# Testing And Performance

Use this reference for review tasks, shared components, and performance-sensitive pages.

## Validation Strategy

Prefer the narrowest validation that proves the change:

- TypeScript check for type-heavy forms, tables, and request mapping.
- Unit or component tests for reusable components and business logic.
- Build for framework/provider/theme changes.
- Storybook or visual review when the project already uses it.
- E2E tests for critical workflows such as approval, payment, refund, or publish.

## Test Targets

- Form validation and server error mapping.
- Submit loading and duplicate-submit prevention.
- Table query mapping, pagination, sorting, and selection cleanup.
- Modal/drawer open, close, reset, and dirty-state protection.
- Permission-gated actions.
- Upload validation and error handling.

## Performance Checks

- Avoid recreating large column arrays inside render without memoization when tables are heavy.
- Avoid uncontrolled rerenders from broad context or global state subscriptions.
- Use server-side pagination/filtering for large datasets.
- Consider virtualization only after verifying table height, scroll, row height, and fixed-column behavior.
- Debounce expensive search input only when the product interaction allows it.
- Do not render hidden heavy tab panels unless the UX requires state preservation.

## Accessibility Checks

- Icon-only buttons need visible tooltip text or `aria-label`.
- Form items need real labels, not only placeholders.
- Destructive actions need clear confirmation copy.
- Table action order should be stable.
- Loading and error states should be perceivable and not color-only.

