# Automation – n8n Workflow

This folder contains the **agentic automation layer** of the project, implemented using **n8n (local deployment)**.

The automation pipeline is responsible for ingesting daily sales data received via email and loading it into the cloud database without manual intervention.

---

## 🔁 Workflow Overview

**Gmail → CSV Extraction → Data Standardization → PostgreSQL (Supabase)**

The workflow is event-driven and triggers automatically when a sales email is received.

---

## ⚙️ Automation Logic

### 1. Email Trigger
- n8n monitors a Gmail inbox for incoming messages
- Trigger condition:
  - Inbox emails
  - Subject contains: `daily sales`
- CSV attachments are automatically downloaded

---

### 2. CSV Extraction
- Attachments are parsed using the **Extract from CSV** node
- Two datasets are handled in parallel:
  - Aggregate order data
  - Order line–level data
- Each row in the CSV is converted into a structured JSON object

---

### 3. Date Standardization
- Source files contain inconsistent date formats (e.g. `DD-MM-YYYY`)
- Dates are standardized to ISO format (`YYYY-MM-DD`)
- Implemented using **n8n expressions backed by the Luxon library**
- This ensures compatibility with PostgreSQL and downstream analytics

Detailed logic is documented in `date_standardization.md`.

---

### 4. Database Ingestion
- Cleaned data is inserted into a PostgreSQL database hosted on **Supabase**
- Separate fact tables are maintained:
  - `fact_aggregate` (order-level data)
  - `fact_order_line` (line-level data)

---

## 📁 Folder Contents

| File | Description |
|----|------------|
| `n8n_daily_sales_ingestion_workflow.json` | Exported n8n workflow definition |
| `n8n_workflow.png` | Visual representation of the n8n workflow |
| `date_standardization.md` | Explanation of date normalization logic |
| `README.md` | Documentation for the automation layer |

---

## 🧠 Why n8n?

n8n enables:
- Event-driven, agentic automation
- Visual workflow design
- Easy integration with email, databases, and APIs
- Local deployment for full control

This automation layer eliminates manual data handling and serves as the foundation for reliable downstream analytics.

---

## 📌 Notes
- Credentials and secrets are **not** included in the exported workflow
- The JSON file is safe to share publicly
- The workflow can be imported into another n8n instance if needed
