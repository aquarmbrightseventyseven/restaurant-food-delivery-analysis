# 06 — Dashboard explanation

The dashboard has two pages navigated via the **Navigator** panel on the left side of each page.

---

## Header (both pages)

A gold header bar appears on both pages and contains:

- **Title:** Restaurant Delivery
- **Date range slider** — filters all visuals to a selected date range (default: 1 Jan 2020 – 30 Apr 2020)
- **Delivery Area dropdown** — filters by area (All / Fremont / Hayward / Union City)
- **Month Name dropdown** — filters by month (All / January / February / March / April)

---

## KPI strip (both pages)

A row of six headline cards sits below the header on both pages, always visible regardless of which page is active:

| Card | Measure | Value (all data) |
|------|---------|-----------------|
| Total Customers | `Total Customers` | 5.96K |
| Total Order Placement | `order total` | 72.31K |
| Average Delivery Time | `Average Delivery Time` | 2.20 hrs |
| Service Efficiency | `Service Efficiency` | 0.45 orders/hr |
| Driver Efficiency | `Driver Efficiency` | 1.02 deliveries/hr |
| Average Tip | — | $9.37 |

Three gauge charts also appear on the right of this strip:

| Gauge | Measure | Value |
|-------|---------|-------|
| ASAP Order % | `ASAP yes percent` | 79.85% |
| Order Completed % | `completion rate` | 77.74% |
| Customer Retention % | `customer turnout` | 55.78% |

---

## Page 1 — Home

This page covers overall operational and revenue performance.

### Navigator panel (left)
Two navigation buttons:
- **Home** — current page
- **Best/Worst Sales** — navigates to Page 2

### Sales by Month (clustered column chart)
Dual-axis chart showing `Revenue` (dark blue bars) and `Number of Orders` (light blue bars) by month, sorted January → April.

| Month | Revenue | Orders |
|-------|---------|--------|
| January | 1.37M | 18,079 |
| February | 1.87M | 18,078 |
| March | 2.17M | 18,079 |
| April | 2.39M | 18,078 |

Revenue grows each month while orders remain constant — average order value is increasing.

### Sales by Hour (area chart)
Order volume plotted across the 24-hour clock. Peak demand is concentrated in the early hours of the morning:

- **1 AM** — 10.4K orders (highest)
- **2 AM** — 8.4K orders
- **3 AM** — 7.1K orders
- Daytime hours (8 AM–3 PM) are the quietest (0.1K–0.8K orders)
- A secondary evening ramp begins around 8 PM

### Average Order Time by Location (stacked bar chart)
Shows average minutes for each pipeline stage broken down by delivery area. All three areas have nearly identical times — each stage averages ~40–42 minutes across Fremont, Hayward, and Union City.

| Area | Placement | Processing | Delivery | Total |
|------|-----------|-----------|---------|-------|
| Fremont | 47.36 min | 40.24 min | 58.72 min | 146.32 min |
| Hayward | 47.26 min | 42.31 min | 57.47 min | 147.00 min |
| Union City | 46.10 min | 40.36 min | 59.35 min | 145.81 min |



### Sales by Location (clustered column chart)
Revenue and order count per delivery area:

| Area | Revenue | Orders |
|------|---------|--------|
| Fremont | $2.05M | 24,229 |
| Hayward | $2.04M | 24,085 |
| Union City | $2.01M | 24,000 |

All three areas are closely matched. Fremont leads on order volume; Hayward leads on revenue per order.

### Daily Sales Trend (line + column chart)
Revenue (line) and order count (columns) by day of week:

| Day | Revenue | Orders |
|-----|---------|--------|
| Sunday | $1.17M | 10.8K |
| Monday | $1.11M | 10.1K |
| Tuesday | $0.98M | 9.2K |
| Wednesday | $1.21M | 11.5K |
| Thursday | $1.16M | 10.8K |
| Friday | $1.01M | 9.1K |
| Saturday | $1.16M | 10.9K |

Wednesday is the peak day. Tuesday and Friday are the two quietest days.

---

## Page 2 — Best / Worst Sales

This page focuses on customer value ranking and driver performance.

### Navigator panel (left)
- **Home** — navigates to Page 1
- **Best/Worst Sales** — current page (highlighted)

### Top 10 Revenue by Customer (bar chart)
Ranks the top 10 customers by total revenue spent. The highest-value customer (#1077359) generated $6.24K. A tooltip on hover shows Customer ID, Sum of Revenue, Percent of first, and Percent of previous.

| Rank | Customer ID | Revenue |
|------|------------|---------|
| 1 | 1077359 | $6.24K |
| 2 | 1059088 | $5.99K |
| 3 | 1078645 | $5.50K |
| 4 | 1148787 | $5.45K |
| 5 | 1080979 | $5.36K |
| 6 | 1172573 | $5.19K |
| 7 | 1028300 | $5.02K |
| 8 | 1005835 | $5.02K |
| 9 | 1112405 | $4.88K |
| 10 | 1097734 | $4.46K |

### Bottom 10 Revenue by Customer (bar chart)
Ranks the 10 lowest-revenue customers. The lowest (#1001632) generated $168.12.

### Top 10 Customers by order count (bar chart)
Ranks the top 10 customers by number of orders placed. Customer #1175554 placed 37 orders — the highest of any customer.

### Best Performing Drivers (bar chart)
Top 10 drivers ranked by deliveries per hour worked:

| Driver | Efficiency (del/hr) |
|--------|-------------------|
| Larry | 1.70 |
| Irene | 1.69 |
| Jada | 1.66 |
| Joshua | 1.66 |
| Carl | 1.62 |
| Lacey | 1.59 |
| Robin | 1.57 |
| Ariana | 1.55 |
| Catherine | 1.54 |
| Michael | 1.52 |

### Poor Performing Drivers (bar chart)
Bottom 10 drivers ranked by deliveries per hour worked:

| Driver | Efficiency (del/hr) |
|--------|-------------------|
| Adam | 0.71 |
| Louise | 0.70 |
| Destiny | 0.70 |
| Kari | 0.69 |
| Jade | 0.67 |
| Stacy | 0.67 |
| Brittany | 0.66 |
| Naomi | 0.66 |
| Louis | 0.65 |
| Erika | 0.62 |

The gap between the best driver (Larry, 1.70) and the worst (Erika, 0.62) is 2.7× — a significant efficiency spread.
