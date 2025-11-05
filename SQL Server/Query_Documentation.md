# Bank Loan SQL Query Documentation

This section contains all SQL Server scripts used for data preparation, KPI computation, and validation in the **Bank Loan Performance Analysis** project.

The queries in this module form the **analytical backbone** of the project — transforming raw loan data into clean, reliable, and interpretable metrics for visualization in **Power BI**.

---

## Project Context

The dataset represents **bank loan applications and repayment behavior**.  
Each record corresponds to a loan, with attributes such as loan amount, interest rate, DTI (Debt-to-Income ratio), term, employment length, and loan status.  

The SQL layer is designed to:
- Extract and clean data from `bank_loan_data` table  
- Calculate monthly and portfolio-level KPIs  
- Segment loans into *Good* and *Bad* categories  
- Support Power BI dashboard validation

---

## Database Setup

- **Database:** `bank_loan_data`  
- **Platform:** Microsoft SQL Server  
- **Primary Table:**  
  - `bank_loan_data`  
    Contains:  
    `id`, `loan_amount`, `term`, `int_rate`, `dti`, `issue_date`, `loan_status`, `total_payment`, `address_state`, `purpose`, `home_ownership`, `emp_length`, `grade`

---

## Key Business KPIs and Their SQL Implementations

### 1️⃣ Loan Application Volume
```sql
-- Total Loan Applications
SELECT COUNT(id) AS Total_Applications
FROM bank_loan_data;
```
<img width="127" height="50" alt="Total Loan Applications" src="https://github.com/user-attachments/assets/1603b3e8-483c-4897-8d45-55e3a2361457" />

```sql
-- Month-to-Date (MTD) Applications
SELECT COUNT(id) AS MTD_Applications
FROM bank_loan_data
WHERE MONTH(issue_date) = 12;
```
<img width="132" height="48" alt="MTD Applications" src="https://github.com/user-attachments/assets/d7730e82-8407-482f-a488-7ca70cf28894" />

```
-- Previous Month-to-Date (PMTD) Applications
SELECT COUNT(id) AS PMTD_Applications
FROM bank_loan_data
WHERE MONTH(issue_date) = 11;
```
<img width="130" height="47" alt="PMTD Applications" src="https://github.com/user-attachments/assets/69ef5c35-9ec0-49fe-a133-330f8ab82420" />

---

### 2️⃣ Loan Funding Performance
```sql
-- Total Funded Amount
SELECT SUM(loan_amount) AS Total_Funded_Amount
FROM bank_loan_data;

-- MTD Funded Amount
SELECT SUM(loan_amount) AS MTD_Funded_Amount
FROM bank_loan_data
WHERE MONTH(issue_date) = 12;

-- PMTD Funded Amount
SELECT SUM(loan_amount) AS PMTD_Funded_Amount
FROM bank_loan_data
WHERE MONTH(issue_date) = 11;
```
---
### 3️⃣ Loan Repayment Collection
```sql
-- Total Amount Received
SELECT SUM(total_payment) AS Total_Amount_Collected
FROM bank_loan_data;

-- MTD Amount Received
SELECT SUM(total_payment) AS MTD_Amount_Collected
FROM bank_loan_data
WHERE MONTH(issue_date) = 12;

-- PMTD Amount Received
SELECT SUM(total_payment) AS PMTD_Amount_Collected
FROM bank_loan_data
WHERE MONTH(issue_date) = 11;
```
---
### 4️⃣ Portfolio Quality Metrics
```sql
-- Average Interest Rate
SELECT AVG(int_rate) * 100 AS Avg_Interest_Rate
FROM bank_loan_data;

-- Average Debt-to-Income Ratio (DTI)
SELECT AVG(dti) * 100 AS Avg_DTI
FROM bank_loan_data;
```
---
### 5️⃣ Loan Quality Segmentation
#### Good Loans
```sql
-- Percentage of Good Loans
SELECT
    (COUNT(CASE WHEN loan_status IN ('Fully Paid', 'Current') THEN id END) * 100.0) / COUNT(id)
    AS Good_Loan_Percentage
FROM bank_loan_data;

-- Good Loan Applications
SELECT COUNT(id) AS Good_Loan_Applications
FROM bank_loan_data
WHERE loan_status IN ('Fully Paid', 'Current');

-- Good Loan Funded Amount
SELECT SUM(loan_amount) AS Good_Loan_Funded_Amount
FROM bank_loan_data
WHERE loan_status IN ('Fully Paid', 'Current');
```
#### Bad Loans
```sql
-- Percentage of Bad Loans
SELECT
    (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) / COUNT(id)
    AS Bad_Loan_Percentage
FROM bank_loan_data;

-- Bad Loan Applications
SELECT COUNT(id) AS Bad_Loan_Applications
FROM bank_loan_data
WHERE loan_status = 'Charged Off';

```
---
### 6️⃣ Loan Status Performance Summary
```sql
SELECT
    loan_status,
    COUNT(id) AS Loan_Count,
    SUM(loan_amount) AS Total_Funded_Amount,
    SUM(total_payment) AS Total_Amount_Received,
    AVG(int_rate * 100) AS Avg_Interest_Rate,
    AVG(dti * 100) AS Avg_DTI
FROM bank_loan_data
GROUP BY loan_status;
```
<img width="745" height="92" alt="Loan Status Summary" src="https://github.com/user-attachments/assets/3f371bdb-b2d1-454e-982a-c2ee7d24ecf9" />

---
### Loan Overview Analysis
#### Monthly Trends
```sql
SELECT 
    MONTH(issue_date) AS Month_Number,
    DATENAME(MONTH, issue_date) AS Month_Name,
    COUNT(id) AS Total_Loan_Applications,
    SUM(loan_amount) AS Total_Funded_Amount,
    SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY MONTH(issue_date), DATENAME(MONTH, issue_date)
ORDER BY MONTH(issue_date);
```
<img width="683" height="271" alt="Monthly trend" src="https://github.com/user-attachments/assets/fd0e1700-8b8f-4d2e-a27e-1cdb7bad0781" />

---
### Regional Performance
```sql
SELECT 
    address_state AS State,
    COUNT(id) AS Total_Loan_Applications,
    SUM(loan_amount) AS Total_Funded_Amount,
    SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY address_state
ORDER BY address_state;
```
<img width="528" height="801" alt="Regional Performance" src="https://github.com/user-attachments/assets/50a566d3-46cc-42a5-9f4a-dc67d6348361" />

---
### Loan Characteristics Breakdown
```sql
-- By Term
SELECT term, COUNT(id) AS Total_Applications, SUM(loan_amount) AS Funded_Amount
FROM bank_loan_data
GROUP BY term;
```
<img width="565" height="68" alt="Loan by Term" src="https://github.com/user-attachments/assets/22e4444f-8ed2-4096-96ea-4f430b2815ca" />

```sql
-- By Employment Length
SELECT emp_length, COUNT(id) AS Applications, SUM(loan_amount) AS Funded_Amount
FROM bank_loan_data
GROUP BY emp_length;
```
<img width="572" height="245" alt="Loan by Employee Length" src="https://github.com/user-attachments/assets/8375f523-415c-4c2d-8c5c-9560c3717189" />

```sql
-- By Loan Purpose
SELECT purpose, COUNT(id) AS Applications, SUM(loan_amount) AS Funded_Amount
FROM bank_loan_data
GROUP BY purpose;

-- By Home Ownership
SELECT home_ownership, COUNT(id) AS Applications, SUM(loan_amount) AS Funded_Amount
FROM bank_loan_data
GROUP BY home_ownership;
```
<img width="573" height="132" alt="Home Ownwership" src="https://github.com/user-attachments/assets/1cd54c5a-21ba-4806-9bf6-56dfceaed062" />

---
### Validation and Filters
- To verify Power BI dashboard accuracy, results were compared using filtered SQL queries.
Example — testing Grade A loans only:
```sql
SELECT 
    purpose, COUNT(id) AS Applications, SUM(loan_amount) AS Funded_Amount
FROM bank_loan_data
WHERE grade = 'A'
GROUP BY purpose
ORDER BY purpose;
```
### Integration with Power BI

The validated KPIs from SQL Server were connected directly to Power BI via the SQL Database connector.

This ensured:
- Accurate aggregation at source level
- Real-time data refresh capability
- Consistent metrics across both SQL and Power BI layers

### Business Impact

This SQL-driven analysis enabled:
- Real-time monitoring of lending performance
- Identification of risk patterns by loan type and region
- Data-backed optimization of interest rates and loan approvals




