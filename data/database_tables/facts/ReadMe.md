# Fact Tables

This folder contains the **fact tables** used in the PostgreSQL database to store transactional supply chain data.

Fact tables represent **measurable business events** and form the foundation for all KPI calculations and analytical insights in this project.

---

## Purpose of Fact Tables

Fact tables answer questions such as:
- *What* happened?
- *When* did it happen?
- *How much* was ordered or delivered?

They store numeric and event-level data that is analyzed using SQL and AI-powered tools.

---

## Tables in This Folder

### fact_aggregate
- Grain: **One row per order**
- Represents order-level transactions
- Includes:
  - Order identifiers
  - Order placement dates
  - Fulfillment indicators:
    - On-Time
    - In-Full
    - OTIF (On-Time In-Full)

#### Used for:
- Total Orders calculation
- On-Time Delivery %
- In-Full Delivery %
- OTIF / Reliability metrics
- SLA and service-level analysis

---

### fact_order_line
- Grain: **One row per order line**
- Represents individual products within an order
- Includes:
  - Product identifiers
  - Ordered quantities
  - Delivered quantities
  - Line-level delivery information

#### Used for:
- Total Order Lines calculation
- Line Fill Rate (LFR)
- Volume Fill Rate (VFR)
- Product-level and quantity-based analysis

---

## Grain Awareness (Critical)

Each fact table operates at a **different level of detail**:

- `fact_aggregate` → order-level grain  
- `fact_order_line` → line-level grain  

Mixing these grains incorrectly can lead to:
- Double counting
- Incorrect KPIs
- Misleading business insights

All KPI logic in this project explicitly respects table grain.

---

## How Fact Tables Are Used

Fact tables are:
- Loaded into PostgreSQL via the n8n automation pipeline
- Joined with dimension tables for contextual analysis
- Queried using SQL to compute KPIs
- Accessed by Quadratic AI for prompt-based analytics

---

## Important Notes

- Fact tables grow continuously as new sales data arrives
- They should not be edited manually
- All changes must flow through the ingestion pipeline
- Maintaining grain integrity is essential for analytical correctness

---

## Why This Matters

Well-designed fact tables:
- Enable accurate KPI computation
- Support scalable analytics
- Reflect real-world transactional behavior
- Ensure trust in business reporting and AI-driven insights

They are the backbone of any reliable analytical system.
