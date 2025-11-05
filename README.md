# Bank Loan Performance Analysis

An end-to-end **Finance Analytics Project** analyzing bank loan performance using **SQL Server** and **Power BI**.  
This project uncovers key insights into loan issuance, repayments, borrower behavior, and portfolio health — empowering data-driven decisions in the banking sector.

---

## Project Overview

Banks manage massive loan portfolios daily. This project simulates a real-world analytics workflow — from data extraction and cleaning in **SQL Server** to visualization in **Power BI** — offering a 360° view of lending performance.

The solution integrates:
- SQL-based data querying, aggregation, and KPI computation  
- Power BI data modeling and relationships  
- Three interactive dashboards: **Summary**, **Overview**, and **Details**

<img width="891" height="504" alt="Overview Dashboard" src="https://github.com/user-attachments/assets/c1d1372c-1bb4-4126-bdb6-3863d3bdec73" />
---

## Project Objectives

- Evaluate loan performance using business KPIs  
- Identify portfolio risk through *Good vs. Bad Loan* segmentation  
- Analyze trends by month, region, and borrower attributes  
- Provide actionable recommendations to optimize lending decisions  
- Develop business-ready visualizations using real financial data concepts

---

## Workflow

1. **Data Source & Cleaning** – Loaded `bank_loan_data` table into SQL Server, verified schema, and cleaned missing or invalid fields.  
2. **Query Development** – Designed modular SQL scripts to calculate KPIs such as:
   - Total Loans, Funded Amount, Amount Received  
   - Avg Interest Rate & DTI  
   - Good vs. Bad Loan Ratios  
3. **Validation** – Cross-checked dashboard values against SQL results for accuracy.  
4. **Modeling in Power BI** – Connected SQL Server to Power BI, built star schema, created relationships, and applied DAX measures.  
5. **Dashboard Design** – Developed three dashboards:
   - **Summary Dashboard:** Portfolio-level KPIs & performance metrics  
   - **Overview Dashboard:** Trends by month, region, purpose, term, and ownership  
   - **Details Dashboard:** Loan-level drill-downs for detailed insights  

---

## Key Metrics & SQL Highlights

| Metric | SQL Logic Summary |
|--------|--------------------|
| **Total Loan Applications** | `COUNT(id)` |
| **Funded Amount** | `SUM(loan_amount)` |
| **Amount Received** | `SUM(total_payment)` |
| **Avg Interest Rate** | `AVG(int_rate) * 100` |
| **Avg DTI** | `AVG(dti) * 100` |
| **Good Loan %** | `(Fully Paid + Current) / Total Loans` |
| **Bad Loan %** | `(Charged Off) / Total Loans` |

All queries are documented in [`/SQL Server/Query_Documentation.md`](./SQL Server/Query_Documentation.md)

---

## Key Insights

- **Good Loans:** Represented the majority of portfolio — indicating healthy repayment behavior.  
- **Bad Loans:** Concentrated among specific states and higher DTI borrowers.  
- **Time Trends:** Loan applications peaked mid-year; disbursements consistent with marketing campaigns.  
- **Portfolio Efficiency:** 80%+ of funds recovered on average, with manageable risk exposure.  

These insights support **risk management, lending optimization**, and **profitability improvement** initiatives.

---

## Dashboards Overview

### 1️⃣ Summary Dashboard
- Displays top-level KPIs (Total Loans, Funded Amount, Received Amount, Avg Interest & DTI)
- Highlights Good vs. Bad loan ratios and monthly performance comparison

<img width="895" height="503" alt="Summary Dashboard" src="https://github.com/user-attachments/assets/75345a20-7386-4f97-a2e0-b790abc61be9" />

### 2️⃣ Overview Dashboard
- Visualizes loan trends across time, region, purpose, term, and ownership
- Enables regional and demographic insights for better segmentation

<img width="891" height="504" alt="Overview Dashboard" src="https://github.com/user-attachments/assets/b50afca3-7963-4c63-acd1-a17d840f0044" />


---

### 3️⃣ Details Dashboard
- Provides granular view with filters for loan grade, status, and borrower type
- Enables in-depth exploration of individual loan performance

<img width="896" height="504" alt="Details Dashboard" src="https://github.com/user-attachments/assets/5377c5d6-6ad8-4135-b4db-69128053bd5d" />


---

## Data & Domain Knowledge

- Dataset: Simulated **Bank Loan Dataset** stored in SQL Server  
- Data Fields: Loan ID, Loan Amount, Issue Date, Loan Status, Interest Rate, DTI, Term, Purpose, Employment Length, etc.  
- Business Context: See [`/Domain/Domain_Knowledge.md`](./Domain/Domain_Knowledge.md) for the full explanation of banking processes, risk assessment, and credit lifecycle.

---

## Tech Stack

| Tool | Purpose |
|------|----------|
| **SQL Server** | Data cleaning, KPI computation, and validation |
| **Power BI** | Data modeling and dashboard creation |
| **Excel** | Initial data exploration and cleaning |
| **DAX** | Advanced measure creation |
| **GitHub** | Version control and portfolio hosting |

---

## Results & Impact

This analysis helps financial institutions to:
- Detect underperforming segments or high-risk loan groups  
- Improve credit decisioning and portfolio profitability  
- Strengthen reporting transparency for business and compliance teams  

---
