# README — Gulong.ph "Targets Overview" Dashboard

**Note:** This is a *different* report from the mancom daily/MTD dashboards covered in the earlier README. This one is organized by **business line** (Website/FB, B2B and Hertz, Marketplace, Rapide) instead of by channel (TAira/CS/Website), and its focus is **hitting targets**, not just daily activity.

---

## What is this dashboard for?

**Simple purpose:** This dashboard exists to answer: *"Out of every business line we run, which ones are pulling their weight toward our monthly sales/gross profit target, and which ones are falling behind?"*

Where the mancom dashboards ask "how did today/this month go," this one asks "are we going to **hit our goal**, broken down by which part of the business is responsible?" That's why it has a **"NEEDED GROSS"** box that the mancom reports don't — it's target-driven, not just activity-tracking.

---

## Section 1: Business Line Summary (Website/FB, B2B and Hertz, Marketplace, Overall)

**What it's for:** A side-by-side scoreboard of every major sales channel/business line, so leadership can see at a glance which lines are growing, which are flat, and which need help.

| Metric | Simple meaning | Example (Website/FB) |
|---|---|---|
| **Orders** | Total number of orders placed | 216 orders placed (▲27.8% vs. comparison period) |
| **Fulfilled Orders** | Of those, how many were actually completed/delivered | 167 completed (▼1.2%) |
| **Tires Sold** | Total individual tires sold (not order count — one order can have 4 tires) | 570 tires sold (▼8.5%) |
| **Sales Net of VAT** | Total peso revenue, with tax removed | ₱3,468,308.39 (▼6.5%) |
| **To Be Fulfilled** | ⚠️ Here this is a **count of orders** still pending, NOT a peso amount (different from the mancom MTD report, where "To Be Fulfilled" was a peso figure!) | 169 orders still waiting to be fulfilled |
| **For Fulfillment Sales** | The peso value of those still-pending orders | ₱2,354,898.88 worth of orders still in progress |
| **Website/CS, Affiliates, Marketplace** | A channel-specific extra column (shows "-" when not applicable to that business line) | Not populated in this snapshot |
| **Needed Gross** | How much MORE gross profit this business line needs to bring in to hit its target | "No data" here, but the Overall section shows **-8.1M**, meaning the whole company is ₱8.1M short of its gross profit target so far |

**Example scenario:** Website/FB has 216 orders (up nicely, +27.8%) but Sales Net of VAT is down 6.5%. That combination usually means: *more people are ordering, but the average order value is smaller* — maybe more budget-tier tires are being sold, or fewer tires per order. Worth digging into "Average Ticket" (see Rapide section below) to confirm.

**B2B and Hertz** and most of **Marketplace** show "0" or "No data" — meaning basically no activity came through those lines this period. That's not necessarily bad on its own; it just means the report has nothing to summarize yet (e.g., a new or inactive channel).

**Overall** is simply all business lines added together — the company-wide total.

---

## Section 2: RAPIDE

**What it's for:** "Rapide" appears to be its own business line/brand (separate from the main Website/FB and B2B lines) — from the shop names further down (RAPIDE SAN ANTONIO MAKATI, RAPIDE MOLINO, etc.), this looks like a specific store/franchise brand line being tracked on its own.

**Top row — Orders, Fulfilled Orders, Tires Sold, Net Sales of VAT, To Be Fulfilled, For Fulfillment, B2B Rapide:** All showing **0**, with Orders down -100%. In simple terms: **Rapide had zero activity this period** — likely inactive, paused, or not yet launched for this date range. This is a flag worth asking about directly, since a -100% drop to zero usually means something changed operationally (a store closed, a system stopped feeding data, or the line genuinely had no sales).

### Breakdown Tables (by Customer Type)

These two tables break down **fulfilled** performance by how the customer purchased:

| Customer Type | Simple meaning | Example |
|---|---|---|
| **Website** | Customer bought directly through the site | 141 orders, 107 fulfilled, ₱2,347,797.32 in fulfilled net sales |
| **Fb** | Customer bought through Facebook | 66 orders, 53 fulfilled |
| **Chatbot** | Customer bought through TAira | 9 orders, 7 fulfilled |
| **Pure Web** | A customer who completed the entire purchase themselves, no human help | 132 orders |
| **CS-Assisted** | A customer who needed a CS agent's help to complete the purchase | 9 orders, but 80% growth — a small number, but growing fast |

**New terms in this table:**
- **Fulfilled Ave Basket**: the average *number of tires* per completed order. Example: Website's 3.36 means the typical completed order includes about 3–4 tires (makes sense — most cars need 4, some just replace 1–2).
- **Fulfilled Avg Ticket**: the average *peso value* per completed order. Example: Website's ₱21,942.03 means a typical completed website order is worth about ₱22K.
- **% Δ**: the percentage change compared to the prior comparison period (shown with the ▲/▼ arrows) — this tells you the *direction* of the trend, not just the current number.

**Example scenario:** CS-Assisted orders grew 80% but Fulfilled Avg Ticket for that group dropped -60.1% (₱8,205.93 vs. previously higher). In simple terms: *many more people are asking a human for help now, but each of those human-assisted sales is worth much less than before.* That's worth investigating — are agents helping with smaller, simpler orders now instead of bigger ones?

---

## Section 3: Installation Partners (IP), Fulfillment Rate & Cancellation Rate

**What it's for:** Tracks the physical network of shops that install the tires, plus two "health check" percentages for the whole operation.

| Metric | Simple meaning | Example |
|---|---|---|
| **Active IP** | Number of installation partner shops currently active and able to take jobs | 126 active shops |
| **New IP** | Shops that just joined/went active this period | 3 new shops added |
| **name / fulfilled orders / active** (table) | Ranks IP shops by how many completed orders they've handled | "GULONG HO" completed 18 orders — the top-performing shop this period |
| **TBF (DEV)** | The peso backlog of Website (DEV channel) orders specifically still waiting to be fulfilled | ₱1,427,281.21 — this is a *channel-specific* slice of the bigger TBF number, not the whole company's backlog |
| **Overall Fulfillment Rate** | Out of everything sold, what % has actually been completed/delivered | 71.49% — meaning about 7 in 10 sold orders are fully done; the rest are still in progress |
| **Cancellation Rate** | What % of orders got cancelled instead of completed | 2.98% — a small but real slice of orders never make it to fulfillment |

**Example scenario:** If Overall Fulfillment Rate is 71.49% and Cancellation Rate is 2.98%, that means roughly 71.49% + 2.98% ≈ 74.5% of orders have a "final" status (either done or cancelled), and the remaining ~25.5% are still sitting in the pipeline (this is the "To Be Fulfilled" backlog). If Fulfillment Rate starts dropping while Cancellation Rate climbs, that's a warning sign that something in the ordering-to-delivery process is breaking down.

---

## Section 4: Tire Category & Brand Performance

**What it's for:** Shows *what kind* of tires are actually selling — by price tier (category) and by brand — so the business can see where demand is shifting.

| Metric | Simple meaning | Example |
|---|---|---|
| **Tire Category** (Premium, Mid Range, Budget, Economy) | Price tier the tire belongs to | Premium had 79 orders and made ₱2,356,344.11 — about 48.95% of all tires sold by volume |
| **Orders / Tires quantity** | Orders and total tire units per category or brand | Premium: 79 orders → 281 tires (some orders bought multiple tires) |
| **% Tires quantity** | What share of ALL tires sold this category/brand represents | Premium = 48.95% of all tires sold — almost half |
| **Net Sales** | Peso revenue from that category/brand | Michelin brand: ₱1,715,026.79 |
| **BRAND1** (Michelin, BFGoodrich, Bridgestone, etc.) | Same idea as tire category, but split by brand instead of price tier | BFGoodrich: 54 orders, up 47.8% — the fastest-growing brand here |

**Example scenario:** Premium tires make up 48.95% of tires sold but are *down* -5.5% in tires quantity and -5.6% in net sales — meaning premium demand is softening. Meanwhile Michelin (a premium brand) is *up* 26.8%/29.2%. That combination suggests: within the premium segment, Michelin specifically is gaining share while premium tires *overall* are shrinking — likely other premium brands (or "Economy," down a sharp -45.6%/-35.6%) are losing the most ground.

---

## Glossary — Terms specific to this dashboard (not already covered in the mancom README)

| Term | Definition |
|---|---|
| **Targets Overview** | This dashboard's name — it's built around comparing actual performance to a sales/gross-profit target, not just reporting daily activity |
| **B2B and Hertz** | A business line for bulk/corporate sales and a partnership channel (Hertz) — separate from regular retail customers |
| **Marketplace** | Sales made through third-party online marketplaces (e.g., Shopee/Lazada-style platforms), not the company's own website |
| **Rapide** | A specific store/franchise brand line, tracked separately from the main Website/FB business |
| **Needed Gross** | How much additional gross profit is required to hit the target for that business line or the company overall. A negative number (e.g., -8.1M) means the company is currently that far short of its target |
| **To Be Fulfilled (this dashboard)** | ⚠️ Unlike the mancom MTD report, here this is a **count of orders** pending, not a peso value — always check which version of "TBF" you're looking at |
| **For Fulfillment Sales** | The peso value equivalent of the "To Be Fulfilled" order count |
| **TBF (DEV)** | The backlog specifically from the Website/DEV channel, as opposed to the company-wide backlog |
| **Overall Fulfillment Rate** | The % of all sold orders that have been successfully completed/delivered |
| **Cancellation Rate** | The % of orders that were cancelled instead of completed |
| **Active IP** | Installation partner shops currently operational and able to accept jobs |
| **New IP** | Installation partner shops that newly went active this period |
| **Fulfilled Ave Basket** | Average number of tires per completed order |
| **Fulfilled Avg Ticket** | Average peso value per completed order |
| **Pure Web** | A customer who self-served the entire purchase with no human assistance |
| **CS-Assisted** | A customer whose purchase involved help from a CS agent |
| **% Δ** | Percentage change vs. the prior comparison period (shown as ▲ green for increase, ▼ red for decrease) — *worth confirming with the dashboard owner exactly which prior period this compares against (previous month, same period last month, etc.)* |
| **Tire Category** | Price/quality tier a tire belongs to: Premium, Mid Range, Budget, or Economy |
| **BRAND1** | The tire manufacturer brand (Michelin, BFGoodrich, Bridgestone, Yokohama, Westlake, Hankook, etc.) |

---

## Key differences vs. the mancom reports (quick reference)

| | Mancom Reports | Targets Overview |
|---|---|---|
| Organized by | Channel (TAira / CS / Website) | Business line (Website/FB / B2B / Marketplace / Rapide) |
| Main question | "How did today/this month go?" | "Are we going to hit our target?" |
| "To Be Fulfilled" meaning | Peso value | **Order count** (peso version is "For Fulfillment Sales") |
| Unique to this report | Needed Gross, Fulfillment Rate, Cancellation Rate, Tire Category/Brand mix | — |
