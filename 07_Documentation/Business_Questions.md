# Healthcare Claims & Revenue Analytics

## Project Objective

Analyze healthcare claims data to understand claim volume, payment patterns, provider utilization, beneficiary payment concentration, payment integrity signals, and potential revenue leakage indicators.

## Primary Business Question

How can healthcare organizations use claims data to identify payment trends, provider performance patterns, beneficiary payment concentration, and payment-integrity signals that may warrant further review?

## Key Business Questions

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

## Analytical Areas

### Claims Volume
- Total number of claims
- Claims by month
- Claims by claim type
- Claims by provider
- Claims by beneficiary

### Financial Analysis
- Total payment amount
- Average payment per claim
- Payment trends
- Payment bands
- Payment concentration
- Beneficiary financial segmentation

### Payment Integrity
- Zero-payment claims
- Negative-payment claims
- Non-positive payment rates
- Provider-level payment-integrity signals
- Payment patterns requiring further review

> This project does not contain a dedicated claim-denial field. Zero-payment claims are therefore not classified as denied claims, and negative payments are not automatically interpreted as refunds, reversals, fraud, or other specific causes.

### Provider Analysis
- Provider claim volume
- Provider payment amount
- Average and median payment per claim
- Payment-per-claim benchmarking
- Payment intensity
- Provider payment concentration
- Payment-integrity screening signals

### Beneficiary Analysis
- Claims per beneficiary
- Payment per beneficiary
- Beneficiary payment segments
- Payment share by beneficiary segment
- Claim share by beneficiary segment
- Higher-payment beneficiary segments

### Diagnosis & Procedure Analysis
- Diagnosis-level payment patterns
- Procedure-level payment patterns
- High-payment diagnosis categories
- High-payment procedure categories
- Outpatient HCPCS payment analysis

## Expected Deliverables

- Python data-validation and data-quality workflow
- Python data-cleaning workflow
- Exploratory data analysis
- SQL analytical queries
- Curated analytical outputs
- Power BI dashboard
- Healthcare claims analytics documentation
- GitHub portfolio repository

## Important Data Limitation

The dataset is based on the synthetic **CMS DE-SynPUF Sample 1** dataset. The analysis is descriptive and intended for analytical demonstration; findings should not be generalized to real-world Medicare populations or interpreted as clinical, fraud, or compliance conclusions without additional validation.