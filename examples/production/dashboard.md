# Dashboard

Dashboards need state handling as much as charts.

Recommended sections:

- KPI cards with `Statistic`.
- Trend charts with the project's chart library.
- Exception/alert list with `Table` or `List`.
- Time range filter.
- Refresh action and last-updated timestamp.

Production checks:

- Loading state for each data group or the whole page.
- Empty state when the user has no data or no permission.
- Error state with retry.
- Stale data indication when refresh fails.
- Responsive layout for narrow screens.
- Drilldown links preserve filters when appropriate.

