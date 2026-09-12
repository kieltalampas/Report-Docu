# Retail Order Fulfillment Lead Time — README

## What this is
A Looker Studio report that measures how many days it takes a retail order to go
from order creation to fulfillment, tracked separately for **Install** and
**Delivery** transaction types.

## Purpose / question answered
> How many days does it take for a retail order to go from order creation to
> fulfillment?

This exists to give a defensible, auditable answer to that question — the
original lead-time field in the underlying data source turned out to be
unreliable (see **Known issues** below), so this report also serves as the
corrected replacement.

## Data source
- **Source:** `Gulong PH V3 - Order`
- Note: this report does **not** have edit access to the data source itself.
  All fixes and new fields below were built at the **report level**
  (chart-scoped), not the source level. See "Access limitation" section.

## Scope / filters applied
- **Retail channels only** — existing filter `Web/FB/Chatbot/Walkin Orders`,
  covering `Website`, `Fb`, `Chatbot`, `Walk-in`. Excludes B2B, marketplace,
  and other non-retail order types.
- **Fulfilled only** — `Status = Fulfilled`. Orders still in progress (New,
  Pending, Processing) or closed unfavorably (Cancelled, For Refund, For
  Return) are excluded, since there's no completion date to measure lead
  time against.
- **Transaction type** — restricted to `Install` and `Delivery` only.
- **Date range control** (top of report) — filters all charts by `order_date`
  (when the order was placed), not delivery date.
- Two additional filter chips (`exclude status=new`, duplicated; `clean up`)
  are inherited on this page but are not editable (no data-source access).
  Investigated and confirmed **not currently affecting the numbers** in this
  report — see "Known issues / investigated" below for detail.

## Metrics on the dashboard

| Element | What it shows |
|---|---|
| Avg Install Lead Time (Calendar Days) | Average days from order to delivery, Install orders only |
| Install Order Count | Number of Install orders the average is based on (n) |
| Avg Delivery Lead Time (Calendar Days) | Average days from order to delivery, Delivery orders only |
| Delivery Order Count | Number of Delivery orders the average is based on (n) |
| Filter: Lead Time (Calendar Days) slider | Drill-down control — narrows the table to orders within a chosen day range. Defaults to full range (no orders hidden) unless manually adjusted. |
| Filter: Customer Type dropdown | Narrows all numbers to a single retail channel (e.g. just Website) |
| Detail table | Order-level rows: id, order date, delivery date, transaction type, customer type, lead time — the evidence behind the averages |

## The lead-time calculation
**Field name:** `Lead Time (Calendar Days)`
**Formula (Looker Studio calculated field):**
```
CASE
  WHEN delivery_date IS NULL THEN NULL
  ELSE DATETIME_DIFF(delivery_date, order_date, DAY)
END
```
Counts every calendar day between order date and delivery date, **including
weekends**. This field had to be recreated separately inside each chart that
uses it (table, both scorecards, both count cards, the slider) because it
was originally created at the chart level, not the data-source level — see
"Access limitation."

### Important definitional note: calendar days, not workdays
This counts weekends as normal days. It does **not** exclude Saturdays/Sundays.
This was a deliberate, temporary decision — not an oversight:
- The original field in the data source (`Delivery workdays`) was meant to
  exclude weekends, but was found to be unreliable (see below), so it
  couldn't be reused or trusted as a reference.
- Whether a weekend-landing delivery should count differently is a business
  question (needs an ops-defined SLA/rule) that hasn't been answered yet.
- Once that rule exists, the formula above can be updated to exclude
  weekends accordingly.

## Known issues found and fixed

### 1. Original `Delivery workdays` field — unreliable, replaced
Spot-checked against raw order/delivery dates in the backend. Findings:
- Row-level: of 10 sampled orders, 8 matched one weekday-counting
  convention, 1 matched a different convention, and 1 matched **no**
  possible formula (its shown value exceeded the maximum number of weekdays
  mathematically possible between its own order and delivery dates).
- Aggregate-level: recomputed averages didn't match the dashboard's
  original 2.85 (Install) / 1.67 (Delivery) under either weekday-counting
  convention tested.
- Conclusion: the field applies inconsistent logic across rows. Not usable.
  Replaced with the calendar-day formula above.

### 2. Access limitation
No edit access to the `Gulong PH V3 - Order` data source, so the broken
field could not be fixed at the source, and the replacement field could not
be defined once and reused everywhere. It had to be manually recreated in
every chart that needed it. **Maintenance risk:** if the formula is ever
changed (e.g. to add weekend-exclusion logic later), every copy needs to be
updated individually, or the charts will silently drift out of sync with
each other.

### 3. Filter/range controls need to default to "no filtering"
Found twice during QA that report controls (the Lead Time slider) had a
handle sitting away from the true data min/max, silently excluding orders
from all scorecards without it being obvious from looking at the chart.
Confirmed fixed — slider now defaults to the full 0–8 day range. Worth
re-checking after any future edits to this report.

### 4. Delivery scorecard / count metric swap
The "Avg Delivery Lead Time" and "Delivery Order Count" cards briefly had
their underlying metrics swapped (average showing the count, count showing
the average). Confirmed fixed.

## Known issues investigated, not currently affecting this report
- **Duplicate `exclude status=new` filter chips:** redundant, not
  conflicting — `Fulfilled Only` already excludes `Status = New`, so this
  filter has no additional effect here.
- **`clean up` filter:** likely excludes test orders (e.g. customer name
  "Frig Test") and orders flagged `isDeleted = 1` in the backend. Confirmed
  none of the currently-flagged test/deleted orders in this data's date
  range have `Status = Fulfilled`, so they're already excluded by the
  Fulfilled-only filter regardless — this report's numbers are not
  contaminated by test data.

## Verification
All figures below were independently cross-checked directly against the
backend order data (not just trusted from the report):

- Sep 1–11, 2026 (retail, fulfilled, Install/Delivery): Install n=89, avg
  3.88 days; Delivery n=6, avg 2.00 days; combined 95 orders; lead time
  range 0–8 days.

## Out of scope for this report (possible follow-ups)
- **Unfulfilled / backlog aging view** — a separate view of currently-open
  orders and how long they've been open. Not part of the original "lead
  time from order to fulfilled" task; would need its own scoping (e.g. which
  statuses count, recency window to avoid stale historical orders).
- **% within SLA scorecard** — needs an ops-defined day threshold before it
  can be built; a threshold invented without one would look like an
  official target when it isn't.
- **Workday-exclusion logic** — pending an ops decision on how
  weekend-landing orders should be treated.
