# Gulong.ph — Analyst Onboarding: Business & Data Overview

*Read this before opening Looker Studio. Most confusion for new analysts comes from Section 4 (business logic), not the SQL itself.*

---

## 1. The Business — What Gulong.ph Is

Gulong.ph is a **Philippine tire e-commerce platform**, part of Lica Management Inc. / the Lica Group. Customers buy tires online and then get them installed through a network of **installation partners (IPs)** — physical shops around the country that Gulong.ph has recruited and onboarded.

Three ways a customer can transact:
- **Website self-checkout** — customer browses and buys directly on the site (internally called **DEV**)
- **TAira** — an AI/chatbot assistant on ManyChat/Facebook that helps customers and can close bookings (internally called **TAIRA**)
- **Human CS agents** — live agents handling inquiries and bookings (internally called **CS**)

A mobile app (React Native/Expo) is also in active development but isn't yet a live data source you'll see in dashboards.

## 2. What the Analytics Function Does

The analytics work spans the **full stack**: raw data extraction → "gold layer" BigQuery tables → Looker Studio dashboards → ad hoc Python analysis when needed. It covers:

- Sales analytics & reporting (bookings, fulfillment, projections)
- Customer retention / returning-customer analysis
- Marketing attribution (paid search, paid social, organic, chatbot)
- CS & chatbot performance
- Pricing & competitive analysis
- Installation partner network planning
- Product/marketing spec support (acceptance criteria for dev features)

The north star: replace manual Excel/CSV reporting with automated, reliable dashboards that surface decisions, not just numbers.

## 3. Data Sources & Tech Stack

| Layer | Tool | Notes |
|---|---|---|
| Transactional backend | **Laravel / MySQL ("V3")** | Source of truth for orders, branches. Exposed to Looker as data source **"Gulong PH V3 - Order."** Branch table has `active`, `deleted`, `lat`, `lng` columns. |
| Data warehouse | **BigQuery** (project `gulong-chatbot-459723`) | Key datasets: `gulong_core`, `gulong_reporting`, `gulong_backend`, `manychat_data`, `chat_analysis`, `analytics_306667816` (GA4 export) |
| Website analytics | **GA4** | Tables `events_*`, sharded by date (`_TABLE_SUFFIX BETWEEN 'YYYYMMDD' AND 'YYYYMMDD'`). Campaign attribution lives in `session_traffic_source_last_click.manual_campaign.campaign_name`; user identity is `user_pseudo_id`. |
| Chatbot | **ManyChat** (`manychat_data.messages`) | TAira bot is run by agent **Jeanel Co**. Table needs explicit `datetime >=` / `< DATETIME` partition bounds (it's `DATETIME` type, not `TIMESTAMP`). |
| Paid media | **Google Ads** + **Meta Ads Manager** | GA4 was only linked to Google Ads on **June 25, 2026** — anything before that can't be joined/attributed. |
| Dashboards | **Looker Studio** | Connects via custom BigQuery SQL, the native GA4 connector, and the MySQL V3 data source. |
| Ad hoc exports | **Redash** | Used for quick CSV pulls (e.g., `temp_orders`). |

## 4. Core Business Logic — Read This Before Touching a Dashboard

This is where most new-analyst confusion happens:

- **Channel bucketing:** Website = **DEV**, Chatbot = **TAIRA**, everything else (human agents) = **CS**. Almost every dashboard segments by these three.
- **TAira ≠ Aira Garcia.** TAira is the chatbot; Aira L. Garcia is a human CS agent. They're identified in data by `customer_type = 'Chatbot'` or `agent_reporting_group = 'chatbot_jeanel'` — **never** by matching on agent name strings.
- **"TBF" (To-Be-Fulfilled) is NOT a fulfilled-sales metric.** It filters for non-terminal orders that have met payment qualification. Treating TBF as "sales already made" is a recurring mistake across stakeholders — double-check before you present it that way.
- **Canonical source for booked orders:** `gulong_core.orders_booked`.
- **Monthly sales projection formula:**
  `Fulfilled actuals + (TBF × 0.95) + (Run-rate forecast × 0.95)`
  - DEV projections run on **calendar days**; CS/TAira run on **working days** (capped at ~25 selling days/month).
  - Standard naming: *"Fulfilled to Date (Actual)"* / *"Expected Remaining Fulfillment"* / *"Full Month Fulfillment Projection."*

## 5. Campaigns & Paid Media

- **Google Ads structure:** Search campaigns split by brand — BFGoodrich, Michelin, All Brands — plus Performance Max campaigns. Budget strategy has consolidated spend onto the **Michelin sponsored budget**.
- Campaign changes are often pushed via **Google Ads Editor CSV imports**.
- **Attribution caveat:** if you see paid social (Meta) showing zero last-click purchases, it's most likely **broken attribution** (in-app browsers breaking session continuity) rather than the channel genuinely not converting. Always flag this before presenting channel-level CVR comparisons — it's a known trap.
- **Competitive pricing** is tracked against PartsPro, GoGulong, and TireDepot (Michelin SKUs), and there's an internal **GP discount calculator** enforcing a 22% gross-profit floor across Michelin, Apollo, Cooper, BFGoodrich, Arivo, and Linglong.

## 6. Customer Service & Chatbot Ops

- Channels: **TAira** (chatbot), human agents (**Sarah, Rem Reyes, Aira L. Garcia, Rolyn Ang**, plus ManyChat-side **Becca Armstrong**), and website self-checkout.
- Daily funnel reporting runs off `gulong_reporting.t_inquiry_funnel_conversion_daily_v2`.
- Other key views: `v_looker_cs_inquiry_reply_detail_tag_owned` (reply tracking), `v_looker_agent_daily_conversion` (agent conversion).
- Metrics you'll see: reply rate, response time, moderate-intent conversion rate, no-reply chase lists, and agent-level revenue quality (including how TAira handoffs affect agent numbers).

## 7. Installation Partner (IP) Network

- The physical fulfillment layer — shops that install tires after an online purchase.
- **127 IPs** mapped across Metro Manila + 5 provinces, including 10-minute traffic-coverage analysis. **Manila, Caloocan, and Valenzuela** are flagged as critical coverage gaps.
- Recruitment pipeline: **1 scout** (anonymous prospecting calls) feeding **1 recruiter** (calls + site visits to sign up new IPs).

## 8. Other Ongoing Workstreams You May See Referenced

- **Warranty/guarantee dashboard** — program health, claims management, data quality, with "Desisyon" (decision) tags for actionable items.
- **Mobile app** (Expo/React Native) — not a data source yet, but will eventually feed its own analytics.
- **Product/marketing spec docs** — dev-ready acceptance criteria for site features (brand page revamps, promo CMS, GA4 event tagging, SEO).

## 9. Known Looker Studio Gotchas

- The **"Blend Data" toggle** can silently activate and quietly break field visibility — watch for it.
- For segmented views (e.g., TAIRA vs. CS), use **chart-level fixed filters**, not page-level ones.
- **AND vs. OR filter logic** behaves non-intuitively across multiple filter rows — test carefully.
- **Revenue and count metrics need separate axes**, or charts render misleadingly.
- After adding any new data source, hit **"Refresh Fields"** — new fields won't appear otherwise.
- (SQL-side, if you get into the queries): gold-layer views built on top of partitioned tables (like `manychat_data.messages`) can't safely be reused inside CTEs — query the raw table directly with explicit partition bounds instead.

## 10. Practical Checklist for Your First Look at a Dashboard

1. Identify which **channel bucket** (DEV / TAIRA / CS) each chart is filtered to.
2. Check whether a sales metric is **Fulfilled**, **TBF**, or a **Projection** — they are not interchangeable.
3. Note the **date range and partition logic** — calendar days vs. working days matters for CS/TAira numbers.
4. If it's a paid-media chart, check whether the period is before or after **June 25, 2026** (the GA4–Google Ads link date).
5. If something looks off, check for a silently-enabled **Blend Data** toggle before assuming the underlying data is wrong.

---
*Note: Section 2 ("Current state") items reflect where things stood around August–September 2026 — worth a quick verify with the team since dashboards and workstreams move fast here.*
