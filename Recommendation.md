# Kloud Kart: Data Strategy Recommendation

## Recommendation

I recommend that Kloud Kart address its current data problems in three steps.

First, establish control over customer information by identifying where copies are stored, assigning responsibility and controlling who can access them.

Second, separate reporting from the live website by using the already approved second server to host a MySQL read replica.

Third, agree on how important business figures such as revenue are calculated and provide Nana and Finance with shared daily reports from the replica.

I do not recommend introducing a separate data warehouse or continuous streaming system at this stage. Kloud Kart needs reliable reporting and stronger data controls before investing in more advanced technology.

## 1. Architecture and Tools

Kloud Kart should provision the approved second server and configure it as a MySQL read replica.

The existing production server will continue to run the live website and main database. The second server will hold a replicated copy of the database and handle reporting queries and exports.

This separates large reporting workloads from customer transactions, reducing the risk of reports competing with the live website for server resources.

The Data Engineer must configure and test replication before reporting is moved. Testing should confirm that:

- The replica receives changes from the production database.
- Reporting queries do not interfere with live website operations.
- Replication delays are monitored.
- Failed replication or reporting updates are detected.
- Reports display when their data was last updated.

The replica is a reporting copy, not the authority for live stock availability.

### Why Not a Warehouse Initially?

I recommend using the MySQL read replica as the initial reporting environment rather than immediately introducing a separate data warehouse.

Kloud Kart has approximately 40 GB of mainly structured data, a small technical team and a limit of two data hires. Its immediate reporting problem is that Nana and Finance produce conflicting figures and large exports slow the live website.

A warehouse could provide a more specialised reporting environment, but Kloud Kart has not demonstrated that its current reporting requirements need one. Introducing another platform would add infrastructure, data movement, monitoring, access controls and operating costs.

The read replica addresses the immediate performance problem. Scheduled SQL reports address the need for consistent daily figures.

A warehouse can be reconsidered if reporting becomes too complex or demanding for the replica and the business can demonstrate that the additional investment is worthwhile.

### Tools Required

- **MySQL read replica:** Separates reporting workloads from the live production database.
- **SQL:** Calculates agreed business figures and prepares shared reports.
- **Limited Python:** Supports automation where SQL alone is insufficient.
- **Scheduled jobs and basic alerts:** Run daily reporting tasks and identify failures.
- **One BI or reporting tool:** Gives Nana and Finance access to shared reports. The company should use an existing suitable tool or a low-cost option before purchasing an expensive platform.

The company should not purchase Snowflake, BigQuery or a lakehouse simply because they are on the investor or developer wish list.

## 2. Processing Approach

Use scheduled daily batch processing to produce the main business reports from the read replica.

The reporting process should:

1. Run at an agreed time each day.
2. Read the required reporting data from the replica.
3. Apply the definitions approved by Nana and Finance.
4. Produce shared reports.
5. Record whether the update succeeded and when the report was last refreshed.
6. Alert the responsible person if an update fails.

The first implementation should use straightforward scheduled SQL queries and reporting outputs. Incremental processing can be introduced where a reliable method of identifying new and changed records has been designed and tested.

General streaming is not justified because the brief states that most information can refresh daily.

### Stock Must Remain Current

Stock is the exception. It cannot depend on daily reporting because outdated stock figures could cause Kloud Kart to oversell products.

The production MySQL database must remain the source of truth for inventory.

Every order must check and reserve stock against the live database within a transaction. The stock update should only succeed if sufficient quantity remains.

For example, the application can perform a conditional update:

`UPDATE inventory SET quantity = quantity - requested_quantity WHERE product_id = requested_product AND quantity >= requested_quantity;`

The application must check whether the update affected a row. If no row was updated, sufficient stock was not available and the order must not be confirmed as having reserved that stock.

The order and stock changes should be handled within an appropriate database transaction so that a failed order does not leave inventory incorrectly reduced.

This control prevents two customers from successfully reserving the same remaining stock at the same time.

The read replica must never decide whether a product is available for purchase. Its reporting data may be delayed.

## 3. Customer-Data Governance

The new reporting environment must not create uncontrolled copies of customer information.

Kloud Kart should establish a customer-data register covering the production database, read replica, Marketing exports, Finance spreadsheets, Operations files, email attachments and any other identified locations.

Each recorded location should include:

- Department and responsible owner.
- Purpose for holding the information.
- Type of customer information stored.
- Authorised users or roles.
- Whether information is exported or copied elsewhere.
- Retention period or review date.
- How access, correction and deletion requests are handled.

### Access Controls

Access should follow the principle of least privilege: employees should only access the customer information required for their work.

In practice:

- Use individual accounts rather than shared logins.
- Give access according to job responsibilities.
- Restrict the approximately 300,000-person Marketing list to authorised Marketing staff.
- Mask or remove fields from working exports when users do not need the full customer information.
- Require approval before creating new customer-data exports.
- Record who created an export, when it was created, its purpose and where it was stored.
- Review access regularly and remove permissions when they are no longer required.
- Protect data transfers and stored copies using appropriate security controls.

### Retention and Deletion

Kloud Kart should document a process for handling customer requests.

1. Verify and record the request.
2. Identify the customer's information in the known systems and copies.
3. Identify the departments and owners responsible for those locations.
4. Assess whether any information must be retained under applicable legal or business obligations. Obtain legal advice where necessary.
5. Delete or restrict information where required and permitted.
6. Record the location checked, action taken, responsible person and any outstanding issue.
7. Ensure that future restoration of backups does not silently reintroduce information that should remain deleted. Backup retention and restoration procedures must be documented.
8. Provide a response that accurately explains what was done and any information that must legitimately be retained.

The company should confirm its detailed retention rules and legal obligations with appropriate legal advice. A deletion request must not be treated as an instruction to erase every business record without assessing applicable requirements.

The Data Protection Commission complaint should be handled immediately. The company must not wait for the new reporting architecture to be completed before investigating and responding.

## 4. Roles to Hire and First 90 Days

The two roles should be hired in the following order.

### First Hire: Data Engineer

The Data Engineer should be hired first because Kloud Kart must establish control over customer information and separate reporting workloads from the live production database.

**First 30 days**

- Review the existing MySQL environment with the PHP/MySQL developer.
- Identify known locations where customer information is stored.
- Work with departmental owners to create the customer-data register.
- Review access to the Marketing customer list and identify uncontrolled copies.
- Assess the approved second server and prepare the replica design.

**Days 31–60**

- Provision and configure the MySQL read replica.
- Test replication, reporting queries and failure recovery.
- Establish monitoring for replication delays and failures.
- Introduce appropriate access controls for the replica and reporting users.
- Document how new data copies and exports are recorded.

**Days 61–90**

- Move large reporting exports to the replica after testing confirms it is suitable.
- Record website response times before and after the change.
- Test the reporting process and document outstanding problems.
- Support the customer-data request process and confirm that known locations and owners are recorded.

### Second Hire: Analytics Engineer

The Analytics Engineer should be hired second, once the reporting environment is available and its data can be used safely.

**First 30 days**

- Meet Nana and Finance to identify the figures that disagree.
- Document the current calculations and reporting periods.
- Agree which business definitions need approval.
- Identify the source data required for the shared reports.

**Days 31–60**

- Build SQL queries using the read replica.
- Validate the calculations with Nana and Finance.
- Create shared reports for the agreed business figures.
- Replace separate manual calculations where the new reports have been verified.

**Days 61–90**

- Schedule the daily reporting process.
- Add checks for missing, duplicated or inconsistent reporting data.
- Ensure reports display their last update time.
- Introduce failure alerts and document who investigates problems.
- Measure whether Nana's time spent rebuilding and checking Monday figures has reduced.

The two roles have different responsibilities. The Data Engineer establishes and protects the reporting environment. The Analytics Engineer makes the information useful and consistent for management.

## 5. Indicative Cost and Financial Justification

The brief confirms that a second server or read replica is pre-approved, but it does not provide supplier quotations, hosting specifications or confirmed operating costs.

The following figures are therefore planning estimates, not confirmed prices.

For board planning, assume a modest cloud-hosted second server with enough capacity for a 40 GB database, reporting queries, backups and monitoring.

| Cost item | Indicative monthly estimate (USD) | Reason |
|---|---:|---|
| Second server / replica hosting | $100–$250 | Provides a separate environment for replicated data and reporting queries. |
| Backup storage and retention | $20–$75 | Protects the reporting environment and its recoverability. |
| Monitoring and basic reporting tools | $0–$50 | Supports failure alerts and access to shared reports, assuming low-cost or existing tools. |
| **Indicative total** | **$120–$375 per month** | **Approximately $1,440–$4,500 per year.** |

These estimates exclude the salaries of the two data hires, any one-off hardware purchase, taxes, additional network charges and unexpected capacity increases. The final amount must be confirmed through supplier quotations and a capacity assessment.

A separate managed warehouse could add several hundred dollars per month or more, depending on data volume, query activity, storage, data movement and licensing. A planning allowance of approximately $200–$800+ per month can be used for initial comparison, but this is not a supplier quote and does not include the extra engineering and monitoring effort.

The decision is not that a warehouse is always too expensive. It is that Kloud Kart has not yet demonstrated a business requirement that justifies paying for and operating another platform.

The read replica has a clearer immediate purpose: moving reporting workloads away from the live website.

The company should compare the actual infrastructure cost with the cost of website incidents, manual reporting work and the effort required to manage customer-data copies.

## 6. When to Reconsider the Architecture

Kloud Kart should review the initial arrangement if:

- The replica cannot support reporting workloads.
- Replication delays repeatedly make reports unsuitable for management decisions.
- Reporting requirements become too complex for scheduled SQL queries.
- The volume of data or number of users makes the current arrangement difficult to maintain.
- Expansion into Nigeria creates new data, reporting or compliance requirements.

A warehouse should be considered when the company can identify a specific reporting need that the replica cannot reasonably support.

Faster reporting should be considered only when a specific business decision cannot be supported by daily reports and the cost of waiting until the next update can be demonstrated.

Any additional investment must show that its business benefit justifies the extra infrastructure, operating and monitoring costs.

## Conclusion

Kloud Kart should establish stronger customer-data controls, separate reporting from the live website and give Nana and Finance one agreed source of business figures.

The approved second server and MySQL read replica provide a practical starting point. Scheduled daily reports meet the current reporting need without introducing a separate warehouse or general streaming system.

This approach addresses the problems Kloud Kart has today while leaving room to invest in more advanced capabilities when the business can justify them.