# Deliverable 5: One Improvement Beyond the Brief

## Improvement: Monday Figures Check

### 1. The Problem

Nana rebuilds her Monday figures from CSV exports, but Finance's spreadsheet never matches hers.

The roadmap addresses this by introducing shared reports and agreeing on how business figures should be calculated. However, even after these changes, differences may still occur because of missing records, incorrect entries or reporting problems.

I propose a **Monday Figures Check**, a shared spreadsheet that allows Nana and Finance to compare their figures, record differences and track the actions taken to resolve them.

The improvement adds a visible checking and follow-up process rather than assuming that producing a shared report automatically guarantees correct figures.

### 2. What I Will Build

I will create a shared spreadsheet with the following fields:

| Field | Purpose |
|---|---|
| Reporting period | Ensures both figures cover the same dates. |
| Business figure | Identifies what is being compared, such as revenue or order count. |
| Nana's figure | Records the figure from Nana's report. |
| Finance's figure | Records the figure from Finance's records. |
| Difference | Automatically calculates the difference between the two figures. |
| Reason for difference | Records why the figures do not match. |
| Person responsible | Identifies who will investigate the difference. |
| Action taken | Records what was done to address it. |
| Status | Shows whether the figures match or still need follow-up. |
| Follow-up date | Records when an unresolved issue should be reviewed again. |

The spreadsheet will calculate the difference automatically rather than requiring Nana or Finance to work it out manually.

### 3. How It Will Work

Every Monday:

1. Nana and Finance enter their figures for the same reporting period.
2. The spreadsheet automatically calculates the difference.
3. If the figures differ, the reason is investigated and recorded.
4. A responsible person is assigned to resolve the difference.
5. Nana checks the status before presenting the figures to management.

The spreadsheet will use three statuses:

- **Matches:** The figures are equal using the agreed definitions and reporting period.
- **Investigated:** A difference was found, investigated and an action recorded.
- **Needs follow-up:** The difference still requires investigation or action.

A matching result does not automatically prove that the figure is correct. Nana and Finance must still use their agreed definitions and reporting periods.

An unexplained difference must not be treated as resolved simply because someone has recorded it.

### 4. Why This Is Valuable to Nana

This improvement will help Nana:

- See exactly which figures differ instead of searching through CSV files.
- Know who is responsible for investigating each difference.
- Track whether problems have been resolved.
- Check the status of figures before presenting them to management.
- Spend less time rebuilding and reconciling reports.

The improvement should reduce the effort Nana spends finding differences and chasing people for explanations.

### 5. How I Will Measure Its Value

Before introducing the spreadsheet, I will record how much time Nana spends rebuilding and checking her Monday figures.

After introducing the process, I will compare that time with the time she spends using the new spreadsheet and shared reports.

I will also measure:

- The number of differences identified.
- The number of differences investigated.
- The number of unresolved differences.
- The number of unresolved differences with a named owner.
- The time taken to resolve reporting differences.

The purpose is not simply to make the figures match. It is to make differences visible, explainable and assigned to someone for action.

### 6. What the Improvement Addresses

| Area | How it helps |
|---|---|
| Data management | Records differences and the actions taken to resolve them. |
| DataOps | Makes reporting problems visible and assigns responsibility for follow-up. |
| Orchestration | Establishes a regular Monday checking process between Nana and Finance. |

### 7. How I Will Know It Has Worked

The improvement will be successful when:

- Nana and Finance compare figures using the same agreed definitions and reporting period.
- Differences are recorded instead of being overlooked.
- Every unresolved difference has a named person responsible for following it up.
- Nana can see whether differences have been resolved before presenting figures to management.
- The time Nana spends rebuilding and checking reports is reduced.

A matching result alone is not proof that the figures are correct. The underlying reporting definitions and source data must also be checked.

### 8. Why It Is Realistic

This improvement does not require another data hire, a new data platform or a separate warehouse.

It can be built as a shared spreadsheet using tools Kloud Kart already has.

The brief does not explain which figures disagree or why they differ. I will therefore begin by identifying the figures involved and investigating the causes rather than assuming what is wrong.

The Monday Figures Check gives Nana and Finance a practical way to record differences, assign responsibility and follow up on unresolved issues.

It adds a checking step to the reporting process and helps management avoid relying on figures whose differences have not been explained.