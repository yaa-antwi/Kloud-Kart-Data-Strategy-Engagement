# ADR-001: Provision a Second Server and Use a MySQL Read Replica for Reporting

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Kloud Kart leadership

## Context

Kloud Kart stores orders, inventory and customer accounts in one MySQL database on the same server as its live website.

Large Monday reporting exports have slowed the website twice in one month because reporting queries compete with live operations for server resources.

The company has approval to provision a second server or establish a read replica. However, this does not mean the second server or replica is already running.

Kloud Kart has one existing PHP/MySQL developer and a budget for only two data hires. The solution must therefore reduce the current performance risk without introducing more technology than the team can manage.

## Decision

Provision the approved second server and configure a MySQL read replica for reporting.

Direct large reporting queries and data exports to the replica. Keep the production database responsible for live website operations, customer orders and stock transactions.

The initial reporting environment will be the read replica itself. A separate reporting warehouse is not included in this first phase.

The replica must be tested before reporting workloads are moved. Replication delay, failures and recovery procedures must be monitored and documented.

## Alternatives Considered

### Alternative A: Keep Reporting on Production and Schedule or Throttle Exports

- **How it would work:** Continue using the existing database for reporting, but run large exports during quieter hours and limit the resources they consume.
- **Why it is attractive:** It avoids the cost of another server, requires no replication setup and does not create another copy of customer information. It could also be implemented more quickly.
- **Why rejected:** Kloud Kart has already experienced two website slowdowns caused by reporting work. Scheduling exports for quieter hours reduces the likelihood of another slowdown but does not remove competition for resources. As order volumes grow, the problem could return.

### Alternative B: Extract Data Directly from Production into a Managed Cloud Warehouse

- **How it would work:** Connect a warehouse extraction process directly to the production MySQL database and load reporting data into the warehouse on a schedule.
- **Why it is attractive:** It creates a specialised reporting environment and could support more complex reporting as the company grows.
- **Why rejected:** The extraction process would still place reporting workloads on the database supporting the live website. The warehouse separates reporting after extraction, but it does not prevent extraction itself from affecting production. Kloud Kart should first remove that risk by separating reporting workloads through a replica. A warehouse has not yet been justified by the current reporting requirements.

## Consequences

- **What this buys:** Reporting queries and large exports are separated from the production database. This reduces the risk of reporting work slowing the live website and gives the company a separate environment for reporting.
- **What this costs:** Kloud Kart must pay to provision and operate the second server. The team must configure and monitor replication, investigate failures and manage another copy of customer information. This additional copy increases data-protection and deletion responsibilities.
- **What it costs the client if I am wrong:** If the replica cannot handle reporting workloads or repeatedly falls behind, Nana may still receive delayed reports and have to rely on manual exports. If reports do not show their last update time, management could make decisions using outdated figures.
- **What would make me revisit this:** Revisit the design if replication repeatedly falls behind, the replica cannot support reporting demand, or maintenance becomes too difficult for the available team. Significant growth during the Nigeria expansion may also justify reviewing the architecture.

## What This Survives

This decision separates reporting activity from the production database as order volumes increase.

It gives Kloud Kart a manageable starting point without requiring a warehouse immediately.

The decision does not guarantee that the replica is always up to date. Replication must be monitored, reports must display their last update time and live stock decisions must remain on production MySQL.