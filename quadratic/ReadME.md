# Quadratic AI – Analytics Layer

This folder documents how **Quadratic AI** was used as the analytical and AI-assisted exploration layer in this project.

Quadratic was chosen to demonstrate how **prompt-driven analysis**, combined with strong data fundamentals, can accelerate supply chain analytics without replacing human validation.

---

## Role of Quadratic in This Project

Quadratic sits **on top of the PostgreSQL database** (hosted on Supabase) and is used for:

- Exploring data using natural language prompts
- Generating analytical tables using AI-assisted Python code
- Creating derived datasets for analysis
- Validating supply chain KPIs and business logic

Quadratic is **not** the system of record.  
It is an **analysis and experimentation layer**.

---

## Data Access

Quadratic connects directly to the PostgreSQL database and pulls:

- Fact tables:
  - `fact_aggregate`
  - `fact_order_line`
- Dimension tables:
  - `dim_customers`
  - `dim_products`
  - `dim_targets_orders`

All data used in Quadratic originates from the database layer.

---

## AI-Assisted Workflows

### 1. Date Dimension (`dim_date`)
- Generated using natural language prompts
- Covers the full date range of order data
- Enables time-based analysis such as:
  - Monthly trends
  - SLA monitoring
  - Performance over time

---

### 2. Exchange Rate Table
- Created using historical exchange rate data
- Data fetched from the OpenExchangeRates API
- Used to normalize order values into a single reporting currency (INR)

This avoids using dummy rates and ensures realistic financial analysis.

---

### 3. Fact Summary Table
- A denormalized dataset created for analysis
- Built by joining:
  - Order-line data
  - Product details
  - Customer attributes
  - Exchange rate data
- Includes cleaned IDs, standardized dates, and calculated order values

This table is used for:
- Prompt-based analysis
- Rapid business exploration
- Demonstration purposes

---

## Prompt Engineering

Quadratic’s AI was guided using **explicit prompts** to:

- Load and clean data
- Perform joins correctly
- Calculate monetary values
- Preserve analytical grain

Prompts and exercises used during this project are documented in the `prompts/` and `exercises/` subfolders.

---

## Validation and Corrections

AI-generated outputs were **not blindly trusted**.

During analysis:
- Missing columns were identified and corrected
- Join logic was reviewed
- Supply chain KPI definitions were manually validated
- Grain mismatches were corrected before drawing conclusions

This ensured that business insights remained accurate and defensible.

---

## Key Learnings

- AI significantly accelerates exploratory analysis
- Domain expertise is required to validate results
- Incorrect KPI logic can lead to misleading insights
- Human-in-the-loop validation is essential for business-critical analytics

Quadratic is most powerful when used as a **copilot**, not a replacement for analytical thinking.

---

## Why Quadratic Was Used

Quadratic enables:
- Fast iteration through prompts
- Transparent, editable Python code
- Easy correction of AI-generated logic
- A balance between automation and control

It fits naturally into a modern AI-agentic analytics workflow.

---

## Summary

Quadratic played a critical role in:
- Accelerating analysis
- Enabling prompt-based exploration
- Validating supply chain KPIs
- Demonstrating the importance of AI literacy and domain knowledge

It complements the automation and database layers to form a complete, modern analytics system.
