# Common Issues

## Message Or Modal Does Not Pick Up Theme

Check whether the app uses Ant Design 5 `App` provider. Prefer `App.useApp()` inside components that need themed feedback APIs.

## Modal Or Drawer Uses `visible`

Ant Design 5 uses `open`. Check installed version before changing legacy code.

## DatePicker Locale Is Wrong

Check both `ConfigProvider` locale and the date library locale setup.

## Table Selection Persists Incorrectly

Use stable `rowKey`, clear selection after batch operations, and decide whether selection should persist across pages.

## Form Reset Breaks Edit Flow

Separate create and edit initialization. Reset only when the modal/drawer closes or the edited record changes intentionally.

## CSS Overrides Do Not Work

Prefer tokens and component tokens. If CSS is required, inspect CSS-in-JS ordering and local scoping.

