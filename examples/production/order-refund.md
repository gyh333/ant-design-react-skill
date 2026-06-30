# Order And Refund Workflow

Commerce workflows need status transition guards and immutable operation history.

Recommended sections:

- Order summary with `Descriptions`.
- Item list with `Table`.
- Payment/refund timeline.
- Shipping or fulfillment state.
- Row or page actions guarded by status and permission.

Production checks:

- Do not infer allowed actions only from frontend state; backend must authorize transitions.
- Confirm refund, cancel, revoke, and manual adjustment actions.
- Preserve original amounts, discounts, fees, and audit fields.
- Handle partial refunds, split shipments, and after-sale states explicitly.
- Keep money formatting centralized.

