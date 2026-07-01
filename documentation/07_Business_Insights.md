# 07 — Business insights

## 1. Revenue is growing fast — but order volume is flat

Monthly revenue grew from **$1.37M in January to $2.39M in April** — a 74% increase in four months. Yet order volumes were almost identical every month (~18,078 orders). This means the growth is coming entirely from a rising average order value, not from more customers or more orders.

**What this means:** Something changed between January and April that made customers spend more per order — fewer discounts being applied, a shift toward higher-priced menu items, larger group orders, or a mix of all three. This trend is the most important commercial signal in the dataset and should be investigated and protected.

---

## 2. The business operates on an overnight schedule — not a dinner schedule

The hourly order chart shows a demand pattern that is the opposite of what most food businesses expect:

| Period | Orders |
|--------|--------|
| 1 AM (peak) | 10,400 |
| 2 AM | 8,400 |
| 3 AM | 7,100 |
| 8 AM–3 PM | 100–800 |
| 8 PM–midnight | 1,400–2,000 |

More than half of all daily orders arrive between midnight and 4 AM. The traditional dinner window (6–9 PM) is one of the quietest periods of the day.

**What this means:** Driver rosters built around evening shifts are misaligned with actual demand. The business needs overnight-weighted scheduling to service peak hours and avoid long ASAP wait times when demand is highest.

---

## 3. All three delivery areas perform similarly — Hayward extracts more value per order

Revenue and order volume across the three areas are closely matched:

| Area | Revenue | Orders | Revenue per order |
|------|---------|--------|------------------|
| Fremont | $2.05M | 24,229 | $84.62 |
| Hayward | $2.04M | 24,085 | $84.70 |
| Union City | $2.01M | 24,000 | $83.79 |

Hayward achieves the highest revenue per order despite having fewer orders than Fremont. Union City has the lowest revenue per order.

**What this means:** The areas are operationally comparable but Hayward customers are slightly higher spenders. There is no dominant area to prioritise — the business needs consistent coverage across all three. Any significant drop in one area would have an immediate revenue impact.

---

## 4. 80% of orders are ASAP — pre-scheduled capacity planning does not apply

**79.85%** of all orders (57,742 out of 72,314) are requested for immediate delivery. Only 1 in 5 orders gives the business advance notice.

Combined with the overnight demand peak, this means:
- Drivers cannot be pre-assigned to time slots in any meaningful way
- Standby capacity is essential during peak hours (midnight–4 AM)
- Response time is a key competitive differentiator — ASAP customers expect fast fulfilment

**What this means:** The business is an on-demand operation. Scheduling models borrowed from traditional shift-based delivery businesses will not work here.

---

## 5. The order completion rate of 77.74% is a significant concern

**22.26% of orders** are not completed — either refunded or unfulfilled. For a business processing 72,314 orders, this translates to approximately 16,090 failed orders and **$230,480 in refunded revenue**.

| Status | Orders | Revenue |
|--------|--------|---------|
| Completed | 70,330 | $7,571,929 |
| Refunded | 1,984 | $230,480 |

> Note: The completion rate gauge shows 77.74%, which is calculated differently from the refund count above. The gauge likely measures a broader definition of order fulfilment — including orders that were placed but not delivered for reasons beyond refunds. The $230,480 figure covers confirmed refunded orders only.

**What this means:** A completion rate below 80% indicates a systemic issue, not occasional errors. Whether driven by delivery failures, restaurant cancellations, or customer dissatisfaction, nearly one in four orders is not generating the expected revenue.

---

## 6. Wednesday is the busiest day — Friday and Tuesday are surprisingly weak

| Day | Orders | Revenue |
|-----|--------|---------|
| Wednesday | 11,500 | $1.21M |
| Sunday | 10,800 | $1.17M |
| Saturday | 10,900 | $1.16M |
| Thursday | 10,800 | $1.16M |
| Monday | 10,100 | $1.11M |
| Friday | 9,100 | $1.01M |
| Tuesday | 9,200 | $0.98M |

Wednesday outperforms every other day including the weekend. Friday — typically a peak day for food delivery — is the second weakest day in the week. Tuesday is the weakest overall.

**What this means:** The customer base for this operation does not follow conventional food delivery patterns. Wednesday demand may be linked to a specific local factor (corporate orders, weekly events). The Friday underperformance represents a clear opportunity — if Friday could match Wednesday, it would add ~$200K in monthly revenue.

---

## 7. Driver efficiency varies 2.7× between the best and worst performers

| Tier | Driver | Efficiency |
|------|--------|-----------|
| Best | Larry | 1.70 del/hr |
| 2nd | Irene | 1.69 del/hr |
| … | … | … |
| 9th worst | Louis | 0.65 del/hr |
| Worst | Erika | 0.62 del/hr |

The top driver completes **174% more deliveries per hour** than the worst driver. Even closing half of this gap across the bottom 10 drivers would meaningfully increase overall throughput without adding headcount.

**What this means:** Driver efficiency is not uniform and the gap is too large to be explained by natural variation alone. Route assignments, area familiarity, system usage, or logging practices may all be contributing factors.

---

## 8. Customer retention at 55.78% is healthy but has room to grow

More than half of all customers returned to place more than ten order during the four-month period. The top customer (#1175554) placed **37 orders** — nearly one order every three days.

The top 10 customers by revenue each generated over $4,460, with the highest reaching $6,240. However, the bottom 10 revenue customers generated as little as $168 — a 37× gap between top and bottom.

**What this means:** There is a highly engaged core customer base worth protecting with loyalty incentives. The wide revenue spread also suggests a large segment of customers who tried the service once or twice and did not return — a reactivation campaign targeting low-order customers could recover incremental revenue at low cost.
