# Deliverable 1: Situation Diagnosis — Kloud Kart

## 1. Identification, Cost and Ranking of Problems

| Rank | Identified problem | Potential cost to Kloud Kart | Why it matters to the board |
|---|---|---|---|
| 1 | Poor customer-data governance | Staff time spent locating customer information and responding to deletion requests, alongside potential regulatory, legal and reputational exposure. | The Data Protection Commission complaint creates a 90-day response deadline. Kloud Kart must demonstrate that it can identify relevant customer-data locations and explain what action was taken. |
| 2 | Website performance slowdowns | Potential lost orders, customer dissatisfaction and developer time spent investigating performance incidents. | Monday exports have slowed the live website twice in the last month. This creates an existing risk to sales and customer confidence. |
| 3 | Inconsistent business reporting | Staff time spent rebuilding and reconciling reports, alongside the risk of decisions based on conflicting figures. | Nana's figures do not match Finance's figures. This weakens confidence in management reporting and information presented to investors. |

### Ranking Rationale

I ranked the problems using four considerations:

1. **Deadline:** Is there an external deadline Kloud Kart cannot control?
2. **Current impact:** Is the problem already affecting operations?
3. **Reversibility:** How difficult would the consequences be to undo?
4. **Board credibility:** If the problem remains unresolved at the next board conversation, how seriously could it damage confidence in the company's ability to manage its data?

Customer-data governance ranks first because of the active complaint and the 90-day response deadline. Website performance ranks second because the problem has already affected the live service. Reporting inconsistency ranks third because the case establishes wasted work and conflicting figures, but does not establish that an incorrect business decision or direct financial loss has already occurred.

## 2. Detailed Problem Analysis

### 2.1 Poor Customer-Data Governance

**Root Cause**

Marketing exports a customer list containing approximately 300,000 people without tracking how many copies exist or where they are stored.

This indicates a lack of ownership and control over how customer information is distributed, stored, accessed and retained. The problem is not simply that Marketing creates exports. It is that Kloud Kart cannot reliably account for those copies or identify who is responsible for them.

Consequently, when a customer requests deletion, the company may struggle to identify all relevant locations and demonstrate what action was taken.

**Compliance**

The Ghana Data Protection Act, 2012 (Act 843), establishes requirements for organisations that process personal data. These include registration obligations, data-protection principles and individual rights.

Relevant principles include lawful processing, openness, purpose limitation, data minimisation, accuracy, storage limitation and security.

A deletion request does not automatically mean that every record associated with a customer must be erased. Kloud Kart must assess the request, identify the relevant information, consider any applicable legal retention obligations and obtain appropriate legal advice where necessary.

The immediate concern is that untracked exports make this assessment difficult. The company has 90 days to respond to the Data Protection Commission complaint and must be able to explain where the customer's information was held and what action was taken.

**Ranked Findings**

1. The Data Protection Commission complaint creates an immediate response deadline.
2. Marketing's untracked exports make it difficult to identify where customer information is stored.
3. The absence of a reliable copy register makes it harder to demonstrate how deletion requests have been handled.
4. Additional reporting systems or servers could create more customer-data copies unless they are included in the governance process.

**Assumptions and Unknowns**

- The number and locations of customer-data copies are unknown.
- It has not been confirmed whether the customer involved in the complaint appears in Marketing exports, Nana's CSV files, Finance spreadsheets, email attachments or backups.
- Kloud Kart's Data Protection Commission registration status is unknown.
- The person responsible for coordinating customer-data requests has not been identified.
- Applicable retention requirements for the customer's records have not been confirmed.

**Cost Assessment**

- **Wasted labour:** Staff time spent locating customer information, investigating copies and responding to requests takes time away from their other responsibilities.
- **Direct financial loss:** No direct financial loss has been established from the information provided.
- **Risk-weighted exposure:** If Kloud Kart cannot demonstrate appropriate handling of customer information, the complaint could escalate and create legal, regulatory, management and reputational costs.

The financial exposure should be assessed using:

`Staff hours spent investigating and responding × estimated staff cost per hour`

Any legal, regulatory or reputational exposure should be assessed separately rather than presented as a confirmed financial loss.

At the low end, the complaint is resolved with a documented response. At the high end, an incomplete response could require further investigation, legal support and management attention while the company is accountable to investors.

**Risk Ranking Justification**

This problem ranks first because the 90-day deadline is outside Kloud Kart's control and the company currently lacks a reliable record of customer-data copies.

A missed or inadequate response could damage confidence in the company's ability to manage personal information. The consequences may also be difficult to reverse once regulatory or customer trust has been affected.

### 2.2 Website Performance Slowdowns

**Root Cause**

Kloud Kart hosts its live website and MySQL database on the same server.

Nana's Monday exports retrieve hundreds of thousands of records from that database. Reporting queries therefore compete with live website transactions for shared resources, such as processor time, memory and database capacity.

This resource contention is the likely explanation for the slowdowns. However, the exact technical bottleneck has not been confirmed and must be measured before implementation.

The underlying constraint is that the company uses the same production environment for two different workloads: serving customer orders and producing large reports.

**Ranked Findings**

1. Monday exports have slowed the live website twice in the last month.
2. Reporting workloads and live customer transactions depend on the same server and database resources.
3. Continued growth could increase resource demand and make further slowdowns more likely.

**Assumptions and Unknowns**

- Shared-resource contention is the likely cause, but the exact bottleneck has not been confirmed.
- The number of customers affected and the duration of the slowdowns are unknown.
- The number and value of potentially lost orders have not been established.
- Average order value and website conversion rates are unknown.
- The capacity and suitability of the approved second server have not been confirmed.

**Cost Assessment**

- **Wasted labour:** Developer time may be spent investigating and resolving performance incidents.
- **Direct financial loss:** Slow website responses may cause customers to abandon purchases, resulting in potential lost sales. The actual amount is unknown.
- **Risk-weighted exposure:** Repeated slowdowns could reduce sales, damage customer confidence and interrupt normal operations.

A practical estimate of potential lost sales is:

`Estimated affected orders × average order value`

The estimate must use incident records and sales data. It should not be presented as an actual loss until the number of affected orders has been established.

Developer time can be estimated using:

`Incident investigation and recovery hours × developer cost per hour`

**Risk Ranking Justification**

This problem ranks second because it has already affected a production service twice in one month. Unlike reporting inconsistency, it can directly affect customers attempting to place orders.

It ranks below customer-data governance because the active complaint creates a defined external deadline and potential compliance consequences. However, it requires early action because another slowdown could affect revenue and customer confidence.

### 2.3 Inconsistent Business Reporting

**Root Cause**

Nana rebuilds her Monday figures from CSV exports, while Finance produces a separate spreadsheet. Their figures do not match.

The underlying cause has not yet been established. Possible explanations include different definitions, reporting periods, data selection, extraction times or spreadsheet calculations.

A likely contributing weakness is the absence of one agreed and owned reporting process. If Nana and Finance use different rules to calculate revenue or count orders, they can produce different figures even when they start with the same database.

Manual spreadsheet calculations also make the results harder to reproduce and check.

**Ranked Findings**

1. Nana's figures do not match Finance's figures.
2. Both teams rebuild reports independently instead of using one agreed reporting process.
3. The reasons for the differences have not been established.
4. Manual calculations make the reports harder to reproduce, verify and maintain.

**Assumptions and Unknowns**

- The exact figures that disagree have not been identified.
- The reasons for the differences have not been confirmed.
- Differences may arise from calculation methods, reporting periods, data selection, extraction times or spreadsheet formulas.
- The time spent rebuilding and reconciling reports is unknown.
- It has not been established whether conflicting figures have affected business decisions.

**Cost Assessment**

- **Wasted labour:** Nana and Finance spend time rebuilding and checking reports rather than focusing on their other responsibilities.
- **Direct financial loss:** No direct financial loss has been established. However, decisions based on incorrect figures could lead to poor budgeting, planning or operational choices.
- **Risk-weighted exposure:** Conflicting figures could weaken management's confidence in reporting and investors' confidence in Kloud Kart's ability to explain its performance.

The labour cost should be estimated using:

`Weekly hours spent rebuilding and reconciling reports × staff cost per hour × 52`

The company should first measure the actual time Nana and Finance spend on this work. The case does not provide enough information to assign a reliable monetary amount.

**Risk Ranking Justification**

This problem ranks third because it creates wasted labour and uncertainty, but the case does not establish a direct financial loss or an incorrect business decision.

It remains important because management and investors need consistent figures to assess performance and guide business growth. Agreeing on definitions and providing shared reports should reduce the opportunity for departments to produce conflicting results.

## 3. Overall Diagnosis

Kloud Kart's immediate challenge is not a lack of advanced data technology.

It is the lack of sufficient control over customer information, separation between reporting and live operations, and consistency in business reporting.

The problems have different causes and therefore require different responses:

- Customer-data governance requires ownership, access controls, a copy register and documented request-handling procedures.
- Website performance requires reporting workloads to be separated from the production database.
- Reporting inconsistency requires agreed definitions and a shared reporting process.

These foundational problems should be addressed before Kloud Kart invests heavily in a warehouse, machine learning or real-time streaming.

## 4. Information That Must Be Verified

The brief does not provide enough evidence to calculate actual financial losses or confirm every root cause.

During implementation, Kloud Kart should establish:

- Where customer information and exported copies are held.
- The time spent locating and responding to customer-data requests.
- The actual cause, duration and customer impact of website slowdowns.
- The figures that disagree between Nana and Finance and the reasons for those differences.
- The time Nana and Finance spend rebuilding and reconciling reports.
- The actual infrastructure and operating costs of the proposed solution.

These measurements will allow management to compare the cost of the problems with the cost of addressing them.