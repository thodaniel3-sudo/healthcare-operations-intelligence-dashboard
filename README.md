# Healthcare Operations & Financial Intelligence Dashboard

## Project Overview
This project was completed as part of the AnalystLab Africa Experience Lab Internship Programme (Week 3, Track A: Data Analytics). The objective was to develop an interactive healthcare operations dashboard that helps decision-makers understand encounter patterns, costs, payer coverage, and procedure utilisation. 

## Business Problem
A healthcare organisation needed to improve its understanding of hospital operations, encounter costs, and patient return visits. The goal was to translate historical healthcare datasets into actionable, evidence-based operational insights.

## Data Source & Preparation
The analysis is based on a synthetic healthcare dataset (Synthea) containing:
*   **Encounters:** Fact table containing visit details, costs, and payer coverage.
*   **Procedures:** Fact table containing procedure details and base costs.
*   **Patients:** Dimension table containing demographics (PII removed).
*   **Payers:** Dimension table containing insurance details.
*   **Organizations:** Dimension table containing hospital details.

**Data Cleaning (Power Query):** 
*   Converted ISO 8601 timestamps to standard Date/Time formats.
*   Removed Personally Identifiable Information (PII) such as names, addresses, and coordinates from the Patient table to ensure privacy.
*   Calculated `Encounter Duration (Hours)` using the START and STOP timestamps.
*   Retained valid zero values in `PAYER_COVERAGE` (representing self-pay/out-of-pocket) distinct from missing data.

**Data Modeling:** Built a Star Schema with `Encounters` as the central fact table, related to `Patients`, `Payers`, and `Organizations` (Dimensions), and `Procedures` (Secondary Fact Table).

## Key Findings
1.  **Operational Volume:** Over 27,800 total encounters recorded, with Ambulatory and Outpatient classes representing the highest volume.
2.  **Financial Risk:** 13,586 encounters have zero recorded payer coverage (Self-Pay/NO_INSURANCE), representing a significant financial risk.
3.  **Cost Drivers:** Total claim cost exceeds $101.5 Million. Inpatient encounters account for the longest average duration (over 30 hours).

## Dashboard Pages
1.  **Executive Overview:** High-level KPIs, volume trends, and payer distribution.
2.  **Encounter Trends:** Monthly volume trends and duration comparisons by class.
3.  **Cost & Payer Coverage:** Financial breakdown by class and payer, highlighting zero-coverage risks.
4.  **Procedure Utilisation:** Most frequent procedures and average base costs.
5.  **Demographics & Org:** Patient distribution by gender, race, and ethnicity.

## Limitations
The dataset is synthetic and does not represent real patient data. Therefore, findings demonstrate analytical capability and methodology but should not be used for real-world clinical decisions or policy-making. Additionally, because `TOTAL_CLAIM_COST` includes procedure costs, procedure base costs were not summed alongside total claim costs to prevent double-counting.

## Author
Daniel Thomas
AnalystLab Africa Experience Lab Intern