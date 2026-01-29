# AI Limitations and Validation

This document captures the limitations observed while using AI-assisted analytics tools in this project and explains why **human validation is essential**.

---

## AI Is Not Domain-Aware by Default

AI tools like Quadratic can:
- Generate Python code
- Create charts and tables
- Aggregate data quickly

However, AI does not inherently understand:
- Supply chain domain rules
- Business definitions of KPIs
- The consequences of incorrect logic

Without guidance, AI may apply **technically valid but business-invalid logic**.

---

## Common Issues Observed

During analysis, the following limitations were encountered:

- Incorrect KPI grain assumptions  
  (e.g., calculating In-Full at line level instead of order level)

- Silent logic errors  
  (results looked reasonable but were analytically incorrect)

- Missing columns or joins in AI-generated code

- Over-aggregation leading to inflated KPIs

These issues did not raise errors but could lead to **misleading insights**.

---

## Importance of Human Validation

Every AI-generated output was manually reviewed to ensure:
- Correct KPI definitions
- Proper grain handling
- Alignment with supply chain best practices

Validation included:
- Cross-checking results using SQL
- Reviewing generated Python code
- Interpreting outputs through a business lens

---

## Key Takeaway

AI dramatically accelerates analysis, but **it cannot be blindly trusted**.

Reliable analytics requires:
- Strong domain expertise
- Explicit validation steps
- Human-in-the-loop decision making

AI should be treated as a **copilot**, not an autonomous decision-maker.
