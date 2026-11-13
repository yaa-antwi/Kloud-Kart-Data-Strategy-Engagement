# Kloud Kart: Data Strategy Engagement

## Project Overview

This project presents a practical 12-month data strategy for Kloud Kart, a growing e-commerce company in Accra, Ghana.

The strategy addresses three problems:

- Poor control over customer information and uncertainty about where copies are stored.
- Reporting activities slowing the live website.
- Inconsistent business figures between Nana and Finance.

The recommendation is designed around Kloud Kart's current size, one existing PHP/MySQL developer, a limit of two data hires and the need to keep the live website operating.

The central decision is to establish a MySQL read replica on the approved second server and use it for scheduled reporting. The company will not introduce a separate data warehouse or general streaming system initially.

## Deliverables

### 1. Situation Diagnosis

**File:** `Situation_Diagnosis.md`

Identifies and ranks Kloud Kart's three main data problems. Each problem is examined through:

- Root cause and business consequences.
- Potential financial and operational costs.
- Risk to the board conversation.
- Known facts, assumptions and information requiring investigation.

The ranking prioritises the Data Protection Commission complaint, followed by website performance and reporting consistency.

### 2. Recommendation and 12-Month Roadmap

**Files:** `Recommendation.md` and `Roadmap.md`

The recommendation establishes three priorities:

1. Agree and document the meaning of important business figures.
2. Use the approved second server to host a MySQL read replica, separating reporting workloads from the live website.
3. Produce scheduled daily reports from the replica for Nana and Finance.

The initial architecture does not include a separate warehouse or continuous streaming system. Those investments will be reconsidered only when a demonstrated business need justifies their cost and complexity.

The roadmap divides implementation into four quarterly business outcomes:

- **Q1:** Address immediate customer-data and website performance risks.
- **Q2:** Establish consistent business reporting.
- **Q3:** Improve reporting reliability and customer-data controls.
- **Q4:** Assess readiness for future growth, including expansion into Nigeria.

The recommendation also identifies the two roles to hire, their hiring order and their first-90-day responsibilities.

### 3. Architecture Decision Records

**Folder:** `decisions/`

Three ADRs document the important decisions, alternatives rejected, accepted trade-offs and conditions that would justify reconsidering each decision.

- `ADR-001.md` — Provision a second server and use a MySQL read replica for reporting.
- `ADR-002.md` — Establish controlled customer-data governance across company systems.
- `ADR-003.md` — Use scheduled daily batch reporting from the read replica.

The ADRs describe the same initial architecture as the recommendation. A separate reporting warehouse is a possible future investment, not part of the accepted first phase.

### 4. Board Presentation

**File:** `Board_Presentation.pptx`

Summarises the ranked problems, recommended strategy, quarterly outcomes and information that could not be verified from the brief.

The presentation is intended for Nana and the board. It focuses on business consequences and decisions rather than technical terminology.

### 5. Improvement Beyond the Brief

**File:** `Monday_Figures_Check.xlsx`

The Monday Figures Check is a shared spreadsheet for Nana and Finance to compare figures, record differences, assign responsibility and track follow-up.

It adds a visible checking and resolution process to the reporting arrangement. Its value will be measured by whether it reduces unexplained differences and the time Nana spends rebuilding and checking figures.

## Overall Recommendation

Kloud Kart should establish control over customer information, protect the live website from reporting workloads and agree on reliable business figures before investing in advanced analytics.

A read replica and scheduled daily reports provide a manageable starting point. The company should invest in a warehouse, forecasting or faster processing only when a specific business requirement demonstrates that the existing arrangement is insufficient.

## Important Assumptions and Limitations

The brief does not provide:

- Actual financial losses caused by website slowdowns.
- The time Nana and Finance spend rebuilding and reconciling reports.
- The full locations and number of customer-data copies.
- The exact cause of the reporting differences.
- Supplier quotations or confirmed infrastructure costs.
- The acceptable replication delay for reporting.

These items must be measured or confirmed during implementation. Planning cost estimates are not supplier quotations or approved expenditure.