# Fact Summary Prompt

This prompt was used to create a **denormalized fact_summary table** for analysis and exploration in Quadratic.

The table consolidates multiple datasets into a single analytical view.

---

## Prompt Used

Create a Python code that:

### 1. Load data from:
- fact_order_line table  
- dim_products sheet (skip first row, use second row as headers)  
- dim_customers sheet (skip first row, use second row as headers)  
- Exchange Rate sheet (skip first row, use second row as headers)  

### 2. Clean the data:
- Convert product_id and customer_id to numeric  
- Strip whitespace from IDs  
- Remove rows with NULL IDs  
- Convert IDs to integers  
- Convert dates to datetime  

### 3. Merge the tables:
- Orders with products using product_id  
- Result with customers using customer_id  
- Result with exchange rates using order_placement_date  

### 4. Calculate total amounts:
- For USD currency:  
  `price_USD * USD_INR_Rate * order_qty`
- For INR currency:  
  `price_INR * order_qty`

### 5. Clean final output:
- Drop intermediate columns:  
  `price_USD, price_INR, currency, Date, USD_INR_Rate`
- Keep only essential columns:
  - Order details
  - IDs
  - Dates
  - Quantities
  - Delivery information
  - Total order amount (INR)

---

## Purpose

- Enable AI-driven exploratory analysis
- Simplify joins for business questions
- Provide a flattened dataset for demonstration and validation

---

## Validation

AI-generated code was manually reviewed to:
- Fix missing columns
- Correct join logic
- Preserve correct analytical grain
