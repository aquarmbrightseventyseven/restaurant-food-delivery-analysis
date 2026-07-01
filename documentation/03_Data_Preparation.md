# 03 — Data preparation

## Source data

The primary source is a single flat call-centre export: **`Call Center_Restaurant Orders`**. This table contains one row per delivery order and includes all timestamps, financial fields, driver info, customer ID, and area.

Supporting lookup and summary tables were derived or ingested alongside the main table.

---

## Tables ingested via Power Query (M)

| Table | Source type | Description |
|-------|------------|-------------|
| `Call Center_Restaurant Orders` | M query / import | Core transaction table — one row per order |
| `DriverSummary` | M query / import | Pre-aggregated driver-level delivery counts and hours worked |
| `DeliveryArea` | M query / import | Distinct delivery area values (lookup) |
| `ASAP` | M query / import | Distinct ASAP flag values with order counts |
| `IsRefunded` | M query / import | Distinct refund status values with counts |
| `Customer Retention` | M query / import | Customer-level order history |
| `Customer Retention Summary` | M query / import | Customer-level aggregation (repeat order flag) |
| `MonthlyRevenue` | M query / import | Monthly revenue and order count rollup |
| `Date` | M query / import | Date dimension |
| `Day week` | M query / import | Day-of-week dimension with sort order |

---

## Key transformations applied

### `Call Center_Restaurant Orders`

| Column | Transformation |
|--------|---------------|
| `Date` | Parsed to date type |
| `Time customer placed order` | Parsed to time type |
| `Time Order Placed at Restaurant` | Parsed to time type |
| `Time Driver Arrived at Restaurant` | Parsed to time type |
| `Delivery time` | Parsed to time type |
| `OrderPlacement` | Calculated: seconds from customer call to restaurant receipt |
| `OrderProcessing` | Calculated: seconds from restaurant receipt to driver arrival |
| `OrderDelivery` | Calculated: seconds from driver pickup to delivery |
| `Time Taken for Delivery Process` | Calculated: total end-to-end seconds |
| `Hour` | Extracted from order time for hourly analysis |
| `Month Name` | Extracted text month name, sorted by `Month` number |
| `Month` | Extracted month number (for sort) |
| `Day of Week` | Extracted numeric day (1=Monday) |
| `Day Name` | Extracted text day name |
| `Amount` | Derived: Sub Total + Delivery fee + Service fee − Discount + Tip − Refunded amount |
| `IsRefunded` | Text flag: `"Yes"` / `"No"` |

### `DriverSummary`

Pre-aggregated at source. Contains `Driver Name`, `Count` (deliveries), `DriverSecondsWorked`, and a pre-calculated `DriverEfficiency` column. The DAX measure recalculates efficiency dynamically.

### `MonthlyRevenue`

Rollup of `Amount` and order `Count` by `Month Name` / `Month` number. Used to drive the monthly revenue slicer and dynamic title.

### `Day week`

Contains `Day Name` and `Day of Week` sort column. Used for the day-of-week slicer and dynamic title.

---

## Data quality notes

- All storage mode is **Import** — data is a snapshot at refresh time.
- The model was last refreshed on **7 May 2026**.

