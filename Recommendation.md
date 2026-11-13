# Kloud Kart: Data Strategy Recommendation

I recommend that Kloud Kart take three steps. First, agree and document the meaning of important business figures such as revenue so Nana and Finance can work from consistent definitions. Second, separate reporting from the live website by using the already approved second server to host a MySQL read replica. Third, introduce scheduled daily reports using this separate copy of the database. Stock information will remain in the live system because it must be current when customers place orders.

## 1. Architecture and Tools

Kloud Kart should use the already approved second server to host a MySQL read replica. The existing server will continue running the live website and main database, while the second server handles reporting queries. This separates reporting workloads from customer orders, reducing pressure on the live website. The Data Engineer must configure and test the replica before relying on it, including checking its performance and replication delay.

I recommend using the read replica as the initial reporting environment rather than immediately introducing a data warehouse. With approximately 40 GB of mainly structured data, a small technical team and a budget limited to two data hires, a warehouse would introduce additional costs and management responsibilities before a clear need has been established. Scheduled SQL reports can initially provide Nana and Finance with consistent figures without requiring another data platform.

**Tools required:**
- **MySQL read replica:** separates reporting from the live database.
- **SQL:** prepares data and calculates agreed business figures.
- **Limited Python:** supports automation where SQL is insufficient.
- **Scheduled jobs and basic alerts:** update reports daily and identify failures.
- **One BI tool:** allows Nana and Finance to access shared reports.

A managed cloud warehouse can be reconsidered if reporting requirements grow beyond what the replica and scheduled reports can reasonably support. A data lake or lakehouse would add even more complexity without a current business justification.

## 2. Processing Approach

Use an automatic daily batch process to extract new and changed reporting records from the read replica and prepare the reports. The process should include basic alerts to notify someone if an update fails.

Daily updates are sufficient for revenue, customer and management reports because these figures do not need second-by-second updates. General streaming would add costs and operational complexity without a demonstrated business benefit.

**Stock is the exception, but it does not require a separate streaming system.** The live MySQL database must remain the source of truth for stock. Customer orders must check and update inventory there because daily reporting figures may be outdated and must never determine whether an item is available.

Kloud Kart should introduce a warehouse or faster processing only when a specific business requirement justifies the additional cost and complexity and the need for a decision to be made.