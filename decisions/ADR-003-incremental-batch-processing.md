# ADR-003: Use Scheduled Daily Batch Reporting from the MySQL Read Replica

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Data Consultant (Kloud Kart engagement)

## Context

Kloud Kart needs reliable reporting for revenue, customers and management decisions.

Nana currently rebuilds Monday figures from large CSV exports, while Finance produces different figures using spreadsheets.

Most reporting requirements do not need second-by-second updates. The company has only two data hires and must avoid introducing a processing system that requires more monitoring and operational support than the team can provide.

The approved MySQL read replica will provide a separate environment for reporting. The company has not demonstrated a current need for a separate warehouse or continuous streaming system.

Stock is different because inventory must remain current when customers place orders. Stock decisions must continue to use the live production database.

## Decision

Use scheduled daily batch reporting directly from the MySQL read replica.

The process will:

1. Run at an agreed time each day.
2. Read the required reporting data from the replica.
3. Apply the business definitions approved by Nana and Finance.
4. Produce shared reports.
5. Record whether the update succeeded and when the report was last refreshed.
6. Alert the responsible person if an update fails.

The initial implementation should use scheduled SQL queries and straightforward reporting outputs.

Incremental processing may be introduced where a reliable method of identifying new and changed records has been designed and tested. It must not be assumed to exist before that mechanism has been established.

No separate reporting warehouse or general streaming system will be introduced in the initial phase.

## Alternatives Considered

### Alternative A: Run a Full Nightly Extract of the Reporting Data

- **How it would work:** Extract the full reporting dataset from the read replica every night and reload or replace the reporting output with the latest data.
- **Why it is attractive:** It is straightforward to understand and implement. The team does not need to track which records have changed since the previous run.
- **Why rejected:** Repeatedly extracting the full dataset can waste processing time and resources as the database grows. Kloud Kart should first identify the reporting data required and use scheduled SQL queries to produce the necessary outputs. A full extract may be reconsidered if it proves simpler or more reliable for a particular report.

### Alternative B: Use Continuous Streaming to Update Reports

- **How it would work:** Capture database changes continuously and send them to a reporting environment as transactions occur.
- **Why it is attractive:** Reports can reflect new transactions much sooner than daily batch processing. This could support decisions that genuinely depend on current information and may appeal to investors requesting real-time analytics.
- **Why rejected:** Kloud Kart's main reporting requirements do not currently justify continuous updates. Streaming introduces additional complexity around failed events, duplicates, ordering and monitoring. A two-person data team would have to support this system even though most business reports only need daily updates.

## Consequences

- **What this buys:** Scheduled daily reporting gives Nana and Finance consistent figures without requiring them to rebuild large CSV reports independently. It avoids the need to operate a separate warehouse or continuous streaming system at this stage.
- **What this costs:** Reports will not show every transaction immediately. The team must schedule and monitor reporting jobs, handle failed runs and check that records are not missing or incorrectly included.
- **What it costs the client if I am wrong:** If management makes a decision that depends on information more recent than the daily update, it could act on incomplete figures. Nana might present outdated revenue or customer figures, and management could miss a developing business problem because the latest transactions have not yet appeared in the report.
- **What would make me revisit this:** Revisit the schedule if management identifies a business decision that cannot wait for the next daily update, or if the reporting process cannot complete reliably within the available reporting window. Any move towards more frequent processing must demonstrate a clear business benefit that justifies the additional operating and monitoring costs.

## What This Survives

Scheduled daily reporting can support Kloud Kart's current management needs without requiring a separate warehouse or continuous streaming system.

As order volumes grow, the company can improve the reporting process or introduce more frequent batches if the evidence justifies the investment.

If future requirements demand faster reporting, Kloud Kart can evaluate change-capture technology or a warehouse without immediately committing to streaming across the entire data environment.

Stock availability remains separate from this decision. Live customer orders must continue checking and reserving stock against production MySQL, never against a daily reporting output or delayed replica.