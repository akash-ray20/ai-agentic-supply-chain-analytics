# Processed Datasets

This folder contains **derived and analysis-ready datasets** created downstream of the ingestion and database layers.

The files in this folder are **not raw inputs** and **not the system of record**.  
They exist to support analysis, demonstrations, and AI-assisted exploration.

---

## Purpose of This Folder

The datasets here represent **processed outputs** generated after:

- Raw email data is ingested via n8n
- Data is stored in PostgreSQL (Supabase)
- Cleaning, enrichment, and aggregation logic is applied

These files are primarily used for:
- Analytical convenience
- Sample outputs for reviewers
- AI-assisted analysis in Quadratic
- Demonstrating KPI logic and results

---

## Files in This Folder

### fact_summary_sample.csv

This file is a **sample denormalized dataset** created for analytical purposes.

It is derived by:
- Joining order-line data with:
  - Product details
  - Customer attributes
  - Exchange rate information
- Cleaning and standardizing IDs and dates
- Converting order values into a single reporting currency (INR)

#### Characteristics
- Combines multiple source tables into one flat structure
- Simplifies exploratory analysis and AI-driven querying
- Not used for ingestion or as a source of truth

This dataset is particularly useful for:
- Prompt-based analysis in Quadratic
- Rapid business exploration
- Demonstration and validation of transformation logic

---

### KPIs.csv

This file contains the **final supply chain KPIs** computed from the database using SQL.

It includes metrics such as:
- Total Orders
- Total Order Lines
- Line Fill Rate (LFR)
- Volume Fill Rate (VFR)
- On-Time Delivery %
- In-Full Delivery %
- On-Time In-Full (OTIF %)

#### Characteristics
- Represents the **final analytical output**
- KPIs are calculated using correct grain-aware logic
- Intended for reporting, validation, and business interpretation

This file serves as:
- A reference output for KPI calculations
- A lightweight alternative to dashboards
- A clear representation of business performance

---

## Important Notes

- These datasets are **derived**, not raw
- They should not be used as inputs for ingestion
- Any changes to logic should be made upstream (SQL / automation / AI prompts)
- Files may be regenerated as data volume grows

---

## Why This Matters

Separating processed outputs from raw and database data:

- Prevents confusion between inputs and outputs
- Improves traceability of transformations
- Makes the repository easier to understand
- Reflects real-world analytics best practices

This folder provides a clear view of what the system ultimately produces for analysis and decision-making.
