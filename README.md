# Healthcare Claims & Revenue Analytics

A healthcare analytics project using **CMS DE-SynPUF Sample 1** to analyze claims volume, payment patterns, provider performance, beneficiary financial segmentation, payment concentration, and payment-integrity signals.

> **Important:** CMS DE-SynPUF is synthetic data. This project is intended for analytical demonstration and portfolio purposes. Findings should not be generalized to real-world Medicare populations or interpreted as clinical, fraud, or compliance conclusions.

---

## Project Overview

Healthcare claims data contains valuable information about utilization, payments, providers, beneficiaries, diagnoses, and procedures.

This project builds an end-to-end analytics workflow to transform raw claims data into business-oriented insights using:

- **Python** for validation, data-quality assessment, cleaning, and exploratory analysis
- **SQL / DuckDB** for structured analytical queries and financial/provider/beneficiary analysis
- **Power BI** for executive, provider, and beneficiary dashboards

The project focuses on understanding **where claims volume and payments are concentrated, how payment patterns vary across providers and beneficiaries, and which payment-integrity signals may warrant further review.**

---

## Business Objective

The primary objective is to answer:

> **How can healthcare organizations use claims data to identify payment trends, provider performance patterns, beneficiary payment concentration, and payment-integrity signals that may warrant further review?**

### Key Business Questions

1. What is the total number of claims?
2. What is the total amount paid across claims?
3. What is the average payment per claim?
4. How are claims and payments distributed between inpatient and outpatient services?
5. Which providers generate the highest claim volume and payment amounts?
6. Which providers have payment-per-claim values above the relevant benchmark?
7. Which providers show higher-than-expected non-positive payment rates?
8. Which diagnosis and procedure categories are associated with higher payment amounts?
9. What are the monthly claim volume and payment trends?
10. Which beneficiaries fall into higher payment and utilization segments?
11. How concentrated are payments across providers and beneficiaries?
12. What payment patterns may warrant additional financial or operational review?

---

## Dataset

**Source:** CMS DE-SynPUF Sample 1

### Included Data

| Data Domain | Included |
|---|---:|
| Beneficiary data | Yes |
| Inpatient claims | Yes |
| Outpatient claims | Yes |
| Carrier claims | No |
| Prescription drug events (PDE) | No |

### Analytical Scope

The project uses:

- Beneficiary files for 2008–2010
- Inpatient claims
- Outpatient claims

The raw dataset is intentionally **not included in the GitHub repository**. It remains in the local `01_Raw_Data/` directory and is excluded through `.gitignore`.

---

## Project Results

The completed analytical dataset contains:

| Metric | Result |
|---|---:|
| Total claims | **857,563** |
| Inpatient claims | **66,773** |
| Outpatient claims | **790,790** |
| Unique beneficiaries with claims | **86,738** |
| Total payment | **₹863,784,890** |
| Inpatient payment | **₹639,260,180** |
| Outpatient payment | **₹224,524,710** |
| Average payment per claim | **₹1,007.26** |
| Zero-payment claims | **32,265** |
| Negative-payment claims | **2,621** |
| Missing-payment claims | **0** |

---

## Analytical Workflow

```text
Raw CMS DE-SynPUF Data
        │
        ▼
Data Validation
        │
        ▼
Data Quality Assessment
        │
        ▼
Data Cleaning
        │
        ▼
Exploratory Data Analysis
        │
        ▼
SQL Analytical Layer
        │
        ▼
Curated Analytical Outputs
        │
        ▼
Power BI Dashboard
        │
        ▼
Business Insights
```

---

## Python Analysis

The Python workflow is organized into four notebooks.

### 1. Data Validation

`03_Python/01_Data_Validation.ipynb`

Validates:

- File availability
- Dataset dimensions
- Column structures
- Data types
- Beneficiary and claim identifiers
- Duplicate records
- Payment fields
- Referential consistency

### 2. Data Quality Assessment

`03_Python/02_Data_Quality_Assessment.ipynb`

Examines:

- Missing values
- Duplicate records
- Negative payments
- Zero payments
- Invalid or unusual values
- Data consistency
- Claim-level integrity

### 3. Data Cleaning

`03_Python/03_Data_Cleaning.ipynb`

Creates analytical-ready datasets while preserving the original raw data.

**Raw data is never modified.**

### 4. Exploratory Data Analysis

`03_Python/04_Exploratory_Data_Analysis.ipynb`

Explores:

- Claim volume
- Payment distributions
- Inpatient vs outpatient patterns
- Monthly trends
- Provider payment patterns
- Beneficiary payment patterns
- Diagnosis and procedure patterns
- Payment concentration

---

## SQL Analysis

SQL analysis is performed using **DuckDB**.

Main notebook:

`04_SQL/01_SQL_Analysis.ipynb`

The SQL layer contains analytical outputs covering:

### Claims

- Claims financial summary
- Payment bands
- Payment concentration
- Payment status
- Monthly financial trends
- Month-over-month changes

### Providers

- Provider financial performance
- Provider ranking
- Payment benchmarking
- Payment intensity
- Payment concentration
- Payment-integrity screening

### Beneficiaries

- Financial segmentation
- Financial mix
- Payment intensity
- Service mix
- Top payment beneficiaries

### Diagnoses & Procedures

- Diagnosis-level financial analysis
- High-payment diagnosis analysis
- Procedure financial analysis
- HCPCS payment analysis
- High-value outpatient HCPCS

---

## Power BI Dashboard

The Power BI dashboard contains three analytical pages.

### 1. Executive Overview

**`01_Executive_Overview`**

Provides a high-level view of:

- Total claims
- Total payments
- Average payment per claim
- Unique beneficiaries
- Monthly claim trends
- Monthly payment trends
- Inpatient vs outpatient claim mix

### 2. Provider Financial & Performance Analysis

**`02_Provider_Analysis`**

Analyzes:

- Top providers by total payment
- Providers above payment benchmarks
- Non-positive payment rates
- Provider payment intensity
- Provider payment concentration

### 3. Beneficiary Financial Analysis

**`03_Beneficiary_Analysis`**

Analyzes:

- Beneficiaries by payment segment
- Payment share by beneficiary segment
- Claim share by beneficiary segment
- Average payment per beneficiary

---

## Payment Integrity Approach

This project does **not** contain a dedicated claim-denial field.

Therefore:

- Zero-payment claims are **not classified as denied claims**
- Negative-payment claims are **not automatically classified as refunds or reversals**
- Negative payments are **not automatically treated as fraud**
- Provider payment-integrity metrics are **screening signals only**

The analysis is designed to identify patterns that could warrant additional financial or operational investigation.

---

## Key Analytical Insights

### Claims Mix

Outpatient claims represent the majority of observed claim volume, while inpatient claims account for a substantially larger share of total payments.

### Payment Concentration

Provider-level payment concentration analysis shows that payment is distributed across a large provider population rather than being dominated by only a small number of providers.

### Provider Benchmarking

Provider payment-per-claim benchmarking identifies providers whose observed payment intensity is above the relevant analytical benchmark.

These are **analytical comparison signals**, not evidence of inappropriate billing.

### Beneficiary Segmentation

Beneficiaries can be segmented according to payment levels and claim activity to understand how healthcare payments are distributed across the population represented in the synthetic dataset.

---

## Data Quality & Integrity

The completed validation and reconciliation process established:

- Claim business keys are unique using `CLM_ID + SEGMENT`
- Claims successfully match beneficiary identifiers
- No missing payment values were identified
- Zero and negative payment claims were explicitly identified
- Raw data was preserved without modification
- Analytical datasets were generated separately
- SQL outputs were reconciled against the overall claims totals

Final reconciliation:

```text
Total claims:              857,563
Unique claim keys:         857,563
Unique beneficiaries:       86,738
Inpatient claims:            66,773
Outpatient claims:          790,790
Total payment:          ₹863,784,890
```

---

## Repository Structure

```text
Healthcare_Claims_Revenue_Analytics/
│
├── .gitignore
├── README.md
│
├── 03_Python/
│   ├── 01_Data_Validation.ipynb
│   ├── 02_Data_Quality_Assessment.ipynb
│   ├── 03_Data_Cleaning.ipynb
│   └── 04_Exploratory_Data_Analysis.ipynb
│
├── 04_SQL/
│   ├── 01_SQL_Analysis.ipynb
│   └── analytical_outputs/
│
├── 05_PowerBI/
│   └── 01_Data/
│       ├── 01_Executive/
│       ├── 02_Provider/
│       └── 03_Beneficiary/
│
└── 07_Documentation/
    └── Business_Questions.md
```

### Excluded from GitHub

The following are intentionally excluded:

```text
00_Working_Data/
01_Raw_Data/
02_Cleaned_Data/
*.pbix
*.duckdb
*.duckdb.wal
```

This prevents large source, working, database, and Power BI files from being accidentally committed.

---

## Tools & Technologies

| Technology | Purpose |
|---|---|
| Python | Data validation, cleaning & EDA |
| Pandas | Data manipulation |
| NumPy | Numerical analysis |
| Jupyter | Analytical notebooks |
| SQL | Claims and financial analytics |
| DuckDB | Local analytical database |
| Power BI | Interactive dashboarding |
| DAX | Power BI measures |
| Git | Version control |
| GitHub | Portfolio publishing |

---

## Important Limitations

1. **Synthetic data:** CMS DE-SynPUF is synthetic and does not represent actual Medicare beneficiary behavior.
2. **No denial field:** The dataset does not provide a dedicated claim-denial indicator.
3. **Payment interpretation:** Zero and negative payments require contextual interpretation.
4. **No fraud conclusions:** Payment-integrity screens identify patterns for review and do not establish fraud.
5. **No clinical conclusions:** High utilization or payment segments are analytical classifications rather than clinical risk assessments.
6. **Limited scope:** This project covers beneficiary, inpatient, and outpatient data available in the selected dataset.
7. **Descriptive analysis:** Results describe patterns in the selected synthetic dataset and should not be generalized to real-world populations.

---

## Portfolio Value

This project demonstrates an end-to-end healthcare analytics workflow:

**Data → Quality → Python → SQL → Financial Analytics → Power BI → Business Insights**

It is designed to demonstrate practical skills relevant to:

- Healthcare Data Analyst
- Healthcare BI Analyst
- Revenue Cycle Analyst
- Claims Analyst
- Healthcare Reporting Analyst
- Business Intelligence Analyst

---

## Author

**Dr. Sumit Bhardwaj**

Healthcare Data Analytics | Clinical & Healthcare Operations | SQL | Python | Power BI | Healthcare Claims Analytics