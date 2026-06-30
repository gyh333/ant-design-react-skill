# Theme System

Use this reference for design token and theming work.

## Ant Design 5 Direction

- Prefer `ConfigProvider` theme tokens.
- Use component tokens for component-specific behavior.
- Use algorithms for default, dark, and compact themes.
- Avoid Less-variable-era assumptions unless the project is on an older stack.

## Token Scope

Use global tokens for brand-level decisions:

- `colorPrimary`
- `borderRadius`
- `fontFamily`
- `colorBgLayout`
- `controlHeight`

Use component tokens for local component tuning:

- Button heights
- Table header backgrounds
- Form item spacing
- Layout trigger colors

## CSS Overrides

CSS is acceptable when:

- tokens cannot express the requirement
- the project already has a scoped styling convention
- selector scope is narrow and stable

Avoid broad selectors targeting generated class names.

