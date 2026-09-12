# README — Gulong.ph Mancom Reports (Simple Guide)

This explains the 4 reports in plain language, with an example for each metric, plus a glossary of every term used across them.

---

## 1. Daily Dashboard

**What it's for:** A same-day check-up — "did today go okay?" — split by TAira (chatbot), Website, and CS (human agents).

### TAira Performance
| Metric | Simple meaning | Example |
|---|---|---|
| No. of Inquiries | How many people messaged the chatbot today | 81 people chatted with TAira today |
| No. of Moderate | How many of those the bot couldn't handle alone, so it flagged for a human | Out of 81, 13 were too complex for the bot and got flagged |
| No. of Bookings | How many of those inquiries turned into an actual sale, from the bot alone | 0 — the bot closed zero sales today |
| No. of Response | How many flagged (moderate) chats a human actually replied to | Only 6 of the 13 flagged chats got a reply |
| Booking Revenue | Money earned from bot-only bookings | No data, because there were 0 bookings |
| Overall booking revenue | Total money earned across ALL channels combined | ₱276,307.41 total for the day |

### Platform Funnel (Website)
| Metric | Simple meaning | Example |
|---|---|---|
| No. of Total User | How many people visited the website | 9,723 visitors today |
| No. of Searches | How many of them searched for a product | 852 people searched for a tire |
| No. of Organic/Direct User | Visitors who came without clicking a paid ad (they typed the URL or found it on Google for free) | 785 people came in "for free," not through an ad |
| No. of Checkouts | How many reached the payment page | 99 people got to checkout |
| Booked Count | How many actually completed a purchase | 8 people finished buying |
| No. of Organic/Direct Purchase | Of those purchases, how many came from free (non-ad) traffic | 3 of the 8 purchases came from organic visitors |
| Booking Revenue | Money earned from website sales | ₱101,964.29 |

### CS Performance (Human Agents, team total)
Same idea as TAira Performance, but for human agents.
| Metric | Example |
|---|---|
| No. of Inquiries | 321 people messaged a human agent today |
| No. of Moderate | 47 of those needed more attention/follow-up |
| No. of Bookings | 9 turned into sales |
| Booking Revenue | ₱174,343.12 earned |

### TAira Follow-up Funnel
**What it's for:** Chasing the chatbot's flagged leads that never got a reply, before they're considered "lost."

| Metric | Simple meaning | Example |
|---|---|---|
| No. of Followups | How many follow-up messages were sent to old flagged leads | 1 follow-up sent today |
| No. of Customer Responded | How many of those people replied back | 1 person responded |
| No. of Customer Eligible for Followup | How many old leads are still "alive" and can still be followed up | 5 leads are still within the window |
| Lost Customer (7-day window expired) | Leads that went unanswered for 7 days and are now considered gone | 10 leads expired and are lost |
| No. of Book from Follow-ups | How many follow-ups actually turned into a sale | 0 sales from follow-ups today |
| Avg Response Time / Minute | On average, how fast the team responds to a lead | 12 minutes average |

---

## 2. MTD Dashboard (Month-to-Date)

**What it's for:** "Are we on track to hit our monthly sales target?" — zooms out from daily noise to see the bigger monthly trend.

| Metric | Simple meaning | Example |
|---|---|---|
| Booking Sales To Date | Total value of everything sold this month so far (whether delivered yet or not) | ₱4,351,440.00 sold since Sep 1 |
| No. of IPs (Active IPs) | How many installation partner shops are currently active and able to install tires | 126 shops available right now |
| Run Rate Projection | Best guess of total sales by month-end, based on how the month is going so far | Projected to hit ₱12,654,141.44 by Sep 30 |
| Run Rate Projection Minus X% | A more cautious/conservative version of the projection above, in case the optimistic number doesn't hold | ₱11,047,065.48 (the "safer" estimate) |
| For Fulfillment Sales (a.k.a. "TBF" / To Be Fulfilled) | Orders that have been SOLD but not yet DELIVERED/completed | ₱2,360,180.13 worth of orders still being processed |
| Net Fulfilled Sales | Orders that are actually completed/delivered — the "real," done-deal revenue | ₱3,515,129.82 completed so far this month |
| Net Fulfilled Sales Yesterday | Just yesterday's completed orders | ₱383,703.39 completed yesterday |

💡 **Key idea to remember:** *Booking Sales* = everything sold. *Fulfilled Sales* = only the part that's actually been delivered. These are NOT the same number — a sale can be "booked" today but only "fulfilled" days later.

---

## 3. CS Performance Breakdown (Per Agent)

**What it's for:** Same information as the CS card above, but broken down per person, so you can see who's doing well and who needs help.

| Metric | Simple meaning | Example (Aira) |
|---|---|---|
| Inquiries (Today/MTD) | How many people messaged this specific agent | 78 today, 940 this month |
| Bookings (Today/MTD) | How many of those turned into sales | 5 today, 21 this month |
| Booked Revenue | Money from this agent's sales | ₱98,999.55 today |
| Fulfilled (MTD) | How much of this agent's sales have actually been delivered/completed | ₱249,958.12 delivered so far |
| Conversion Rate | Out of everyone who messaged this agent TODAY, what % actually bought | 5 bookings ÷ 78 inquiries = 6.41% |
| To Be Fulfilled | This agent's sales that are still waiting to be delivered | ₱177,103.12 still in progress |

💡 **Key idea to remember:** Conversion Rate here is calculated using TODAY's numbers only, even though it's placed next to the MTD column — don't read it as a monthly rate.

---

## 4. FB Inquiries & Intent

**What it's for:** A name-by-name worklist of chatbot leads that need a human to step in, plus a look at how long leads typically take to become a sale.

### Top numbers (same meaning as TAira Performance card)
No. of Inquiries, Moderates, Replies, Bookings, Reply Rate, Avg Response Time — same definitions as in Section 1.

### Moderate Response Rate table
**What it's for:** A literal to-do list — actual names of customers who were flagged and are still waiting for a human reply.
> Example: "Mich Manuel" messaged at 9:33 PM and was flagged at 10:30 PM, but as of the report, still shows "No CS Reply" — meaning someone needs to message this specific person.

### Moderate Conversion Breakdown MTD
**What it's for:** Looks back at flagged leads from the past and shows how long they actually took to turn into a real sale — used to judge whether we're giving up on leads too early or too late.
| Column | Simple meaning | Example |
|---|---|---|
| booking_day | The date the lead was originally flagged | Jul 1, 2026 |
| day_mode_to_booking | How many days it took from being flagged to becoming a booking | 72 days (Chii Chii took 72 days to convert) |
| average day moderate to booking conversion | The average across all leads | 31.71 days — most flagged leads take about a month to convert |

💡 **Key idea to remember:** Some leads convert same-day, others take over 100 days — this is why the "Lost Customer (7-day window expired)" number in Section 1 is worth questioning: real customers can still buy long after 7 days.

---

## Glossary — All Terms Used in These Reports

| Term | Definition |
|---|---|
| **TAira** | The company's AI chatbot that talks to customers on Facebook/Messenger without human help |
| **CS (Customer Service)** | Human support agents who chat with and assist customers directly |
| **DEV / Platform / Website** | The self-service website where customers browse and check out on their own, no chatbot or agent involved |
| **Inquiry** | Any message/question a customer sends in, on any channel |
| **Moderate** | An inquiry that the chatbot couldn't fully resolve on its own, so it's flagged for a human to step in |
| **Booking** | A confirmed sale/order — the customer has committed to buy |
| **Fulfilled / Fulfillment** | The order has been completed and delivered/installed — not just sold, but actually finished |
| **TBF (To Be Fulfilled)** | Orders that are sold/booked but NOT yet delivered — still in progress. Also called "For Fulfillment Sales" |
| **Booking Revenue** | Total peso value of confirmed sales (whether delivered yet or not) |
| **Net Fulfilled Sales** | Total peso value of orders that have actually been completed/delivered |
| **Booking Sales To Date** | Total value of all sales made so far this month, delivered or not |
| **Run Rate Projection** | A forecast/estimate of what total sales will look like by the end of the month, based on the current pace |
| **Active IPs (Installation Partners)** | Tire shops/partners currently available to install tires for customers who bought online |
| **Conversion Rate** | The percentage of people who inquired that actually ended up buying (Bookings ÷ Inquiries) |
| **Reply Rate** | The percentage of flagged (moderate) chats that actually got a human reply |
| **Response Time** | How fast (in minutes) the team replies to a customer message |
| **Follow-up** | A message sent to re-engage a customer who was flagged but never replied to |
| **Eligible for Follow-up** | A lead that is still within the allowed time window and can still be followed up on |
| **Lost Customer (7-day window expired)** | A flagged lead that went unanswered for 7 days and is now treated as unlikely to convert |
| **Organic/Direct User** | A website visitor who arrived without clicking a paid ad (e.g., typed the URL, searched on Google for free, or came from a bookmark) |
| **Checkout** | The step where a customer is about to pay — the last step before completing a purchase |
| **MTD (Month-to-Date)** | Totals counted from the 1st of the current month up to today |
| **Booked Revenue** | Peso value of an agent's or channel's confirmed sales |
| **manychat_id** | A unique ID number for a customer conversation inside the ManyChat chatbot system |
| **order_status_norm** | The current status of an order (e.g., "processing" = still being worked on, "fulfilled" = completed) |

---

*This README covers only the terms and metrics found in the 4 mancom reports above.*
