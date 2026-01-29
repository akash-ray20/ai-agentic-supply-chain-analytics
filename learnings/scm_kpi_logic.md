# Supply Chain KPI Logic

This document explains the **business logic and definitions** behind the key supply chain KPIs used in this project.

Correct KPI logic is critical to ensure analytical accuracy and trustworthy business insights.

---

## Orders vs Order Lines

Before defining KPIs, it is essential to distinguish between:

- Order  
  A single transaction identified by a unique Order ID

- Order Line  
  An individual product item within an order

Many supply chain KPIs depend on applying logic at the **correct level of detail**.

---

## Line Fill Rate (LFR)

Line Fill Rate measures fulfillment performance at the **order line level**.

Definition:
- Percentage of order lines delivered in full

Logic:
- A line is considered fulfilled only if delivered quantity equals ordered quantity

Used by:
- Supply planners
- Production managers
- Regional supply teams

---

## Volume Fill Rate (VFR)

Volume Fill Rate measures fulfillment at the **quantity level**.

Definition:
- Ratio of total quantity delivered to total quantity ordered

Logic:
- Aggregated across all order lines
- Independent of how many lines failed

Used by:
- Sales teams
- Commercial negotiations
- Customer communication

---

## On-Time Delivery (OT)

On-Time Delivery evaluates **delivery timeliness at the order level**.

Definition:
- An order is on-time if the actual delivery date matches the agreed delivery date

Logic:
- Binary outcome per order (on-time or not)

Used by:
- Warehouse and logistics teams

---

## In-Full Delivery (IF)

In-Full Delivery measures **order completeness**.

Definition:
- An order is In-Full only if every line item is delivered in full

Logic:
- Even one missing item causes the entire order to fail

Used by:
- Regional supply managers
- Fulfillment accuracy monitoring

---

## On-Time In-Full (OTIF)

OTIF (Reliability) is the most stringent supply chain KPI.

Definition:
- An order must be both On-Time and In-Full

Logic:
- Calculated strictly at the order level
- Partial success is not allowed

Used by:
- Supply Chain Directors
- Senior leadership
- SLA enforcement and customer retention

---

## Key Takeaway

Supply chain KPIs are **not interchangeable metrics**.

Correct KPI computation depends on:
- Clear definitions
- Grain awareness
- Strict adherence to business rules

Misapplying KPI logic can lead to incorrect strategic decisions.
