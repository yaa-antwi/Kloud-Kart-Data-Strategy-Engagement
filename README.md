# Kloud Kart: Data Strategy Engagement

## Project Overview

This project presents a 12-month data strategy for Kloud Kart, a growing e-commerce business in Accra, Ghana. It examines the company's current data challenges and recommends practical improvements that fit its budget, two-hire limit, operational needs and business growth plans.

The strategy focuses on protecting customer information, preventing reporting activities from slowing the live website, and giving management reliable business figures without introducing unnecessary technology or costs.

## Deliverables

### 1. Situation Diagnosis
Identifies and ranks Kloud Kart's three main data problems:
- Poor customer-data governance and compliance risks.
- Website performance slowdowns caused by reporting workloads.
- Inconsistent business reporting between Nana and Finance.

Each problem is examined through its root cause, potential costs, assumptions and risk to the business.

### 2. Data Strategy Recommendation and 12-Month Roadmap
Recommends using an approved second server to host a MySQL read replica, moving reporting away from the live database, and introducing scheduled daily reports.

The roadmap divides implementation into four quarterly priorities:
- **Q1:** Address immediate compliance and website performance risks.
- **Q2:** Establish consistent business reporting.
- **Q3:** Improve reporting reliability and customer-data controls.
- **Q4:** Assess readiness for future growth, including expansion into Nigeria.

### 3. Architecture Decision Records (ADRs)
Documents the key technical and business decisions, the alternatives considered, why they were rejected, the consequences of each decision and the conditions that would justify reconsidering them.

The three decisions cover:
- Using a MySQL read replica for reporting.
- Establishing controlled customer-data governance.
- Using scheduled incremental batch processing instead of continuous streaming.

### 4. Board Presentation
Summarises the ranked business problems, recommended strategy and quarterly roadmap. It also identifies information that could not be verified from the assignment brief, including the full extent of customer-data copies, the financial impact of website slowdowns, the causes of reporting differences and actual operating costs.

### 5. Improvement Beyond the Brief
Introduces the **Monday Figures Check**, a shared spreadsheet for Nana and Finance to compare business figures, record differences, assign responsibility and track follow-up.

The improvement provides a practical way to identify unresolved reporting differences and measure whether Nana's time spent rebuilding and checking figures is reduced.

## Overall Recommendation

Kloud Kart should establish reliable reporting and stronger control over its data before investing in advanced analytics, machine learning or real-time streaming. The recommended approach addresses current business risks while providing a manageable foundation for future growth.
