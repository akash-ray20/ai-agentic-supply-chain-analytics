# Exchange Rate Prompt

This document describes the prompt used in Quadratic AI to generate a historical exchange rate table for currency normalization.

Instead of relying on static or assumed exchange rates, real historical data was fetched dynamically using an external API to ensure financial accuracy across regions.

---

## Data Source

Historical exchange rates were sourced from the following platform:

https://openexchangerates.org/

An App ID (API key) was generated from the platform and explicitly used inside the AI prompt to enable dynamic, API-driven table creation.

---

## Prompt Used

Create an exchange_rate table for the period from **March 1st, 2025**, to **May 17th, 2025**.

Use the following API request pattern to fetch historical exchange rates:

response = requests.get(f'https://openexchangerates.org/api/historical/2024-10-
21.json?app_id=<Replace your app id here>&symbols=INR')

Replace the date in the URL with each date within the specified range.

---

## Purpose

- Avoid hardcoded or dummy exchange rates
- Ensure realistic conversion of USD-denominated orders to INR
- Enable accurate financial analysis across India and USA datasets
- Demonstrate how AI prompts can be enhanced using live external APIs

---

## Implementation Notes

- The API key was injected directly inside the prompt
- Quadratic generated Python code to iterate through the date range and fetch rates
- Generated code was reviewed and adjusted where required
- The resulting table was used downstream while creating the fact summary dataset

---

## Key Takeaway

Embedding an external API call inside an AI prompt enables dynamic table generation, real-world financial accuracy, and stronger analytical credibility.

This step ensures that all monetary KPIs reflect actual historical exchange conditions rather than assumptions.

