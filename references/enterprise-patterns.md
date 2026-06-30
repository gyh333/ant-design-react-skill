# Enterprise Patterns

Use this reference for admin systems and operational tools such as OA, MES, CRM, CMS, ERP, commerce, dashboards, and internal platforms.

## Shared Principles

- Optimize for repeated use, scanning, comparison, and safe operation.
- Keep primary actions predictable and permission-aware.
- Make query state shareable when the project supports URL search params.
- Prefer server-side pagination and filtering for operational data.
- Include audit fields, status, owner, updated time, and operation history when relevant.

## Domain Routing

| Domain | Common Screens | Important States |
|---|---|---|
| OA | approval list, workflow detail, task assignment, leave/travel forms | pending, approved, rejected, revoked, delegated |
| MES | work orders, process tracking, equipment status, quality inspection | queued, running, paused, failed, completed, abnormal |
| CRM | leads, customers, contacts, opportunities, follow-ups | stage, owner, next action, overdue, lost reason |
| CMS | article list, editor, category management, review workflow | draft, scheduled, published, archived, rejected |
| ERP | master data, inventory, purchase/sales orders, finance review | locked, posted, reversed, partially fulfilled |
| Commerce | orders, refunds, products, inventory, promotions | paid, shipped, refunded, cancelled, after-sale |
| Dashboard | KPI cards, trend charts, alerts, ranked lists | loading, empty, stale data, drilldown, permission limited |

## UI Guidance

- Use compact, structured layouts for dense data.
- Keep filters close to the table they affect.
- Use drawers for contextual detail and edit flows from list pages.
- Use modals for focused confirmation or short forms.
- Use tabs only when each tab has meaningful independent content.
- Avoid hero sections, marketing cards, and decorative visual treatment in enterprise tools.

