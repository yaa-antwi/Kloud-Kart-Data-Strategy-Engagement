# ADR-002: Establish Controlled Customer-Data Governance Across Company Systems

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Data Consultant (Kloud Kart engagement)

## Context

Kloud Kart holds customer information across its business systems, including a Marketing customer list of approximately 300,000 people.

The company does not have a reliable record of where copies of this information are stored or who is responsible for them.

The company is also dealing with a Data Protection Commission complaint involving a customer's request for deletion and must respond within 90 days.

The introduction of a read replica will create another location containing customer information. Without clear ownership and procedures, Kloud Kart may struggle to locate, protect or act on customer information when required.

## Decision

Establish a company-wide customer-data governance process that records where customer information is stored, assigns responsibility to the relevant departments and controls who can access it.

The process must cover the production database, read replica, Marketing exports, Finance spreadsheets, Operations files, email attachments, backups and any other identified locations.

Each known location must have:

- A responsible department and owner.
- A stated purpose for holding customer information.
- A description of the information stored.
- A list of authorised users or roles.
- A record of exports and further copies.
- A retention period or review date.
- A documented process for access, correction and deletion requests.

### Access and Copy Controls

Access must follow least privilege. Employees should only have access to the customer information required for their responsibilities.

Kloud Kart should:

- Use individual accounts instead of shared logins.
- Assign access according to job responsibilities.
- Restrict the approximately 300,000-person Marketing list to authorised Marketing staff.
- Mask or remove customer fields from working exports when full details are not needed.
- Require approval before creating new customer-data exports.
- Record who created an export, when it was created, why it was needed and where it was stored.
- Review permissions regularly and remove access when it is no longer required.
- Protect stored information and data transfers using appropriate security controls.

### Retention and Deletion Controls

Kloud Kart must document a process for handling customer requests.

1. Verify and record the request.
2. Identify the customer's information in known systems and copies.
3. Contact the responsible departmental owners.
4. Assess applicable legal and business retention requirements.
5. Delete or restrict information where required and permitted.
6. Record each location checked, the action taken, the responsible person and any outstanding issue.
7. Document how backups are retained and how restoration is handled so that information that should remain deleted is not silently reintroduced.
8. Provide an accurate response explaining what was done and any information that must legitimately be retained.

The detailed retention schedule and legal requirements must be confirmed with appropriate legal advice.

## Alternatives Considered

### Alternative A: Allow Each Department to Manage Its Own Customer Information

- **How it would work:** Marketing, Finance and Operations would continue managing their own customer-data files and copies. Each department would decide who can access its information and how requests are handled.
- **Why it is attractive:** Departments understand their own work and can manage their information without waiting for a central process. It also avoids the immediate effort of creating a company-wide register and assigning governance responsibilities.
- **Why rejected:** Kloud Kart already does not know where all customer-data copies are stored. Continuing with separate departmental arrangements makes it harder to identify every relevant copy when a customer requests deletion or when the company investigates a complaint. It also makes consistent oversight difficult.

### Alternative B: Keep Customer Information Only in One Central System

- **How it would work:** Move all customer information into one central database and require departments to access it from there instead of maintaining separate copies.
- **Why it is attractive:** It could reduce the number of locations containing customer information and make access control and deletion easier to coordinate.
- **Why rejected:** Departments may still need information in different systems to perform their work. Moving everything into one system would require significant changes and would not automatically remove existing copies. Kloud Kart must first identify and control its current data locations rather than assume that centralisation alone solves the problem.

## Consequences

- **What this buys:** Kloud Kart gains a clearer record of where customer information is held, who is responsible for it and how requests are handled. This improves the company's ability to investigate complaints, control access and demonstrate the actions taken when responding to customer requests.
- **What this costs:** Departments must help identify their data locations, maintain accurate records and follow common procedures. Management must assign responsibility and review whether the controls are followed. The process takes time away from other departmental work.
- **What it costs the client if I am wrong:** If the register is incomplete or departments fail to report their copies, Kloud Kart could overlook customer information when responding to a deletion request. This could result in an incomplete response to the Data Protection Commission, further regulatory consequences and damage to customer trust.
- **What would make me revisit this:** Revisit the governance arrangement if new systems, departments or countries introduce data locations that the current process cannot adequately track. Reconsider the controls if deletion requests repeatedly reveal unknown copies or access reviews show that departments cannot manage their responsibilities effectively.

## What This Survives

This decision provides a governance process that can cover the production database, read replica, Marketing files, Finance spreadsheets and future systems.

It does not depend on all customer information being stored in one place.

As Kloud Kart grows, new systems and departments must be included in the register and assigned clear responsibility before their customer information is used.