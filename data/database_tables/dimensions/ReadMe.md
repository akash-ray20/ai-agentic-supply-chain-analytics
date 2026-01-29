# Dimension Tables

This folder contains the **dimension tables** used in the PostgreSQL database to support supply chain analytics.

Dimension tables provide **descriptive context** to the transactional fact tables and are used for slicing, filtering, and business-level analysis.

---

## Purpose of Dimension Tables

Dimension tables answer questions such as:
- *Who* placed the order?
- *What* product was ordered?
- *What* service-level targets apply to a customer?

They do **not** store transactions.  
They enrich fact tables with business meaning.

---

## Tables in This Folder

### dim_customers
- Stores customer identifiers and attributes
- Includes information such as:
  - Customer ID
  - Customer name
  - City / region
- Used for:
  - Customer-level KPIs
  - Regional performance analysis
  - SLA and service-level reporting

---

### dim_products
- Stores product-related attributes
- Includes information such as:
  - Product ID
  - Product category
  - Pricing details
- Used for:
  - Product-level demand analysis
  - Volume and value calculations
  - Category-wise performance insights

---

### dim_targets_orders
- Stores **target service-level metrics** for customers
- Includes targets such as:
  - On-Time %
  - In-Full %
  - OTIF %
- Used for:
  - Target vs actual KPI comparison
  - SLA monitoring
  - Performance gap analysis

---

## How Dimension Tables Are Used

Dimension tables are joined with fact tables to:
- Compute KPIs at customer or product level
- Enable filtering in analytics tools
- Support AI-driven business queries in Quadratic

They remain relatively stable compared to fact tables, which grow daily.

---

## Important Notes

- Dimension tables are loaded into PostgreSQL via the ingestion pipeline
- They should not be edited manually
- Changes should be versioned and handled upstream
- Correct joins depend on consistent and clean primary keys

---

## Why This Matters

Well-designed dimension tables:
- Improve query readability
- Enable scalable analytics
- Ensure consistent business definitions
- Support reliable AI-assisted insights

They are a foundational component of any analytical data model.
