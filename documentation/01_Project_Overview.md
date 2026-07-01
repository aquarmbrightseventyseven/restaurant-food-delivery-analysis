# 01 — Project overview

## Background

This project delivers a Power BI dashboard for a restaurant food delivery business operating through a call-centre order channel. The business captures granular order-level data — including timestamps at each stage of the delivery pipeline, driver assignments, delivery areas, customer IDs, and financial amounts — and needed a way to turn that raw operational data into actionable commercial and operational insights.

## Objectives

- Monitor order fulfilment and delivery performance in a single view
- Identify bottlenecks in the order pipeline (placement → processing → delivery)
- Evaluate individual driver efficiency and highlight best and worst performers
- Track revenue trends by area, month, hour, and day of week
- Identify top and bottom revenue-generating customers
- Measure customer retention and repeat order behaviour
- Quantify ASAP order demand to inform staffing decisions

## Scope

| In scope | Out of scope |
|----------|-------------|
| Call-centre orders (Jan–Apr 2020) | Online / app orders |
| Three delivery areas: Fremont, Hayward, Union City | Other geographic markets |
| Delivery performance timing | Kitchen preparation time |
| Driver-level efficiency | Vehicle or route optimisation |
| Customer revenue ranking (top and bottom 10) | Individual customer CRM |
| Revenue and order totals | Profit & loss / cost accounting |

## Deliverables

- A two-page interactive Power BI dashboard (Home + Best/Worst Sales)
- A star-schema data model with 10 tables
- 23 DAX measures covering revenue, timing, efficiency, and retention
- This documentation suite

## Key numbers at a glance

| Metric | Value |
|--------|-------|
| Period covered | 1 Jan 2020 – 30 Apr 2020 |
| Total customers | 5,960 |
| Total orders | 72,310 |
| Average delivery time | 2.20 hrs |
| Service efficiency | 0.45 orders/hr |
| Driver efficiency | 1.02 deliveries/hr |
| Average tip | $9.37 |
| ASAP order rate | 79.85% |
| Order completion rate | 77.74% |
| Customer retention rate | 55.78% |

## Tools and technologies

| Tool | Purpose |
|------|---------|
| Power BI Desktop | Data modelling, DAX authoring, dashboard design |
| Power Query (M) | Data ingestion and transformation |
| DAX | Calculated measures |
| GitHub | Version control and documentation |

## Timeline

| Milestone | Date |
|-----------|------|
| Data model created | 7 May 2026 |
| Measures authored | 7 May 2026 |
| Dashboard published | 7 May 2026 |
| Documentation | 28 June 2026 |

## File details

| Property | Value |
|----------|-------|
| File name | `Restaurant_Food_Delivery_Analysis.pbix` |
| Model size | ~15 MB |
| Compatibility level | 1601 |
| Storage mode | Import |
| Connection | localhost (Power BI Desktop) |
