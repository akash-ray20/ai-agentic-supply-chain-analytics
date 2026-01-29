# KPI Prompt

This file documents the **single KPI prompt** used in Quadratic AI to compute supply chain performance metrics.

The focus of this prompt was to validate whether the AI could correctly understand and compute **domain-specific supply chain KPIs**.

---

## Prompt Used

Create the following KPIs:

1. Total Orders  
2. Total Order Lines  
3. Line Fill Rate  
4. Volume Fill Rate  
5. On Time Delivery %  
6. In Full Delivery %  
7. On Time In Full (OTIF) %

---

## Purpose

This prompt was used to:
- Test AI understanding of supply chain KPI definitions
- Validate correct grain usage (order-level vs line-level)
- Compare AI-generated results against SQL-based calculations

---

## Validation Performed

- Order-level KPIs (On-Time, In-Full, OTIF) were manually verified
- Line-level KPIs (LFR, VFR) were checked for correct aggregation logic
- AI results were cross-validated using PostgreSQL SQL queries
- Any incorrect assumptions were corrected before final use

---

## Key Insight

While Quadratic AI was able to compute the KPIs, **human domain knowledge was essential** to ensure:

- Correct KPI definitions
- Proper grain handling
- Business-safe interpretations

This reinforces the importance of a human-in-the-loop approach when using AI for analytics.
