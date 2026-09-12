# README — KPI Monitoring: CS | Sales Agent Performance

**Note:** This is a third, distinct report from the mancom dashboards and the Targets Overview dashboard covered in earlier READMEs. This one scores **individual sales agents** (plus DEV/Website and TAira, treated like "agents" for comparison) against **personal targets**, with color-coded grading.

---

## What is this dashboard for?

**Simple purpose:** This dashboard answers: *"Who on the CS team is hitting their number, who's falling behind, and exactly where is each person's revenue coming from?"*

Where the Targets Overview dashboard asked "is the business line on track," this one zooms in one level further — to the **person**. It's built for performance management: coaching conversations, recognizing top performers, and catching someone who's quietly underperforming before it shows up in the company-wide numbers.

---

## Section 1: Header KPIs + Target Achievement/CS Table

**What it's for:** The main scoreboard. Company-wide totals up top, then a person-by-person breakdown below so you can see exactly who's contributing what.

### Header KPIs

| Metric | Simple meaning | Example |
|---|---|---|
| **Orders** | Total orders across every agent, this period | 220 orders (Sep 1–12) |
| **Order Net Value** | Total peso value of all those orders combined | ₱4.65M |
| **Targets** | The full-period sales goal for the whole group | ₱12.76M |
| **Booked/High Conversion Rate** | Currently blank ("-") | Not yet populated for this view |

⚠️ **Important:** Order Net Value (₱4.65M) and Targets (₱12.76M) look like they should be compared directly, but the Targets figure is the **full period's** goal — don't divide these two and assume that's "% achieved," since the table below shows the real % Target is actually **88.9%** (Grand total row), calculated against a *smaller* number (₱5,237,091.21), not the ₱12.76M shown up top. These are two different target figures serving two different scopes — worth confirming with the dashboard owner which one represents the "real" period target.

### Target Achievement/CS Table

**What it's for:** Ranks every agent (plus DEV and TAira) by how close they are to their individual sales goal — the color coding lets a manager scan it in two seconds.

| Color | Simple meaning |
|---|---|
| 🟩 Green | Excellent — met or exceeded target |
| 🟦 Blue | Good |
| 🟨 Yellow | Average |
| 🟥 Red | Bad — significantly behind target |

| Column | Simple meaning | Example |
|---|---|---|
| **No. of Orders** | How many orders this agent closed | DEV: 135 orders |
| **Net Sales** | Peso value of those orders | DEV: ₱3,057,757.05 |
| **Targets** | This agent's personal sales goal for the period | DEV: ₱2,799,999.96 |
| **% Target** | Net Sales ÷ Target — the real "did they hit their number" answer | DEV: 109.2% (green — beat the goal) |

**Example scenario:** DEV is at 109.2% (green) while Sarah Mae is at 38.9% (red) — a huge gap. But notice their targets are also very different sizes: DEV's target is ₱2.8M, while every human agent's target is the same ₱523,832.65. **This means targets are set differently per role/channel, not applied equally** — so it wouldn't be fair to compare raw peso sales between DEV and a human agent. The **% Target** column exists specifically to make that comparison fair, since it normalizes everyone against their own personal goal.

**Why DEV and TAira are in a "Sales Agent" table:** They aren't people, but they're tracked the same way so leadership can compare channel performance (Website, Chatbot) side-by-side with human agent performance, all on one scoreboard.

---

## Section 2: Daily Orders to Target

**What it's for:** The same "hitting target or not" question, but sliced by day instead of by person — this exists to catch a bad day immediately, rather than only discovering a problem once the whole period is already over and it's too late to fix.

| Metric | Simple meaning | Example |
|---|---|---|
| **Net Sales of VAT** | That day's actual sales | Sep 7: ₱764,603.93 |
| **Targets** | That day's expected sales goal | ₱454,887.08 on most days |
| **% Achievement (Net)** | Sales ÷ Target for that one day | Sep 7: 168.09% — a great day, well above target |
| **Fulfilled Amount (NET)** | How much of that day's sales has actually been delivered/installed so far | Sep 12 shows ₱0 — makes sense, since Sep 12 just happened and installs take time to process |

**Example scenario:** Sep 5 (43.57%) and Sep 12 (66.72%) are both red/underperforming days, while Sep 7 (168.09%) and Sep 10 (97.35%) are strong. If red days start clustering together (e.g., every weekend, or every time a certain agent is off), that pattern is worth investigating — a single bad day is noise, but a repeating pattern is a real signal.

💡 **Note:** Sep 6's target (₱233,333.33) is noticeably lower than every other day's (₱454,887.08) — likely a shorter business day (e.g., a holiday or half-day) rather than a data error. Worth confirming, but the daily target itself flexes to reflect expected business volume for that specific day.

---

## High Intent Daily Conversion Rate

**What it's for:** Measures how well each agent converts their *best* leads — the ones flagged as very likely to buy — into actual sales. This exists because raw order counts don't tell you if an agent is good at closing strong leads specifically, versus just getting lucky with volume.

| Term | Simple meaning |
|---|---|
| **High Intent** | A lead the system judged as showing strong buying signals |
| **Orders from Chat** | How many actual orders came from chat conversations that day |
| **Conversion Rate** | Of the High Intent leads, what % became actual orders |
| **Target Conversion Rate** | The goal for that conversion rate |

**Example:** On Sep 11, Aira had 4 "Orders from Chat" but "High Intent" shows 0. Since this column reads 0 across every single agent and every date, that's a sign the High Intent tagging may not be feeding into this dashboard yet, rather than every lead genuinely being low-intent — worth flagging to whoever maintains the lead-scoring pipeline before drawing conclusions from this section.

---

## Section 3: Customer Type/Source per CS

**What it's for:** Breaks down *where* each agent's orders actually come from — because "Agent X closed 22 orders" doesn't say whether those came from a Facebook chat, a phone call, or a chatbot handoff. This matters for two reasons: coaching (is this agent strong on chat, or on calls?) and channel strategy (which entry point is driving the most volume company-wide?).

| Column | Simple meaning | Example |
|---|---|---|
| **Fb / Chat** | Orders that started as a Facebook message | Remylyn: 22 orders, 85 tires, ₱405.14K |
| **Fb / Call** | Orders that started as a phone call sourced from Facebook | Aira: 4 orders, ₱82.42K |
| **Chatbot / Chatbot** | Orders handled entirely by TAira, no human involved | TAira: 10 orders, ₱285K |
| **Website / Chat** | Orders that came through website live chat | Remylyn: 1 order, ₱10.81K |

**Example scenario:** TAira shows activity *only* in the Chatbot/Chatbot column and zero everywhere else — which makes sense, since a bot can't take a phone call. This confirms the channel-attribution logic is working as expected: a bot only ever gets credit for bot-native conversations.

### The row-level detail table (below the summary)

**What it's for:** This is the underlying raw data the summary numbers are built from — one row per actual order. It exists as an audit trail: if a summary number ever looks wrong, this is where you'd drill down to find the specific order responsible.

| Term | Simple meaning | Example |
|---|---|---|
| **Sta. (Status)** | The order's current stage | "Proc." = Processing, "Pen." = Pending, "INSTALL..." = installation-related status |
| **many_c... (manychat_id)** | A unique ID tied to the customer's chat conversation | Used to trace an order back to the actual chat log if needed |
| **GP (Gross Profit)** | The peso profit made on that specific order, after cost | ₱2.7K on one Duratu order |
| **disc. (Discount)** | Any discount applied to the order | Most rows show 0; one row shows 100 (a voucher-based discount) |
| **voucher** | Whether a promo/voucher code was used | A blank/0 means no voucher was used on that order |

---

## Glossary — Terms specific to this dashboard

| Term | Definition |
|---|---|
| **KPI Monitoring** | The category this dashboard belongs to — focused on tracking individual performance metrics (KPIs) against goals, as opposed to general activity reporting |
| **Target** | The sales goal set for a specific agent, channel, or day |
| **% Target / % Achievement** | Actual sales divided by the target for that same scope (per agent or per day) — the true "did we hit the number" metric |
| **Color grading (Green/Blue/Yellow/Red)** | A visual shortcut for performance tier: Green = Excellent, Blue = Good, Yellow = Average, Red = Bad |
| **High Intent** | A lead flagged by the system as showing strong signals of being ready to buy |
| **Orders from Chat** | Orders that originated from a chat conversation (as opposed to a call or other channel) |
| **customer_source** | Where the customer's conversation originated (e.g., Fb, Website, Chatbot) |
| **customer_type** | How the customer engaged (e.g., Chat, Call, Chatbot) |
| **DEV** | The website channel, tracked here like an "agent" for comparison against human CS agents |
| **TAira** | The AI chatbot, also tracked like an "agent" in this table |
| **Fulfilled Amount (NET)** | How much of a given day's sales has actually been delivered/completed |
| **GP (Gross Profit)** | Profit earned on an order after subtracting cost |
| **Sta. (Status)** | Shorthand column for the order's current processing stage |

---

## How this report differs from the other two (quick reference)

| | Mancom Reports | Targets Overview | KPI Monitoring (this one) |
|---|---|---|---|
| Organized by | Channel (TAira/CS/Website) | Business line (Website/FB, B2B, Marketplace, Rapide) | **Individual agent** (plus DEV/TAira as comparison rows) |
| Main question | "How did today/this month go?" | "Are we going to hit our target?" | "**Who** is hitting their personal target?" |
| Unique to this report | — | Needed Gross, Fulfillment Rate, Cancellation Rate, Tire mix | **Color-coded grading, per-agent targets, per-agent channel-source breakdown, High Intent conversion** |

**Key thing to double-check with the dashboard owner:** the header "Targets: 12.76M" and the table's Grand Total target (₱5,237,091.21, giving 88.9%) don't match — they appear to be two different target scopes shown side-by-side without labeling which is which. Worth clarifying before quoting either figure in a mancom presentation.
