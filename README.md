# AI-Agentic Supply Chain Analytics  
### Improving Reliability & Fulfillment Visibility at Atliq Mart

This repository contains an end-to-end **AI-agentic supply chain analytics project** built to address real-world fulfillment and reliability challenges faced by a growing FMCG manufacturer.

The project demonstrates how **agentic automation, cloud-native data modeling, and AI-assisted analytics** can be combined with strong domain knowledge to deliver trustworthy business insights.

---

## 📌 Project Context

**Atliq Mart** is a Gujarat-based organic food manufacturer that recently expanded operations into the United States. While demand increased, the supply chain infrastructure did not scale at the same pace, leading to:

- Late deliveries and partial fulfillment  
- Customer dissatisfaction and SLA risk  
- No reliable visibility into OTIF, On-Time, or In-Full performance  
- Manual, Excel-based reporting using CSV files received via email  

Leadership explicitly requested a **modern, AI-powered analytics solution** to fix supply chain gaps before further expansion.

---

## 🎯 Project Objectives

The goal of this project was to design and implement an **AI-agentic analytics system** that could:

- Automate ingestion of daily sales data received via email  
- Centralize India and USA operations into a single analytical source  
- Compute **industry-correct supply chain KPIs**  
- Enable fast, prompt-driven business analysis  
- Improve fulfillment reliability (OTIF) using data-backed insights  

---

## 🏗️ Solution Architecture

The solution follows a layered architecture with clear separation of responsibilities:

1. **Agentic Automation Layer**  
   - Tool: **n8n (local deployment)**  
   - Monitors Gmail inbox for “daily sales” emails  
   - Extracts CSV attachments (aggregate & order-line data)  
   - Standardizes dates using Luxon  
   - Loads clean data into PostgreSQL  

2. **Data Storage & Modeling Layer**  
   - Tool: **PostgreSQL (Supabase)**  
   - Fact and dimension tables with strict grain control  
   - Order-level and line-level data modeled separately  
   - Acts as a single source of truth  

3. **Analytics & AI Layer**  
   - Tool: **Quadratic AI**  
   - Connected directly to PostgreSQL  
   - Used for prompt-driven analysis, KPI computation, and visualization  
   - Integrated with real historical exchange rates via API  

4. **Validation Layer**  
   - Human-in-the-loop review of all AI outputs  
   - SQL used to validate KPI logic and aggregation grain  

---

## 🔄 Data Ingestion & Automation (n8n)

Daily sales data arrives as CSV files via email.

The n8n workflow:
- Triggers on Gmail messages with subject **“daily sales”**
- Downloads attachments automatically
- Separates:
  - Aggregate order data  
  - Order-line level data  
- Normalizes inconsistent date formats using **Luxon**
- Inserts clean records into PostgreSQL tables  

This eliminated manual data handling and reduced ingestion errors.

---

## 🧠 AI-Assisted Analytics (Quadratic)

Quadratic AI was used as an **AI-powered analytical workspace**.

Using natural language prompts, Quadratic was used to:
- Create a `dim_date` table  
- Generate a historical exchange rate table using the OpenExchangeRates API  
- Build a denormalized `fact_summary` table for exploration  
- Compute supply chain KPIs  
- Generate charts and customer-level insights  

AI outputs were **always validated manually** to ensure correctness.

---

## 📊 KPI Framework

The following **industry-standard supply chain KPIs** were implemented:

- **Total Orders**  
- **Total Order Lines**  
- **Line Fill Rate (LFR)**  
- **Volume Fill Rate (VFR)**  
- **On-Time Delivery %**  
- **In-Full Delivery %**  
- **On-Time In-Full (OTIF / Reliability)**  

Key design principle:
> **Order-level KPIs and line-level KPIs were computed separately to preserve analytical correctness.**

OTIF was treated as the **gold-standard reliability metric** used for SLA enforcement and customer negotiations.

---

## 📈 Business Insights Generated

Using AI-driven analysis, the system enabled:

- Monthly On-Time delivery performance by city  
- Identification of high-value customers with low reliability  
- Customer-level OTIF, IF, and OT benchmarking  
- Early warning signals for SLA risk  

These insights shifted discussions from anecdotal explanations to **data-backed root cause analysis**.

---

## 🧪 Human-in-the-Loop Validation

While AI significantly accelerated analysis, it was **not blindly trusted**.

Every AI-generated output was reviewed for:
- Correct KPI definitions  
- Proper aggregation grain  
- Business-safe interpretation  

SQL was used to cross-validate results wherever required.

---

## ✅ Impact

The implemented solution:

- Eliminated manual CSV handling  
- Improved visibility into fulfillment failures  
- Enabled faster, more confident decision-making  
- Created a scalable analytics foundation for future growth  

---

## 🧠 Key Takeaway

> **AI is a force multiplier — not a replacement for analytical thinking.**

The real value of this project came from combining:
- Supply chain domain knowledge  
- Correct data modeling and KPI logic  
- Agentic automation  
- Responsible, validated use of AI  

---

## 🔮 Future Enhancements

- Fully automate U.S. data ingestion  
- Add predictive models for delivery risk  
- Implement automated SLA alerts  
- Extend analytics into inventory optimization  

---

## 📎 Artifacts

- Consulting-style PPT walkthrough  
- Full project report (Word / PDF)  
- n8n workflow JSON  
- SQL-based KPI logic  
- Quadratic AI prompts  

---

## 🙌 Closing Note

This project is intentionally designed to reflect **real-world complexity**, not a clean academic dataset.

It demonstrates how **modern analytics systems should be built** when data is messy, stakeholders care about reliability, and AI must be used responsibly.

---

**Feedback, suggestions, and discussions are welcome.**
