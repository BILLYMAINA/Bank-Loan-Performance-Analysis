# Bank Loan Report – Domain Knowledge

This document provides the **business and industry context** for the *Bank Loan Performance Analysis* project.  
It explains how banks collect, manage, and analyze loan data — and why understanding this data is essential for financial decision-making, risk management, and portfolio optimization.

---

## Overview

Bank loans are a core product in the financial services industry — enabling individuals and organizations to access capital for personal, commercial, and investment purposes.  
To remain profitable and minimize risk, banks must monitor loan performance and customer repayment behavior continuously.  
Analyzing loan data helps institutions strike the right balance between **credit growth and credit risk**.

---

## Data Collection Process

Banks collect loan data through multiple sources and systems during the loan lifecycle:

| Source | Description |
|---------|--------------|
| **Loan Applications** | Borrowers submit personal, financial, and employment information when applying for a loan. |
| **Credit Reports** | Banks access credit bureaus to assess applicants’ credit history, current liabilities, and payment behavior. |
| **Internal Records** | All loan disbursements, repayments, and adjustments are recorded in core banking databases. |
| **Online Portals** | Digital channels capture loan requests, repayments, and account interactions in real time. |
| **Third-Party Data** | External verification (e.g., income validation, identity checks) supplements bank data for enhanced accuracy. |

---

## Loan Approval Workflow

Understanding the loan approval process is essential to model realistic loan performance metrics.  
Below is the simplified process used in the banking domain:

1. **Loan Application** – Customer submits a loan request (online or in person).  
2. **Application Review** – The bank collects and validates supporting documentation.  
3. **Identity Verification** – Confirms applicant authenticity and prevents identity fraud.  
4. **Credit Check** – Evaluates applicant’s credit score and past payment record.  
5. **Income Verification** – Confirms the borrower’s ability to repay.  
6. **Debt-to-Income (DTI) Assessment** – Measures repayment capacity based on income vs. liabilities.  
7. **Employment Verification** – Validates job stability and tenure.  
8. **Collateral Evaluation** *(for secured loans)* – Estimates collateral value and risk.  
9. **Risk Assessment** – Combines all factors to assess overall creditworthiness.  
10. **Loan Approval / Rejection** – Decision made based on bank’s risk tolerance.  
11. **Loan Agreement** – Terms (amount, rate, tenure) finalized and signed.  
12. **Fund Disbursement** – Funds released to borrower.  
13. **Repayment & Monitoring** – Continuous tracking of payments and delinquency.  

---

## Key Metrics in Loan Analytics

The following metrics are commonly used in financial loan reporting and are reflected in this project’s dashboards:

| Metric | Description |
|--------|--------------|
| **Loan Applications** | Total number of loans requested during a period. |
| **Funded Amount** | Total principal amount disbursed to borrowers. |
| **Amount Received** | Total payments (principal + interest) collected. |
| **Interest Rate** | Average rate charged on loans, measuring profitability. |
| **Debt-to-Income (DTI)** | Ratio of borrower’s debt payments to income — indicates repayment capacity. |
| **Good Loan %** | Share of loans currently being repaid or fully paid off. |
| **Bad Loan %** | Share of loans that have defaulted or been charged off. |

---

## Reasons for Loan Data Analysis

Banks analyze loan data to drive data-informed decision-making across multiple business dimensions:

1. **Risk Assessment** – Evaluate borrower creditworthiness and predict default probability.  
2. **Decision Support** – Use analytics to approve or decline loan applications objectively.  
3. **Portfolio Management** – Monitor the performance of all active loans.  
4. **Fraud Detection** – Identify irregular patterns suggesting potential loan fraud.  
5. **Regulatory Compliance** – Ensure compliance with KYC, AML, and HMDA requirements.  
6. **Customer Insights** – Understand borrower behavior to improve customer segmentation and targeting.  
7. **Profitability Analysis** – Track loan interest income versus losses from defaults.  
8. **Market Research** – Identify new lending opportunities based on trends and customer needs.  
9. **Credit Risk Management** – Forecast and manage portfolio exposure.  
10. **Customer Retention** – Detect refinancing or cross-selling opportunities.  

---

## Business Relevance

The insights derived from this analysis help financial institutions:
- Strengthen **credit risk management** practices.  
- Improve **loan approval models** with predictive analytics.  
- Optimize **portfolio profitability** by targeting ideal customer segments.  
- Enhance **strategic reporting** for management and compliance.  

Ultimately, **data-driven loan performance analysis** supports banks in making more informed, fair, and profitable lending decisions.

---

## Summary

| Business Process | Analytical Focus |
|------------------|------------------|
| Loan Origination | Application patterns and approval rates |
| Loan Disbursement | Funded amounts and distribution trends |
| Loan Servicing | Repayment timelines and delinquencies |
| Credit Monitoring | Portfolio health and risk segmentation |
| Regulatory Reporting | Transparency and compliance tracking |

---

> *Understanding the business domain is the foundation of effective analytics.  
> In banking, every number represents a person, a business, and a financial decision that impacts both lives and economies.*

