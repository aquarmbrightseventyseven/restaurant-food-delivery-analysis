# 02 — Business requirements

## Stakeholder questions

The dashboard was designed to answer the following business questions:

### Revenue & orders
- What is the total revenue and order count across the period?
- How does revenue trend by month — is the business growing?
- How does revenue and order volume vary by hour of day?
- How does revenue break down by delivery area?
- Which days of the week generate the most and least revenue?

### Delivery performance
- What is the average end-to-end delivery time?
- How long does each stage take — placement, processing, and delivery?
- Which delivery areas have the longest average order times?

### Driver performance
- How many deliveries does each driver complete per hour worked?
- Who are the top 10 and bottom 10 performing drivers?

### Customer value
- Who are the top 10 customers by total revenue?
- Who are the bottom 10 customers by total revenue?
- Which customers place the most orders?

### Order quality & type
- What percentage of orders are completed without a refund?
- What share of orders are ASAP vs scheduled?
- What is the customer retention rate?

---

## KPIs and actual values

| KPI | Measure | Value |
|-----|---------|-------|
| Total customers | `Total Customers` | 5,960 |
| Total orders | `order total` | 72,310 |
| Average delivery time | `Average Delivery Time` | 2.20 hrs |
| Service efficiency | `Service Efficiency` | 0.45 orders/hr |
| Driver efficiency | `Driver Efficiency` | 1.02 deliveries/hr |
| Average tip | — | $9.37 |
| ASAP order % | `ASAP yes percent` | 79.85% |
| Order completion % | `completion rate` | 77.74% |
| Customer retention % | `customer turnout` | 55.78% |

---

## Report audience

| Audience | Primary interest |
|----------|----------------|
| Operations manager | Delivery times, driver efficiency, completion rate, hourly demand |
| Commercial / revenue team | Revenue by area, month, day; top customers |
| Customer experience team | Retention rate, refund rate, bottom-revenue customers |
| Senior leadership | High-level KPIs, growth trajectory, best/worst performers |

---

## Filtering requirements

Users can filter all visuals using:

| Filter | Field | Location |
|--------|-------|----------|
| Date range | `Date` | Date slider — both pages (header) |
| Delivery area | `DeliveryArea[Delivery Area]` | Dropdown slicer — both pages (header) |
| Month name | `MonthlyRevenue[Month Name]` | Dropdown slicer — both pages (header) |

Dynamic titles update automatically when filters are applied, driven by DAX title measures (`location title`, `monthly title`, `day title`, `locatio time title`).
