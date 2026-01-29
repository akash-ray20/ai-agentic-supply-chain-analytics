# Database Tables

This folder contains the structured datasets that represent the tables stored in the PostgreSQL database (hosted on Supabase).

These datasets act as the system of record for all analytics, KPI calculations, and AI-driven insights in this project.

---

## Purpose

Unlike the raw CSV files received via email, the datasets in this folder are:

- Cleaned and standardized during ingestion
- Stored with a defined schema
- Designed for analytical querying
- Preserved at the correct grain (order-level vs line-level)

All data in this folder is populated via the n8n automation workflow.

---

## Folder Structure

database_tables/
- dimensions/
  - dim_customers.csv
  - dim_products.csv
  - dim_targets_orders.csv
- facts/
  - fact_aggregate.csv
  - fact_order_line.csv

---

## Data Modeling Approach

The database follows a star-schema–inspired structure:

- Fact tables store transactional data
- Dimension tables store descriptive attributes

This separation ensures accuracy, scalability, and maintainability when computing supply chain KPIs.

---

## Fact Tables

fact_aggregate  
- Grain: One row per order  
- Used for order-level metrics such as On-Time, In-Full, and OTIF  

fact_order_line  
- Grain: One row per order line  
- Used for Line Fill Rate and Volume Fill Rate calculations  

---

## Dimension Tables

dim_customers  
Stores customer identifiers and attributes for segmentation and analysis.

dim_products  
Stores product details, categories, and pricing information.

dim_targets_orders  
Stores target service-level metrics used for target vs actual comparisons.

---

## Important Notes

- These files represent database tables, not raw input data
- Files should not be edited manually
- All changes must flow through the ingestion pipeline
- Preserving data grain is critical for correct KPI computation

---

## Why This Matters

Separating database tables from raw input data:

- Prevents accidental misuse of operational files
- Enables correct and defensible KPI logic
- Reflects real-world data warehouse practices
- Improves traceability and reliability of analytics
