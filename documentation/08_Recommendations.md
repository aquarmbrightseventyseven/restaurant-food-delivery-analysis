# 08 — Business recommendations

## Summary of key numbers

| Metric | Value |
|--------|-------|
| Total revenue | $7,802,409 |
| Total orders | 72,314 |
| ASAP orders | 57,742 (79.9%) |
| Completed orders | 70,330 (97.3%) |
| Refunded orders | 1,984 (2.7%) |
| Revenue lost to refunds | $230,480 |

---

## 1. Double down on Hayward — it is your highest-revenue area

Revenue by delivery area is almost evenly split across three zones, but Hayward leads:

| Area | Revenue | Orders |
|------|---------|--------|
| Hayward | $2,617,915 | 24,085 |
| Fremont | $2,595,408 | 24,229 |
| Union City | $2,589,087 | 24,000 |

Hayward generates the highest revenue with **fewer orders than Fremont**, meaning customers there are spending more per order on average. This suggests a higher-value customer base or a stronger restaurant mix.

**Recommendation:** Prioritise driver availability and service quality in Hayward. Consider running loyalty promotions or upsell campaigns (e.g. meal bundles, larger order incentives) specifically in Hayward to capitalise on the higher spend per customer.

---

## 2. Revenue is growing every month — protect that trajectory

Monthly revenue has grown consistently from January to April:

| Month | Revenue | Orders |
|-------|---------|--------|
| January | $1,368,843 | 18,079 |
| February | $1,870,990 | 18,078 |
| March | $2,174,986 | 18,079 |
| April | $2,387,590 | 18,078 |

Order volumes are **identical each month** (~18,078), but revenue has grown by **74% from January to April**. This means average order value is rising — customers are ordering more expensive items, larger quantities, or adding fewer discounts over time.

**Recommendation:** Investigate what is driving the rising average order value (fewer discounts used, higher-priced menu items, larger group orders) and reinforce those drivers. Ensure driver capacity is scaled ahead of the continued revenue growth curve heading into May and beyond.

---

## 3. Wednesday and Sunday are your two biggest days — staff accordingly

| Day | Revenue | Orders |
|-----|---------|--------|
| Wednesday | $1,206,286 | 11,458 |
| Sunday | $1,173,128 | 10,838 |
| Thursday | $1,164,011 | 10,772 |
| Saturday | $1,161,085 | 10,899 |
| Monday | $1,106,668 | 10,134 |
| Friday | $1,006,753 | 9,051 |
| Tuesday | $984,478 | 9,162 |

Wednesday is the single busiest day — **26% more orders than Tuesday**, the quietest day. Friday and Tuesday are notably weak despite being mid-week and pre-weekend.

**Recommendation:** Ensure maximum driver availability on Wednesdays and Sundays. Investigate why Friday underperforms — this is counterintuitive for a food delivery business and may point to a pricing, marketing, or coverage gap. Consider targeted Friday promotions to lift demand on what should be a natural peak day.

---

## 4. You are an overnight business — most orders arrive between midnight and 3 AM

The busiest hours are not dinner time — they are the early hours of the morning:

| Hour | Orders | Revenue |
|------|--------|---------|
| 1 AM | 12,353 | $1,289,869 |
| 2 AM | 11,657 | $1,220,827 |
| 0 (midnight) | 10,319 | $1,088,960 |
| 3 AM | 8,533 | $899,185 |

Orders then fall sharply through the morning, hitting their lowest point between 12 PM and 2 PM (~200 orders/hour), before slowly recovering through the evening.

**Recommendation:** Shift driver scheduling to weight the overnight hours (midnight–4 AM) heavily. Daytime driver hours (9 AM–3 PM) are largely wasted capacity. If you are paying drivers a flat shift, restructuring to overnight-focused rostering would significantly reduce cost while improving coverage when demand is highest.

---

## 5. The refund rate is low but the revenue loss is material — investigate root causes

| Status | Orders | Revenue |
|--------|--------|---------|
| Completed | 70,330 | $7,571,929 |
| Refunded | 1,984 | $230,480 |

A 2.7% refund rate is operationally low, but **$230,480 in lost revenue** is significant. The average refunded order value is **$116** — higher than it should be if refunds were only for small or simple orders.

**Recommendation:** Filter the dashboard by `IsRefunded = Yes` and cross-reference with `Delivery Area` and `Driver Name` to identify whether refunds are concentrated in a particular zone or with specific drivers. A single driver or a single area accounting for a disproportionate share of refunds would indicate a targeted fix (retraining, route reassignment) rather than a systemic problem.

---

## 6. 80% of orders are ASAP — your business model is on-demand, not pre-scheduled

| Order type | Orders | Revenue |
|------------|--------|---------|
| ASAP | 57,742 | $6,100,660 |
| Scheduled | 14,572 | $1,701,750 |

Nearly 4 in 5 orders are requested for immediate delivery. This means the business cannot smooth demand through advance booking — it must be ready to respond at all times, particularly during the overnight peak identified above.

**Recommendation:** Stop planning driver capacity around scheduled slots. Instead, use the hourly order volume data (see recommendation 4) to deploy drivers in surge patterns aligned to when ASAP demand arrives. Consider a minimum guaranteed response time SLA for ASAP orders as a customer-facing quality commitment.

---

## 7. Your top drivers are nearly twice as efficient as your bottom drivers — close the gap

The most efficient drivers complete approximately **1.7 deliveries per hour worked**, while the least efficient complete fewer than **0.65 deliveries per hour** — a gap of more than 2.5×.

Top 5 drivers by efficiency:

| Driver | Deliveries | Hours worked | Efficiency |
|--------|-----------|-------------|------------|
| Larry | 136 | 79.9 | 1.70 del/hr |
| Irene | 152 | 90.0 | 1.69 del/hr |
| Jada | 196 | 117.8 | 1.66 del/hr |
| Joshua | 152 | 91.8 | 1.66 del/hr |
| Carl | 200 | 123.3 | 1.62 del/hr |

Bottom 5 drivers by efficiency:

| Driver | Deliveries | Hours worked | Efficiency |
|--------|-----------|-------------|------------|
| Erika | 184 | 294.6 | 0.62 del/hr |
| Louis | 184 | 284.7 | 0.65 del/hr |
| Stacy | 152 | 226.4 | 0.67 del/hr |
| Brittany | 160 | 242.0 | 0.66 del/hr |
| Naomi | 152 | 230.6 | 0.66 del/hr |

**Recommendation:** Investigate the bottom-performing drivers before assuming they need retraining. The extremely high hours-worked figures for low-efficiency drivers may indicate a data quality issue (logged-in but not delivering, system not clocking out, etc.). If the data is accurate, pair low-efficiency drivers with a high-efficiency driver for a week to identify whether the gap is route knowledge, system usage, or physical pace.

---

## Priority action plan

| Priority | Recommendation | Expected impact |
|----------|---------------|----------------|
| 🔴 Immediate | Shift driver rosters to overnight (midnight–4 AM) peak | Reduce idle labour cost, improve ASAP response time |
| 🔴 Immediate | Investigate Friday demand gap | Recover ~$220K/year in underperformed revenue |
| 🟡 Short-term | Audit bottom-efficiency driver data | Identify whether issue is data or performance |
| 🟡 Short-term | Refund root-cause analysis by area and driver | Recover up to $230K in annual refund losses |
| 🟡 Short-term | Launch Hayward loyalty or upsell campaign | Increase AOV in highest-value area |
| 🟢 Medium-term | Build a Wednesday/Sunday surge staffing model | Reduce missed orders on peak days |
| 🟢 Medium-term | Monitor monthly revenue trajectory through Q3 | Ensure capacity keeps pace with 74% revenue growth |
