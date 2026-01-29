# Date Standardization Logic

This document explains the **date normalization step** implemented in the n8n automation workflow.

Date standardization was a critical requirement to ensure reliable data ingestion into PostgreSQL and consistent downstream analytics.

---

## 📌 Problem Context

The daily sales CSV files received via email contained **inconsistent date formats**, including:

- `DD-MM-YYYY`
- Mixed regional formats across India and USA data

PostgreSQL requires dates to be ingested in a consistent format.  
Without normalization, this resulted in **ingestion failures** and unreliable analytical outputs.

---

## 🎯 Objective

- Convert all incoming date fields into **ISO 8601 format**  
