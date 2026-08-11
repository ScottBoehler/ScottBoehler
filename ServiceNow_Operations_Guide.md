# ServiceNow Operations Guide
### IT Service Management | Platform Overview for Operations Leaders

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** July 2026  
**Applies To:** Operations leaders, Service Delivery Managers, and IT professionals transitioning to ServiceNow from legacy ITSM platforms or building ServiceNow-based service management practices from scratch

---

## Purpose & Scope

ServiceNow is the de facto standard for enterprise IT service management. If you are managing a service desk, running a 24x7x365 operations team, or governing a change management process at scale, ServiceNow is almost certainly the platform you are working in or will be working in.

This guide is written for operations leaders — not developers, not ServiceNow administrators. It covers what ServiceNow does, how its core modules work together, and how an experienced operations leader uses the platform to run a service management function. It does not cover platform configuration, scripting, or development — those are the ServiceNow administrator's domain. What it covers is everything the SDM, Incident Commander, Change Manager, or Problem Manager needs to know to operate effectively in the platform.

One important note on context. Much of the operational knowledge in this guide was developed through hands-on experience with BMC Remedy — the enterprise ITSM platform that preceded ServiceNow as the industry standard. Remedy and ServiceNow share the same underlying ITIL data model. The process logic, the record types, the escalation mechanics — they are the same. ServiceNow delivers them through a modern cloud-native interface with significantly more automation capability. The platform is different. The operational discipline is identical.

---

## Section 1 — What ServiceNow Is and Why It Matters

### The Platform in Plain Language

ServiceNow is a cloud-based platform that manages IT service workflows. At its core, it is a system of record for everything that happens in an IT operations environment — every incident, every change, every problem, every service request. Every action taken, every approval given, every SLA timer that fires — it all lives in ServiceNow.

Before platforms like ServiceNow, operations teams managed these workflows through a combination of email threads, spreadsheets, and legacy ticketing systems that did not talk to each other. An incident might be tracked in one system, the change that caused it in another, and the post-incident review action items in a spreadsheet nobody could find six months later. ServiceNow puts all of it in one place with a common data model, automated workflows, and reporting that does not require manual assembly.

### Why Operations Leaders Need to Know It

A Service Delivery Manager who does not know ServiceNow is operating blind. The platform is where:

- Incidents are created, assigned, escalated, and closed
- SLA timers run — and breach when they are not met
- Changes are submitted, reviewed by CAB, approved, and tracked
- Problem records are linked to the incidents that drove them
- RCA findings are documented and action items are tracked
- Service request fulfillment is managed end to end
- Reports are generated that tell leadership whether the operation is working

Every metric the SDM presents in a service review, every SLA compliance number, every MTTR figure — it comes from ServiceNow. An SDM who cannot navigate the platform cannot verify the data they are presenting. That is a credibility problem.

### ServiceNow vs. BMC Remedy — The Transition

For operations professionals with a Remedy background, ServiceNow is not a foreign language — it is the same language with a new interface and significantly more capability.

| Concept | In Remedy | In ServiceNow |
|---|---|---|
| Ticket / Record | Request / Incident form | Record — incident, change, problem, request |
| Assignment | Assigned To / Support Group | Assignment Group + Assigned To |
| Priority | Impact + Urgency matrix | Impact + Urgency → auto-calculates Priority |
| SLA tracking | SLA targets on ticket | SLA module — timers, breach alerts, compliance reports |
| Escalation rules | Assignment engine rules | Business Rules + Escalation policies |
| Change record | Change Request form | Change Request — with workflow states |
| Approval workflow | Approval Server | Approval Engine — digital approvals with audit trail |
| Reporting | Reports module | Reports + Dashboards — real-time and scheduled |
| Knowledge base | Knowledge Management module | Knowledge Base — integrated with incident triage |
| CMDB | Asset Management | CMDB — Configuration Management Database |

The operational concepts are identical. The primary differences are:

**Automation.** ServiceNow automates far more than Remedy. SLA breach alerts, assignment routing, approval notifications, escalation triggers — these are configured once and run automatically. In Remedy, many of these required manual intervention or custom development.

**User experience.** ServiceNow's interface is browser-based and modern. Remedy's interface varied significantly by version and was often cumbersome. The learning curve for experienced Remedy users is primarily UI navigation, not conceptual understanding.

**Cloud-native.** ServiceNow is SaaS — no on-premise infrastructure to maintain. Updates are delivered automatically. This changes the upgrade and maintenance dynamic significantly.

**Integration capability.** ServiceNow integrates with monitoring platforms, CI/CD pipelines, communication tools, and virtually any enterprise system through its integration hub. Remedy integrations required significant custom development.

---

## Section 2 — The Core Modules

ServiceNow is organized into modules — each one managing a specific type of IT service workflow. The five core modules for operations are Incident Management, Change Management, Problem Management, Service Request Management, and the Configuration Management Database (CMDB). Every other module in the platform builds on top of these five.

### How the Modules Connect

The power of ServiceNow is not in any individual module — it is in how the modules connect to each other. A single production event can touch all five modules simultaneously:

```
Monitoring alert fires
    → Incident created (Incident Management)
    → Root cause identified — production change implemented yesterday
    → Incident linked to Change record (Change Management)
    → Problem record created — this has happened before
    → Problem linked to Incident (Problem Management)
    → Known Error added to KEDB
    → Fix requires a new change to the CI in the CMDB
    → Change record created (Change Management)
    → CMDB updated when fix is implemented (CMDB)
    → Service request raised for additional monitoring on the affected system
    → Request fulfilled (Service Request Management)
```

That is one event, five modules, complete audit trail. Every step is linked. Six months later, when someone asks what happened and how it was resolved, the answer is in ServiceNow.

---

## Section 3 — Incident Management Module

### What It Does

The Incident Management module is where production service disruptions are created, tracked, and resolved. It is the highest-traffic module in any operations environment — every alert, every user report, and every proactively detected issue starts here.

### The Incident Record

Every incident in ServiceNow is a record with a unique number (INC followed by digits). The record captures everything about the incident from detection to closure.

**Key fields on the incident record:**

| Field | Purpose | Notes |
|---|---|---|
| **Number** | Unique identifier — INC0001234 | Auto-generated. Used in all communications and audit references. |
| **Caller** | Who reported the incident | For monitoring-generated incidents — the monitoring integration |
| **Category / Subcategory** | What type of incident — network, application, hardware | Used for trend reporting and assignment routing |
| **Impact** | How many users or systems are affected — High / Medium / Low | Combined with Urgency to calculate Priority |
| **Urgency** | How quickly resolution is needed — High / Medium / Low | Combined with Impact to calculate Priority |
| **Priority** | Auto-calculated from Impact + Urgency — P1 through P4 | Drives SLA timer selection |
| **Assignment Group** | The team responsible for resolution | Drives on-call routing and SLA accountability |
| **Assigned To** | The individual working the incident | |
| **State** | New / In Progress / On Hold / Resolved / Closed | State transitions drive workflow and SLA timers |
| **Short Description** | One-line summary | Appears in list views and notifications |
| **Description** | Full incident detail | Everything known at time of creation |
| **Work Notes** | Internal log — not visible to end user | All investigation steps, findings, escalations documented here |
| **Additional Comments** | Customer-facing updates | Visible to the caller if using self-service portal |
| **Resolution Notes** | How the incident was resolved | Required before State can be set to Resolved |
| **Close Code** | Resolved by caller / Resolved by support / etc. | Required at closure for reporting accuracy |

### Major Incident Workbench

When a Sev 1 or Sev 2 incident is declared a Major Incident — by checking the Major Incident checkbox on the incident record — ServiceNow activates the Major Incident Workbench. This is a dedicated interface for managing high-severity incidents.

**What the Major Incident Workbench provides:**

- **Stakeholder notification log** — tracks every executive notification sent, by whom, at what time
- **Bridge call log** — records bridge call open and close times
- **Status update tracking** — confirms 30-minute update cadence is being maintained
- **Escalation timeline** — shows when each escalation level was triggered
- **Resolution timeline** — captures all key timestamps from detection to closure

The workbench is the audit trail for major incident management. It is also what the SDM references when preparing a post-incident report for the customer.

### SLA Module — How It Works With Incidents

Every incident has an SLA attached based on its Priority. The SLA module starts a timer the moment the incident is created and tracks it against the target.

**SLA states:**

| State | Meaning |
|---|---|
| **In Progress** | Timer running — SLA has not been met or breached |
| **Paused** | Timer paused — typically when incident is On Hold waiting for customer response |
| **Completed** | SLA met — incident resolved within the target window |
| **Breached** | SLA missed — incident was not resolved within the target window |

**Warning notifications:**
ServiceNow fires automated notifications at configurable thresholds — typically 50%, 75%, and 90% of the SLA window. At 75%, the on-call manager receives an alert. At 100%, the breach is recorded and the SDM is notified automatically.

**Pause conditions:**
SLA timers can be paused under specific conditions — most commonly when an incident is placed On Hold pending customer information. The conditions that pause the SLA are configured by the ServiceNow administrator. They must be defined carefully — a timer that pauses too easily inflates compliance rates without reflecting actual performance.

### Key Incident Reports

| Report | What It Shows | Where to Find It |
|---|---|---|
| Incident Volume by Priority | Count of incidents by P1/P2/P3/P4 over a time period | Reports → Incident Reports → Volume by Priority |
| MTTA by Priority | Average acknowledgment time by severity | Reports → SLA Reports → Mean Time to Acknowledge |
| MTTR by Priority | Average resolution time by severity | Reports → SLA Reports → Mean Time to Resolve |
| SLA Compliance Dashboard | Real-time compliance rate by priority | Service Level Management → SLA Dashboard |
| Breached SLAs | All incidents where SLA was missed | Reports → SLA Reports → Breached SLAs |
| Repeat Incidents | Incidents linked to known errors or closed problems | Reports → Incident Reports → Incidents by Known Error |
| Major Incident Log | All declared major incidents with resolution times | Reports → Incident Reports → Major Incidents |

---

## Section 4 — Change Management Module

### What It Does

The Change Management module manages every modification to production systems, applications, and infrastructure. It enforces the approval workflow, tracks the implementation, and maintains the audit trail that regulators and auditors examine.

### The Change Record

Every change in ServiceNow is a Change Request record with a unique number (CHG followed by digits).

**Key fields on the change record:**

| Field | Purpose | Notes |
|---|---|---|
| **Number** | Unique identifier — CHG0001234 | Auto-generated |
| **Type** | Standard / Normal / Emergency | Determines workflow path |
| **Risk** | Low / Medium / High / Critical | Drives approval requirements |
| **Impact** | Low / Medium / High | Combined with Risk for overall change assessment |
| **Requested By** | Who is requesting the change | Segregation of duties — cannot be same as Approved By |
| **Assignment Group** | Team implementing the change | |
| **Assigned To** | Individual implementing the change | Segregation of duties — cannot be same as Requested By or Approved By |
| **State** | New / Assess / Authorize / Scheduled / Implement / Review / Closed | State machine drives the workflow |
| **Planned Start / End** | Implementation window | Used to populate the Forward Schedule of Change |
| **Short Description** | One-line summary | |
| **Description** | Full change detail including justification | |
| **Implementation Plan** | Step-by-step procedure | Required field — incomplete submissions returned |
| **Backout Plan** | Rollback procedure | Required field — must define rollback decision point |
| **Test Plan** | Post-implementation validation | Required field |
| **Work Notes** | Implementation log — every step documented in real time | |
| **Close Code** | Successful / Unsuccessful / Rolled Back | Required at closure |

### Change Workflow States

ServiceNow enforces change management through a state machine — the record must pass through each state in sequence, and certain actions are only available in specific states.

| State | What Happens Here |
|---|---|
| **New** | Change record created — fields populated by requestor |
| **Assess** | Change Manager reviews completeness — returns if incomplete |
| **Authorize** | CAB review and approval — digital approvals recorded with timestamps |
| **Scheduled** | Approved — appears on Forward Schedule of Change |
| **Implement** | Implementation window is active — work notes updated in real time |
| **Review** | Post-implementation testing and review |
| **Closed** | Change record closed — close code and outcome documented |

### The Approval Engine

When a change record reaches the Authorize state, ServiceNow's Approval Engine routes it to the configured approvers based on change type and risk level. Each approver receives a notification and approves or rejects directly in ServiceNow — creating a digital approval record with the approver's name and timestamp.

**What the approval record captures:**
- Approver name and role
- Approval or rejection
- Timestamp
- Comments (required on rejection)

This is the audit evidence that the change was properly authorized before implementation. An approval that happened verbally but was not recorded in ServiceNow does not exist for audit purposes.

### Forward Schedule of Change (FSC)

The FSC is the calendar view of all approved upcoming changes. Every change in the Scheduled state appears on the FSC. The Change Manager and operations team use the FSC to:

- Identify conflicts between simultaneous changes
- Enforce blackout periods
- Communicate upcoming changes to stakeholders
- Sequence changes to minimize risk on any given day

The FSC is a living document — it is reviewed at every CAB meeting and updated as changes are approved, deferred, or withdrawn.

### Standard Change Catalog

Standard changes — pre-approved, low-risk, routine — are managed through the Standard Change Catalog. The catalog contains templates for each approved standard change type. An implementer selects the appropriate template, which auto-populates the implementation plan, risk level, and approval status.

The Standard Change Catalog is reviewed quarterly by the CAB. Any template that has resulted in an incident or rollback in the past 90 days is flagged for re-evaluation.

### Key Change Reports

| Report | What It Shows | Where to Find It |
|---|---|---|
| Change Success Rate | % of changes closed as Successful vs. Rolled Back | Reports → Change Reports → Implementation Outcome |
| Emergency Change Rate | % of changes classified as Emergency | Reports → Change Reports → Change Type Distribution |
| Change-Induced Incidents | Incidents where a recent change was identified as a contributing factor | Reports → Change Reports → Changes with Related Incidents |
| Unauthorized Changes | Production changes without a corresponding approved change record | Reports → Change Reports → Changes Without Approval |
| CAB Approval Rate | % of submitted changes approved at first review | Reports → Change Reports → Approval Rate |
| Forward Schedule of Change | Upcoming approved changes by date | Change → Forward Schedule of Change |

---

## Section 5 — Problem Management Module

### What It Does

The Problem Management module manages the root cause analysis process and the Known Error Database (KEDB). It is the bridge between reactive incident response and proactive service improvement.

### The Problem Record

Every problem in ServiceNow is a Problem record with a unique number (PRB followed by digits). Problem records are created from incidents — typically Sev 1 and Sev 2 — and link back to the originating incident records.

**Key fields on the problem record:**

| Field | Purpose | Notes |
|---|---|---|
| **Number** | Unique identifier — PRB0001234 | Auto-generated |
| **Problem Statement** | Specific, measurable description of what failed | Not the incident title — the underlying problem |
| **Related Incidents** | Links to all incidents caused by this problem | Populated when problem is created from incident |
| **Assigned To** | Problem Manager — accountable for driving to closure | |
| **Root Cause** | Documented finding from RCA | Populated after RCA session |
| **Workaround** | Interim solution if permanent fix not yet available | Linked to KEDB entry |
| **State** | Open / Known Error / Resolved / Closed | |
| **Problem Tasks** | Action items from PIR — owner, due date, priority | Child records linked to problem |

### Known Error Database (KEDB)

When a problem's root cause is identified but the permanent fix has not yet been implemented, the problem becomes a Known Error. A Known Error record is created in the KEDB — documenting the failure mode, the workaround, and the planned fix.

**Why the KEDB matters:**
When a front-line analyst encounters an incident that matches a known error, they can apply the documented workaround immediately — without escalating or re-investigating. This reduces MTTR for repeat incidents from hours to minutes.

**What a KEDB entry contains:**
- Description of the failure mode — what the symptoms look like
- Known trigger conditions — what causes it to occur
- Workaround — specific steps to restore service temporarily
- Permanent fix — what will resolve it permanently and when
- Linked problem record — for full audit trail

**KEDB search from the incident record:**
When an analyst creates or updates an incident, ServiceNow displays related KEDB entries based on category and description match. This is the mechanism that makes the KEDB useful in real time — the analyst does not have to remember to search for it.

### Problem Tasks

Every action item from a Post-Incident Review is documented as a Problem Task linked to the Problem record. Problem Tasks have:
- Specific description of what will be done
- Named assignee — one individual, not a team
- Due date — specific calendar date
- Priority — P1 / P2 / P3

Problem Tasks are tracked in ServiceNow and appear in the Problem Manager's task list. They do not disappear after the PIR meeting — they exist in the system until they are completed and closed.

### Key Problem Reports

| Report | What It Shows | Where to Find It |
|---|---|---|
| Open Problem Records | All problems not yet resolved | Reports → Problem Reports → Open Problems |
| PIR Completion Rate | % of Sev 1/2 incidents with completed problem records | Reports → Problem Reports → Problems by Linked Incident |
| Problem Task Status | Open, in-progress, and overdue problem tasks | Reports → Problem Reports → Open Problem Tasks |
| KEDB Utilization | How often KEDB entries are referenced during incident triage | Reports → Knowledge Reports → KEDB Article Views |
| Repeat Incident Rate | Incidents linked to known errors | Reports → Incident Reports → Incidents by Known Error |

---

## Section 6 — Service Request Management Module

### What It Does

The Service Request Management module handles standard, pre-defined requests that do not require incident investigation or a change record. It separates routine fulfillment work from the incident queue — keeping the incident queue focused on actual service disruptions.

### The Service Catalog

The Service Catalog is the front-end interface where users submit requests. It is organized as a catalog of services — each service is a catalog item with a defined fulfillment workflow, SLA, and approval requirement.

**Catalog item structure:**
- **Name and description** — what the user is requesting
- **Request form** — the fields the user completes to submit the request
- **Fulfillment workflow** — the steps taken to fulfill the request, automated where possible
- **Approval requirement** — does this request require manager or IT approval before fulfillment?
- **SLA target** — how long fulfillment should take
- **Fulfillment group** — which team fulfills this request type

**Examples of catalog items:**
- New user account setup
- Software installation request
- Hardware provisioning
- Access request — application or system
- Password reset (if not self-service)
- VPN access request
- Distribution list creation

### The Request Record and RITM

When a user submits a catalog item, ServiceNow creates two records:

**REQ record (Request)** — the parent record representing the user's overall request. A single REQ can contain multiple items.

**RITM record (Requested Item)** — one RITM per catalog item requested. The RITM is where fulfillment is tracked — it has its own state, assignment group, and SLA timer.

Operations teams work RITMs — not REQs. The REQ is the container. The RITM is the unit of work.

### Self-Service Portal

ServiceNow's self-service portal (Service Portal) is the user-facing interface for submitting requests, reporting incidents, checking ticket status, and searching the knowledge base. A well-configured Service Portal reduces phone and email volume to the service desk by enabling users to handle routine requests themselves.

**What users can do in the Service Portal:**
- Submit service requests from the catalog
- Report incidents
- Check the status of their open tickets
- Search the knowledge base for how-to information
- Search the KEDB for known issues affecting their service

---

## Section 7 — Configuration Management Database (CMDB)

### What It Does

The CMDB is the inventory of every component in the IT environment — servers, applications, network devices, endpoints, cloud resources, and the relationships between them. It is the foundation that every other module builds on.

### Configuration Items (CIs)

Every component tracked in the CMDB is a Configuration Item (CI). A CI record captures:

- **Name and type** — what the component is
- **Owner** — who is responsible for it
- **Location** — physical or logical location
- **Status** — operational, in maintenance, retired
- **Relationships** — what this CI depends on and what depends on it
- **Linked records** — incidents, changes, and problems associated with this CI

### Why the CMDB Matters for Operations

**Incident impact assessment:**
When an incident affects a server, the CMDB shows what applications run on that server, what services those applications support, and what customers use those services. That context turns a generic server alert into a specific business impact statement — in seconds.

**Change risk assessment:**
When a change is proposed to a CI, the CMDB shows the dependencies. A change to a database server that three customer-facing applications depend on carries a different risk profile than a change to an isolated development server. Without the CMDB, that risk assessment is based on whoever happens to know the dependencies.

**Root cause analysis:**
When a problem record is created, the CMDB provides the relationship map — helping the RCA team trace the failure through the infrastructure to its source.

### CMDB Health

A CMDB that is incomplete or inaccurate is worse than no CMDB — it gives false confidence. The most common CMDB health issues:

- **Stale records** — CIs that no longer exist still showing as active
- **Missing relationships** — dependencies between CIs not documented
- **Inaccurate ownership** — CIs assigned to teams or individuals who no longer manage them
- **Discovery gaps** — new CIs added to the environment without corresponding CMDB records

CMDB health is maintained through a combination of automated discovery tools (which scan the environment and populate CI records automatically) and manual review processes. The SDM is not responsible for CMDB administration — but the SDM depends on CMDB accuracy for incident impact assessment and change risk evaluation. When the CMDB is wrong, the SDM's decisions are based on bad data.

---

## Section 8 — Reporting and Dashboards

### What Good Reporting Looks Like

ServiceNow's reporting capability is one of its strongest differentiators over legacy ITSM platforms. Reports can be run on demand, scheduled for automatic delivery, or displayed as live dashboards that update in real time.

The SDM who knows how to build and use ServiceNow reports does not depend on anyone else to tell them how the operation is performing. The data is there — the question is whether you know how to get it.

### Report Types

| Report Type | Best Used For | Example |
|---|---|---|
| **Bar Chart** | Comparing counts across categories | Incident volume by priority — this month vs. last month |
| **Pie Chart** | Showing distribution | Change success rate — successful vs. rolled back vs. unsuccessful |
| **Line Chart** | Showing trends over time | MTTR trend — 6-month rolling average |
| **List Report** | Showing individual records | All Sev 1 incidents this month with resolution time |
| **Single Score** | Displaying one key metric | Current SLA compliance rate |
| **Pivot Table** | Multidimensional analysis | Incident volume by category and priority |

### Dashboards

A ServiceNow dashboard is a collection of reports displayed together on a single page. Dashboards can be built for specific audiences — an SDM dashboard, a CAB dashboard, an executive dashboard — each showing the metrics most relevant to that audience.

**SDM Operations Dashboard — recommended widgets:**
- Current SLA compliance rate (single score)
- Open Sev 1 and Sev 2 incidents (list)
- MTTR trend — 90 days (line chart)
- Incident volume by priority — this month vs. last month (bar chart)
- Open problem tasks past due date (list)
- Change success rate — 90 days (single score)
- Emergency change rate — current month (single score)

**CAB Dashboard — recommended widgets:**
- Changes scheduled this week (list)
- Emergency change rate — current month (single score)
- Change success rate — 90 days (line chart)
- Changes pending approval (list)
- Unauthorized changes — current month (single score)

### Scheduled Reports

Reports can be scheduled to run automatically and deliver to a distribution list. Common scheduled reports:

| Report | Frequency | Audience |
|---|---|---|
| Incident SLA compliance summary | Weekly | SDM, Operations team |
| Major incident log | Monthly | SDM, Executive leadership |
| Change success report | Monthly | Change Manager, SDM |
| Problem task aging report | Weekly | Problem Manager, SDM |
| KEDB utilization report | Monthly | Problem Manager |
| Executive operations summary | Monthly | CIO, VP of IT |

---

## Section 9 — ServiceNow for the Operations Leader — Day to Day

### Starting Your Day in ServiceNow

An operations leader who starts the day without checking ServiceNow is starting blind. Here is the recommended daily check sequence:

1. **SLA Dashboard** — are any SLA timers in the red or approaching breach?
2. **Open Sev 1 / Sev 2 list** — any major incidents open from overnight?
3. **My team's queue** — workload distribution, aging tickets, anything stuck?
4. **Problem task list** — any PIR action items past due date?
5. **Change calendar** — what changes are scheduled today? Any conflicts?
6. **Escalation flags** — any incidents flagged for customer escalation?

That check takes ten minutes. It gives the operations leader a complete picture of the current state before the first call of the day.

### The Metrics That Tell You the Operation Is Healthy

| Metric | Green | Yellow | Red |
|---|---|---|---|
| SLA Compliance Rate | ≥95% | 90–94% | <90% |
| Emergency Change Rate | <10% | 10–15% | >15% |
| Repeat Incident Rate | <10% | 10–15% | >15% |
| PIR Completion Rate | 100% | 90–99% | <90% |
| Problem Task Closure Rate | ≥90% by due date | 80–89% | <80% |
| Unauthorized Change Rate | 0% | Any | — |
| Change Success Rate | ≥95% | 90–94% | <90% |

### What to Do When a Metric Is Red

A red metric is not an emergency — it is a signal. The response is always the same sequence:

1. **Confirm the data is accurate** — is ServiceNow configured correctly to measure what you think it is measuring?
2. **Identify the pattern** — is this a one-time event or a trend?
3. **Identify the cause** — process gap, staffing gap, tooling gap, or training gap?
4. **Define the corrective action** — specific, with a named owner and a due date
5. **Track the corrective action in ServiceNow** — not in an email, not in a spreadsheet

A red metric that gets the same response every month without improvement is a sign that the corrective actions are not working — or not being executed.

---

## Section 10 — Common ServiceNow Mistakes Operations Leaders Make

| Mistake | What It Looks Like | What It Costs |
|---|---|---|
| **Not using work notes in real time** | Investigation steps documented after the incident closes — from memory | Inaccurate timeline. Audit trail is incomplete. RCA has no reliable sequence of events. |
| **Closing incidents without resolution notes** | State set to Resolved with no documentation of how it was resolved | KEDB cannot be populated. Repeat incident is investigated from scratch. |
| **SLA timer pause conditions too broad** | Every incident placed On Hold to pause the SLA timer | SLA compliance rate looks good. Actual customer experience is not. |
| **CMDB not maintained** | Change risk assessment based on incomplete dependency data | High-risk changes appear low-risk. Change-induced incidents increase. |
| **Approvals outside ServiceNow** | CAB decisions made verbally and not recorded in the change record | No audit trail. Regulatory finding in a compliance review. |
| **Problem records not linked to incidents** | PIR findings documented but not connected to the incident record | No traceability. Cannot measure repeat incident rate accurately. |
| **Dashboard metrics not reviewed regularly** | Reports configured and never opened | Trends are invisible. Problems grow before they are visible. |
| **Work notes used for customer communication** | Internal notes visible to the customer via portal | Sensitive internal information disclosed unintentionally |
| **Bulk closures without validation** | Aged tickets closed in bulk to clean up the queue | Metrics look better. Real open issues are closed without resolution. Customer discovers the issue is still open. |
| **ServiceNow as a filing system, not a workflow tool** | Records created but workflow states not advanced | Reporting is inaccurate. SLA timers may not fire correctly. Approval workflows stall. |

---

## Appendix A — ServiceNow Quick Reference Card

### Incident Management
| Action | Navigation |
|---|---|
| Create incident | Incident → Create New |
| Set Major Incident flag | Incident form → Major Incident checkbox |
| Add work note | Incident form → Work Notes tab |
| View SLA timer | Incident form → SLA tab |
| Link to problem record | Incident form → Related Records → Create Problem |
| Search KEDB | Incident form → Related Records → Known Errors |
| View Major Incident Workbench | Incident form → Major Incident Workbench button |

### Change Management
| Action | Navigation |
|---|---|
| Create change request | Change → Create New |
| Select standard change | Change → Standard Change Catalog |
| Submit for approval | Change record → Submit for Approval button |
| View Forward Schedule of Change | Change → Forward Schedule of Change |
| Check Change Calendar / blackout periods | Change → Change Calendar |
| Record implementation steps | Change record → Work Notes tab |
| Link change to incident | Change record → Related Records → Add Relationship |

### Problem Management
| Action | Navigation |
|---|---|
| Create problem record | Problem → Create New OR from incident: Related Records → Create Problem |
| Document root cause | Problem record → Root Cause field |
| Create Known Error | Problem record → Create Known Error button |
| Add KEDB workaround | Known Error record → Workaround field |
| Create problem task | Problem record → Related Records → Create Task |
| View open problem tasks | Problem → Problem Tasks → Open |

### Service Request Management
| Action | Navigation |
|---|---|
| Submit request (user-facing) | Service Portal → Service Catalog |
| View open RITMs | Service Catalog → Requested Items → Open |
| Update fulfillment status | RITM record → State field + Work Notes |

### Reporting
| Action | Navigation |
|---|---|
| Create new report | Reports → Create New |
| View existing reports | Reports → View / Run |
| Build dashboard | Dashboards → Create New |
| Schedule report delivery | Report record → Schedule tab |
| SLA compliance dashboard | Service Level Management → SLA Dashboard |

---

## Appendix B — Glossary

| Term | Definition |
|---|---|
| **CI** | Configuration Item — any component tracked in the CMDB |
| **CMDB** | Configuration Management Database — inventory of all IT components and their relationships |
| **FSC** | Forward Schedule of Change — calendar of approved upcoming changes |
| **INC** | Incident record number prefix — INC0001234 |
| **CHG** | Change record number prefix — CHG0001234 |
| **PRB** | Problem record number prefix — PRB0001234 |
| **REQ** | Request record — parent record for service catalog submissions |
| **RITM** | Requested Item — child record representing one catalog item in a request |
| **KEDB** | Known Error Database — catalog of known failure modes and workarounds |
| **SLA** | Service Level Agreement — time-based commitment tracked by the SLA module |
| **OLA** | Operational Level Agreement — internal team commitment supporting an SLA |
| **Business Rule** | Automated logic that fires when a record condition is met — e.g. send notification when SLA reaches 75% |
| **Workflow** | Automated sequence of activities triggered by a state change — e.g. route change for approval when submitted |
| **Assignment Group** | A team in ServiceNow — incidents and changes are assigned to groups, then to individuals |
| **Close Code** | Required field at record closure — categorizes the resolution outcome |
| **Major Incident Workbench** | Dedicated interface for managing Sev 1/2 incidents — stakeholder notifications, bridge call log, status update tracking |
| **Standard Change Catalog** | Library of pre-approved standard change templates |
| **Approval Engine** | ServiceNow module that routes records for digital approval and records the approver, decision, and timestamp |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | July 2026 | Initial release | Scott Boehler |

---

*ServiceNow is a tool. The operations leader who knows the tool is not dependent on someone else to tell them how the operation is performing. The data is there — pull it, read it, and act on it.*
