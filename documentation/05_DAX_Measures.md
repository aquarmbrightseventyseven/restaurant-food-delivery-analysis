# 05 — DAX measures

All 23 measures are documented below, grouped by category.

---

## Revenue & orders

### `Revenue`
**Table:** ASAP  
**Purpose:** Total net revenue across all orders.

```dax
Revenue = SUM('Call Center_Restaurant Orders'[Amount])
```

---

### `order total`
**Table:** ASAP  
**Purpose:** Total number of orders. Sums the `Count` column from the ASAP dimension table to get an overall order count.

```dax
order total = SUM(ASAP[Count])
```

---

### `order total percent`
**Table:** ASAP  
**Purpose:** Percentage of orders (always 100% — used as a base reference for relative comparisons in visuals).

```dax
order total percent = [order total] * 100 / [order total]
```

---

## Order type

### `ASAP yes`
**Table:** ASAP  
**Purpose:** Count of orders where the customer requested immediate (ASAP) delivery.

```dax
ASAP yes =
CALCULATE(
    COUNTROWS('Call Center_Restaurant Orders'),
    'Call Center_Restaurant Orders'[ASAP] = "Yes"
)
```

---

### `ASAP yes percent`
**Table:** ASAP  
**Purpose:** Percentage of total orders that were ASAP requests.

```dax
ASAP yes percent = (ASAP[ASAP yes] * 100) / [order total]
```

---

## Order quality

### `completed`
**Table:** IsRefunded  
**Purpose:** Count of orders that were not refunded (successfully completed).

```dax
completed =
CALCULATE(
    COUNTROWS('Call Center_Restaurant Orders'),
    'Call Center_Restaurant Orders'[IsRefunded] = "No"
)
```

---

### `completion rate`
**Table:** IsRefunded  
**Purpose:** Percentage of orders completed without a refund.

```dax
completion rate = [completed] * 100 / [order total]
```

---

## Delivery timing

### `time taken`
**Table:** Call Center_Restaurant Orders  
**Purpose:** Total delivery time across all orders, in hours.

```dax
time taken = SUM('Call Center_Restaurant Orders'[Time Taken for Delivery Process]) / 3600
```

---

### `Average Delivery Time`
**Table:** Call Center_Restaurant Orders  
**Purpose:** Mean end-to-end delivery duration per order, in hours.

```dax
Average Delivery Time =
AVERAGE('Call Center_Restaurant Orders'[Time Taken for Delivery Process]) / 3600
```

---

### `Average Order Placement`
**Table:** Call Center_Restaurant Orders  
**Purpose:** Mean time for the order placement stage (customer call to restaurant receipt), in minutes.

```dax
Average Order Placement = AVERAGE('Call Center_Restaurant Orders'[OrderPlacement]) / 60
```
---

### `Average Order Processing`
**Table:** Call Center_Restaurant Orders  
**Purpose:** Mean time for the order processing stage (restaurant receipt to driver pickup), in minutes.

```dax
Average Order Processing = AVERAGE('Call Center_Restaurant Orders'[OrderProcessing]) / 60
```

---

### `Average Order Delivery`
**Table:** Call Center_Restaurant Orders  
**Purpose:** Mean time for the final delivery leg (driver pickup to customer door), in minutes.

```dax
Average Order Delivery = AVERAGE('Call Center_Restaurant Orders'[OrderDelivery]) / 60
```

---

## Efficiency

### `Service Efficiency`
**Table:** Call Center_Restaurant Orders  
**Purpose:** Orders completed per hour of total delivery process time — an overall operational throughput measure.

```dax
Service Efficiency =
COUNT('Call Center_Restaurant Orders'[Delivery time])
    / (SUM('Call Center_Restaurant Orders'[Time Taken for Delivery Process]) / 3600)
```

---

### `Driver Efficiency`
**Table:** DriverSummary  
**Purpose:** Deliveries completed per hour worked, per driver. Higher = more productive.

```dax
Driver Efficiency = SUM(DriverSummary[Count]) / (SUM(DriverSummary[DriverSecondsWorked]) / 3600)
```

---

## Customers

### `Total Customers`
**Table:** Call Center_Restaurant Orders  
**Purpose:** Count of distinct customers who placed at least one order.

```dax
Total Customers = DISTINCTCOUNT('Call Center_Restaurant Orders'[Customer ID])
```

---

### `customer turnout`
**Table:** Customer Retention Summary  
**Purpose:** Percentage of total customers who placed repeat orders (customer retention rate).

```dax
customer turnout = SUM('Customer Retention Summary'[HighRetention]) * 100 / [Total Customers]
```

> The `HighRetention` column in `Customer Retention Summary` is a binary flag (1 = repeat customer >= 10, 0 = one-time or less than 10). Summing it gives the count of returning customers.

---

## Dynamic titles (slicer-aware labels)

These measures generate dynamic text that updates based on active slicer selections. They are used as visual titles in the dashboard.

### `loction listing`
**Table:** DeliveryArea  
**Purpose:** Returns the selected area name(s) or "Location" if no filter is active.

```dax
location listing =
IF(
    ISFILTERED(DeliveryArea[Delivery Area]),
    CONCATENATEX(VALUES(DeliveryArea[Delivery Area]), DeliveryArea[Delivery Area], ", "),
    "Location"
)
```
> ⚠️ Typo in name — should be `location listing`.

---

### `location title`
**Table:** DeliveryArea  
**Purpose:** Dynamic chart title: "Sales by [Area]" or "Sales by Location".

```dax
location title = "Sales by " & [loction listing]
```

---

### `locatio time title`
**Table:** DeliveryArea  
**Purpose:** Dynamic chart title: "Average Order Time by [Area]" or "Average Order Time by Location".

```dax
locatio time title = "Average Order Time by " & [loction listing]
```
> ⚠️ Typo in name — should be `location time title`.

---

### `month listing`
**Table:** MonthlyRevenue  
**Purpose:** Returns the selected month name(s) or "Month" if no filter is active.

```dax
month listing =
IF(
    ISFILTERED(MonthlyRevenue[Month Name]),
    CONCATENATEX(VALUES(MonthlyRevenue[Month Name]), MonthlyRevenue[Month Name], ", "),
    "Month"
)
```

---

### `monthly title`
**Table:** MonthlyRevenue  
**Purpose:** Dynamic chart title: "Sales by [Month]" or "Sales by Month".

```dax
monthly title = "Sales by " & MonthlyRevenue[month listing]
```

---

### `day listing`
**Table:** Day week  
**Purpose:** Returns the selected day name(s) or "Daily" if no filter is active.

```dax
day listing =
IF(
    ISFILTERED('Day week'[Day Name]),
    CONCATENATEX(VALUES('Day week'[Day Name]), 'Day week'[Day Name], ", "),
    "Daily"
)
```

---

### `day title`
**Table:** Day week  
**Purpose:** Dynamic chart title: "[Day] Sales Trend" or "Daily Sales Trend".

```dax
day title = 'Day week'[day listing] & " Sales Trend"
```

---

## Measure summary table

| Measure | Table | Category | Format |
|---------|-------|----------|--------|
| Revenue | ASAP | Revenue | Currency |
| order total | ASAP | Orders | Integer |
| order total percent | ASAP | Orders | % |
| ASAP yes | ASAP | Order type | Integer |
| ASAP yes percent | ASAP | Order type | % |
| completed | IsRefunded | Quality | Integer |
| completion rate | IsRefunded | Quality | % |
| time taken | Call Center_Restaurant Orders | Timing | Hours |
| Average Delivery Time | Call Center_Restaurant Orders | Timing | Hours |
| Average Order Processing | Call Center_Restaurant Orders | Timing | Minutes |
| Average Order Placement | Call Center_Restaurant Orders | Timing | Minutes |
| Average Order Delivery | Call Center_Restaurant Orders | Timing | Minutes |
| Service Efficiency | Call Center_Restaurant Orders | Efficiency | Orders/hr |
| Driver Efficiency | DriverSummary | Efficiency | Orders/hr |
| Total Customers | Call Center_Restaurant Orders | Customers | Integer |
| customer turnout | Customer Retention Summary | Customers | % |
| loction listing | DeliveryArea | Dynamic title | Text |
| location title | DeliveryArea | Dynamic title | Text |
| locatio time title | DeliveryArea | Dynamic title | Text |
| month listing | MonthlyRevenue | Dynamic title | Text |
| monthly title | MonthlyRevenue | Dynamic title | Text |
| day listing | Day week | Dynamic title | Text |
| day title | Day week | Dynamic title | Text |
