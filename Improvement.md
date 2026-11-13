# Deliverable 5: One Improvement Beyond the Brief

## Improvement: Monday Figures Check

### 1. The problem

Nana rebuilds her Monday figures from CSV exports, but Finance's spreadsheet never matches hers.

The roadmap addresses this by introducing shared reports and agreeing on how business figures should be calculated. However, even after those changes, differences may still occur because of missing orders, incorrect entries or other reporting problems.

I propose a **Monday Figures Check**, a simple spreadsheet that allows Nana and Finance to compare their figures, record differences and track the actions taken to resolve them.

### 2. What I will build

I will create a shared spreadsheet with the following fields:

| Details | Purpose |
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

### 3. How it will work

Every Monday:

1. Nana and Finance enter their figures for the same reporting period.
2. The spreadsheet automatically calculates the difference.
3. If the figures do not match, the reason is investigated and recorded.
4. A responsible person is assigned to resolve the issue.
5. Nana checks the status before presenting the figures to management.

The spreadsheet will show three possible results:

- **Matches:** Both figures are the same.
- **Investigated:** A difference was found, investigated and an action recorded.
- **Needs follow-up:** The difference still requires investigation or action.

A matching result does not automatically prove that the figure is correct. Nana and Finance must still use their agreed definitions and reporting periods.

### 4. Why this is valuable to Nana

This improvement will help Nana:

- See exactly which figures differ instead of searching through CSV files.
- Know who is responsible for investigating each difference.
- Track whether problems have been resolved.
- Check whether the figures agree before presenting them to management.

I will measure the time Nana currently spends rebuilding and checking her Monday figures. After introducing the spreadsheet, I will compare that time with the time she spends using the new process to see whether her workload has reduced.

### 5. What the improvement addresses

| Area | How it helps |
|---|---|
| Data management | Records differences and the actions taken to resolve them. |
| DataOps | Makes reporting problems visible and assigns responsibility for follow-up. |
| Orchestration | Establishes a regular Monday check between Nana and Finance. |

### 6. How I will know it has worked

The improvement will be successful when:

- Nana and Finance compare figures for the same reporting period and it tallies
- Differences are recorded instead of being overlooked.
- Every unresolved difference has a named person responsible for following it up.
- Nana can see whether the figures match before presenting them to management.
- The time Nana spends rebuilding and checking figures is reduced.

### 7. Why it is realistic

This improvement does not require another data hire, a new system or a separate warehouse. It can be built as a shared spreadsheet using the tools Kloud Kart already has.

The brief does not explain which figures disagree or why they differ. I will therefore begin by identifying the figures involved and investigating the causes rather than assuming what is wrong.

The spreadsheet gives Nana and Finance a practical way to track differences and their resolution. It adds a checking and follow-up step to the reporting process, helping management avoid relying on figures whose differences have not been explained.