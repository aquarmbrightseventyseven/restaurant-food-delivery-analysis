# 04 — Data model

## Schema type

The model follows a **star schema** pattern. `Call Center_Restaurant Orders` is the central fact table. All other business tables are dimension or summary tables connected to it via one-to-many relationships.

---

## Tables

### Fact table

#### `Call Center_Restaurant Orders`
Core transaction table. One row per delivery order.

| Column | Data type | Description |
|--------|-----------|-------------|
| Date | Date/Time | Date the order was placed |
| Time customer placed order | Date/Time | Timestamp when customer called |
| Time Order Placed at Restaurant | Date/Time | Timestamp when order was sent to restaurant |
| Time Driver Arrived at Restaurant | Date/Time | Timestamp when driver arrived for pickup |
| Delivery time | Date/Time | Timestamp of final delivery |
| Driver ID | Integer | Unique driver identifier |
| Driver Name | Text | Driver's name |
| Restaurant ID | Integer | Unique restaurant identifier |
| Customer ID | Integer | Unique customer identifier |
| Delivery Area | Text | Geographic delivery zone |
| ASAP | Text | "Yes" / "No" — immediate delivery requested |
| Sub Total | Decimal | Order subtotal before fees |
| Delivery fee | Decimal | Fee charged for delivery |
| Service fee | Decimal | Platform service fee |
| Discount | Decimal | Discount applied |
| Tip | Decimal | Tip amount |
| Refunded amount | Decimal | Amount refunded (0 if not refunded) |
| IsRefunded | Text | "Yes" / "No" — whether order was refunded |
| Amount | Decimal | Net order value (Sub Total + fees − Discount + Tip − Refund) |
| OrderPlacement | Integer | Seconds: customer call → restaurant receipt |
| OrderProcessing | Integer | Seconds: restaurant receipt → driver arrival |
| OrderDelivery | Integer | Seconds: driver pickup → delivery |
| Time Taken for Delivery Process | Decimal | Total end-to-end seconds |
| Hour | Integer | Hour of day order was placed |
| Month Name | Text | Month name (e.g. "January") |
| Month | Integer | Month number for sorting |
| Day of Week | Integer | Day number (for sort) |
| Day Name | Text | Day name (e.g. "Monday") |

---

### Dimension tables

#### `DriverSummary`
| Column | Data type | Description |
|--------|-----------|-------------|
| Driver Name | Text | Driver name (join key) |
| Count | Integer | Total deliveries completed |
| DriverSecondsWorked | Decimal | Total seconds on duty |
| DriverEfficiency | Decimal | Pre-calculated efficiency score |

#### `DeliveryArea`
| Column | Data type | Description |
|--------|-----------|-------------|
| Delivery Area | Text | Area name (join key) |
| Count | Integer | Total orders in this area |

#### `ASAP`
| Column | Data type | Description |
|--------|-----------|-------------|
| ASAP | Text | "Yes" / "No" (join key) |
| Count | Integer | Total orders with this flag |

#### `IsRefunded`
| Column | Data type | Description |
|--------|-----------|-------------|
| IsRefunded | Text | "Yes" / "No" (join key) |
| Count | Integer | Total orders with this status |

#### `Customer Retention`
| Column | Data type | Description |
|--------|-----------|-------------|
| Customer ID | Integer | Customer identifier |
| Date | Date/Time | Order date |
| Count | Integer | Orders on that date |

#### `Customer Retention Summary`
| Column | Data type | Description |
|--------|-----------|-------------|
| Customer ID | Integer | Customer identifier (join key) |
| Revenue | Decimal | Lifetime revenue from customer |
| Count | Integer | Total orders placed |
| Custom | Integer | Flag: 1 if repeat customer |

#### `MonthlyRevenue`
| Column | Data type | Description |
|--------|-----------|-------------|
| Month Name | Text | Month name |
| Amount | Decimal | Total revenue for the month |
| Count | Integer | Total orders for the month |
| Month | Integer | Month number (sort key) |

#### `Day week`
| Column | Data type | Description |
|--------|-----------|-------------|
| Day Name | Text | Day name |
| Day of Week | Integer | Day number (sort key) |
| Count | Integer | Total orders on that day |
| Amount | Decimal | Total revenue on that day |

#### `Date`
| Column | Data type | Description |
|--------|-----------|-------------|
| Date | Date/Time | Calendar date |

---

## Relationships

All relationships are **active**, **one-to-many**, **single direction** (dimension → fact).

| From table (many) | From column | To table (one) | To column |
|-------------------|-------------|----------------|-----------|
| Call Center_Restaurant Orders | Driver Name | DriverSummary | Driver Name |
| Call Center_Restaurant Orders | Delivery Area | DeliveryArea | Delivery Area |
| Call Center_Restaurant Orders | ASAP | ASAP | ASAP |
| Call Center_Restaurant Orders | IsRefunded | IsRefunded | IsRefunded |
| Call Center_Restaurant Orders | Customer ID | Customer Retention Summary | Customer ID |
| Call Center_Restaurant Orders | Month | MonthlyRevenue | Month |
| Call Center_Restaurant Orders | Date | LocalDateTable (auto) | Date |
| Customer Retention | Customer ID | Customer Retention Summary | Customer ID |
| Customer Retention | Date | LocalDateTable (auto) | Date |
| Date | Date | LocalDateTable (auto) | Date |

> Power BI auto-generates hidden `LocalDateTable` tables for date columns. These are system tables and are not user-visible.

---

## Model diagram (text representation)

```
[DriverSummary] ─────────────────────────────────────────┐
[DeliveryArea]  ─────────────────────────────────────────┤
[ASAP]          ─────────────────────────────────────────┤
[IsRefunded]    ───────────────── [Call Center_Restaurant Orders] ── [Customer Retention Summary] ── [Customer Retention]
[MonthlyRevenue]─────────────────────────────────────────┤
[Date]          ─────────────────────────────────────────┘
[Day week]      (standalone slicer table)
```
