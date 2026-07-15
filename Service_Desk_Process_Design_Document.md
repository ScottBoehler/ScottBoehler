# Service Desk Process Design Document
### Greenfield Service Management Build | 30–60 Day Process Design Phase

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Phase:** Day 30–60 — Process Design  
**Applies To:** Any organization building a service management function from scratch — no inherited processes, no legacy constraints, no technical debt

---

## Purpose & Context

This document defines the process design for a greenfield service desk build. It serves two audiences simultaneously — the operations team that will execute these processes every day, and the leadership team that needs confidence the function is being built on a foundation that scales.

A greenfield build is an opportunity that most service delivery leaders never get. There is no inherited process to work around, no bad habits embedded in the team, no technical debt in the tooling. The downside of starting from zero is that nothing exists. The upside is that everything can be designed right.

That is the governing principle of this document. Every process defined here is designed for where the organization is going — not just where it is today. The team may be small now. The ticket volume may be manageable now. The customer base may be limited now. The processes documented here are built to scale with the business without requiring a complete redesign when growth happens.

This document is a living artifact. It is reviewed after every major incident, updated when process gaps are identified, and formally reviewed on a quarterly basis. A process design document that does not change is not being used — it is being filed.

---

## Section 1 — Process Design Principles

Before any individual process is designed, the principles that govern all process design are established. These principles are not aspirational — they are non-negotiable constraints that every process in this document is built to satisfy.

### Principle 1 — ITIL v4 as the Framework

All processes in this document are built on ITIL v4 principles. ITIL v4 is not a rigid prescription — it is a framework. It defines what good service management looks like without mandating exactly how it is implemented. Every organization adapts ITIL to its context. This document reflects that adaptation for this specific organization.

ITIL v4 practices most directly reflected in this document:
- Incident Management
- Change Enablement
- Problem Management
- Service Request Management
- Service Level Management
- Continual Improvement

### Principle 2 — ServiceNow as the System of Record

Every process in this document is designed with ServiceNow as the system of record. This means:

- Every process step that creates, updates, or closes a record happens in ServiceNow — not in email, not in a spreadsheet, not in a chat tool
- Every SLA timer is measured by ServiceNow — not manually calculated
- Every escalation trigger is automated where possible — not dependent on someone remembering to escalate
- Every report referenced in this document is generated from ServiceNow — not assembled from multiple sources

If a process step cannot be supported by ServiceNow, the process step is flagged for tool configuration before the process goes live. A process that depends on manual steps that ServiceNow should be handling is a process with a gap built into it.

### Principle 3 — Designed to Scale

Every process is designed for the organization at three stages:
- **Current state** — the team and volume that exists today
- **12-month state** — the team and volume projected at 12 months
- **36-month state** — the team and volume projected at 36 months

Where a process requires a different approach at each stage, the transition points are documented. A process that works for a three-person team but breaks at fifteen is not a scalable process — it is a temporary fix.

### Principle 4 — Clarity Over Completeness

A process that is too complex to follow under pressure is not a process — it is documentation. Every process in this document is designed to be executable by a team member who has been awake for four hours dealing with a Sev 1 incident. If it cannot be followed under those conditions, it is too complex.

### Principle 5 — Accountability at Every Step

Every process step has an owner. Every SLA has a measurement. Every escalation has a trigger. Ambiguity in a process is not a minor inconvenience — it is the root cause of most service management failures. Where there is ambiguity about who does what, the process has not been designed — it has been described.

### Principle 6 — Continuous Improvement Is Built In

Every process includes KPIs that measure whether the process is working. Those KPIs are reviewed monthly. When a KPI is trending wrong, the process is reviewed — not the person executing it. The assumption in this document is that people executing a well-designed process will produce good outcomes. A bad outcome is a signal to examine the process.

---

## Section 2 — Process Scope

### The Five Core Processes

The following five processes are designed in the Day 30–60 phase. They represent the minimum viable process set for a functioning service desk. Every other service management process builds on top of these five — they cannot be added before these are stable.

| Process | What It Covers | Why It Is First |
|---|---|---|
| **Incident Management** | Detection, response, escalation, resolution, and closure of service disruptions | Foundation of everything. Without incident management, everything else is reactive chaos. |
| **Change Management** | Classification, approval, implementation, and review of changes to the production environment | Protects production stability. Changes without process cause incidents. |
| **Problem Management** | Root cause analysis, known error management, and prevention of incident recurrence | Turns reactive incident response into proactive improvement. |
| **Service Request Management** | Fulfillment of standard requests that do not require a change or incident | Separates routine requests from incidents. Keeps the incident queue clean. |
| **Escalation Management** | Internal escalation tiers, customer escalation handling, and executive notification | Defines what happens when the standard process is not enough. |

### Process Dependencies

These five processes are not independent. They are connected at specific handoff points. Those handoffs are designed explicitly — not assumed. Section 10 covers the interdependencies in detail.

### What Is Out of Scope for This Phase

The following processes are important but are designed in a later phase once the five core processes are stable:

- Asset and Configuration Management (CMDB build)
- Knowledge Management (knowledge base structure and governance)
- Service Level Management (formal SLA design with customers)
- Capacity Management
- Availability Management

---

## Section 3 — Process Design Template

Every process in this document is documented using the same template. This consistency is deliberate — it makes the processes easier to read, easier to train against, and easier to update. When a new process is added in a future phase, it uses the same template.

---

### [PROCESS NAME] — Process Design

**Process Owner:** [Name and title of the person accountable for this process]  
**Process Version:** [Version number]  
**Last Reviewed:** [Date]  
**Next Review Due:** [Date — quarterly minimum]

---

#### 3.1 Purpose

*One to three sentences. What does this process exist to do? What outcome does it produce?*

---

#### 3.2 Scope

**In scope:**
*What does this process cover? Be specific.*

**Out of scope:**
*What does this process explicitly not cover? Be specific. Do not leave gray areas.*

---

#### 3.3 Definitions

*Define any terms used in this process that could be interpreted differently by different team members. If a term is defined in another process document, reference that document rather than redefining it.*

| Term | Definition |
|---|---|
| [Term] | [Definition] |
| [Term] | [Definition] |

---

#### 3.4 Inputs

*What triggers this process? What information must exist before the process can begin?*

| Input | Source | Required / Optional |
|---|---|---|
| [Input] | [Where it comes from] | [Required / Optional] |
| [Input] | [Where it comes from] | [Required / Optional] |

---

#### 3.5 Outputs

*What does this process produce? What records, notifications, or actions result from completing this process?*

| Output | Destination | Timing |
|---|---|---|
| [Output] | [Who receives it or where it goes] | [When it is produced] |
| [Output] | [Who receives it or where it goes] | [When it is produced] |

---

#### 3.6 Roles and Responsibilities

*Every role that participates in this process. Named roles — not individuals. When a person fills a role, their name is recorded in the team RACI, not here.*

| Role | Responsibilities in This Process |
|---|---|
| [Role] | [What this role does in this process] |
| [Role] | [What this role does in this process] |

**RACI Matrix:**

| Activity | [Role 1] | [Role 2] | [Role 3] | [Role 4] |
|---|---|---|---|---|
| [Activity] | R | A | C | I |
| [Activity] | | | | |

*R = Responsible (does the work) | A = Accountable (owns the outcome) | C = Consulted (provides input) | I = Informed (receives notification)*

---

#### 3.7 Process Workflow

*Step-by-step process flow. Every step has a number, a description, an owner, and a ServiceNow action where applicable. No step is ambiguous about who does what.*

| Step | Description | Owner | ServiceNow Action | Time Target |
|---|---|---|---|---|
| 1 | [Description of step] | [Role] | [What happens in ServiceNow] | [Time] |
| 2 | [Description of step] | [Role] | [What happens in ServiceNow] | [Time] |
| 3 | [Description of step] | [Role] | [What happens in ServiceNow] | [Time] |

**Decision Points:**

*Where the process branches based on a condition — document each branch.*

| Decision Point | Condition | If Yes | If No |
|---|---|---|---|
| [Step number] | [What is being evaluated] | [What happens] | [What happens] |

---

#### 3.8 Escalation Triggers

*The specific conditions that cause this process to escalate — to a higher tier, a different team, or a different process. Every trigger is specific and measurable — not "when it seems necessary."*

| Trigger | Condition | Escalation Action | Owner |
|---|---|---|---|
| [Trigger name] | [Specific, measurable condition] | [What happens] | [Who acts] |
| [Trigger name] | [Specific, measurable condition] | [What happens] | [Who acts] |

---

#### 3.9 SLA Targets

*The time-based commitments that apply to this process. Every SLA has a target, a measurement method, and a consequence for breach.*

| SLA | Target | Measured From | Measured To | Breach Action |
|---|---|---|---|---|
| [SLA name] | [Target] | [Start event] | [End event] | [What triggers on breach] |
| [SLA name] | [Target] | [Start event] | [End event] | [What triggers on breach] |

---

#### 3.10 KPIs and Performance Metrics

*The metrics that tell you whether this process is working. Reviewed monthly. Every metric that is trending wrong triggers a process review.*

| KPI | Definition | Target | Data Source | Review Frequency |
|---|---|---|---|---|
| [KPI name] | [What it measures] | [Target value] | [ServiceNow report] | Monthly |
| [KPI name] | [What it measures] | [Target value] | [ServiceNow report] | Monthly |

---

#### 3.11 ServiceNow Configuration Requirements

*What needs to be configured in ServiceNow before this process can go live. This is the requirements list — the ServiceNow admin translates these into technical configuration.*

| Requirement | Description | Priority | Status |
|---|---|---|---|
| [Requirement] | [What needs to be configured] | [High / Medium / Low] | [ ] Not started / [ ] In progress / [ ] Complete |
| [Requirement] | [What needs to be configured] | [High / Medium / Low] | [ ] Not started / [ ] In progress / [ ] Complete |

---

#### 3.12 Exception Handling

*What happens when the standard process cannot be followed. Every exception path is documented — the team never improvises.*

| Exception | Condition | Handling Procedure |
|---|---|---|
| [Exception name] | [When this exception applies] | [What to do instead] |
| [Exception name] | [When this exception applies] | [What to do instead] |

---

#### 3.13 Related Documents

*Other process documents, runbooks, or reference materials that connect to this process.*

- [Document name] — [How it relates]
- [Document name] — [How it relates]

---

#### 3.14 Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | [Date] | Initial release | [Author] |

---

## Section 4 — Incident Management Process Design

### Incident Management — Process Design

**Process Owner:** Service Delivery Manager  
**Process Version:** 1.0  
**Last Reviewed:** May 2026  
**Next Review Due:** August 2026

---

#### Purpose

To restore normal service operation as quickly as possible following an unplanned interruption or degradation in service quality, minimizing the impact on the business and ensuring SLA commitments are met.

---

#### Scope

**In scope:**
- All unplanned service interruptions affecting production systems, customer-facing services, or internal infrastructure
- All alerts from monitoring systems that indicate service degradation
- All customer-reported service issues regardless of channel (phone, email, portal, chat)
- All Severity 1 through Severity 4 incidents

**Out of scope:**
- Planned maintenance activities (handled under Change Management)
- Standard service requests (handled under Service Request Management)
- Security incidents requiring a security-specific response (handled under Security Incident Response Plan)

---

#### Definitions

| Term | Definition |
|---|---|
| Incident | Any unplanned interruption to a service or reduction in service quality |
| Major Incident | A Sev 1 or Sev 2 incident requiring bridge call activation and executive notification |
| Incident Commander (IC) | The role accountable for managing a major incident from detection to closure |
| MTTR | Mean Time to Resolve — average time from incident detection to confirmed resolution |
| MTTA | Mean Time to Acknowledge — average time from incident detection to acknowledgment in ServiceNow |
| Bridge Call | A dedicated conference call opened for major incident coordination |
| Work Notes | Internal notes in the ServiceNow incident record visible only to the support team |

---

#### Inputs

| Input | Source | Required / Optional |
|---|---|---|
| Monitoring alert | Monitoring platform integration with ServiceNow | Required |
| Customer-reported issue | Phone, email, self-service portal, or chat | Required |
| Internal team detection | Team member identifies issue proactively | Required |
| Escalation from Tier 1 | Tier 1 support creates and escalates incident record | Required |

---

#### Outputs

| Output | Destination | Timing |
|---|---|---|
| Incident record (created) | ServiceNow — Incident module | At detection |
| Initial executive notification | Executive distribution list | Sev 1: 15 min / Sev 2: 30 min |
| Status updates | Customer and executive stakeholders | Every 30 min during active major incident |
| Resolution notification | Customer and executive stakeholders | At resolution |
| Closed incident record | ServiceNow — Incident module | Within 24 hrs of resolution |
| Problem record (Sev 1 and Sev 2) | ServiceNow — Problem module | Within 24 hrs of incident closure |

---

#### Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Service Desk Analyst (Tier 1)** | First point of contact. Creates incident record. Performs initial triage. Resolves Sev 3 and Sev 4 where possible. Escalates Sev 1 and Sev 2 immediately. |
| **Senior Engineer (Tier 2)** | Handles escalated incidents. Provides technical investigation and resolution. Joins bridge call for major incidents. |
| **Incident Commander** | Manages Sev 1 and Sev 2 incidents. Opens and chairs bridge call. Drives resolution timeline. Approves all-clear. Owns PIR scheduling. |
| **Communications Lead** | Sends executive notifications and status updates during major incidents. Logs all communications in ServiceNow. |
| **Service Delivery Manager** | Accountable for overall incident management process. Reviews all Sev 1 post-incident. Escalation point for unresolved major incidents. |

**RACI Matrix:**

| Activity | Tier 1 Analyst | Tier 2 Engineer | Incident Commander | SDM |
|---|---|---|---|---|
| Create incident record | R | | | A |
| Initial triage and classification | R | C | | A |
| Escalate Sev 1/Sev 2 | R | | A | I |
| Open bridge call | | | R/A | I |
| Technical investigation | C | R | | A |
| Executive notification | | | C | R/A |
| Status updates | | | C | R/A |
| Declare resolution | | C | R | A |
| Close incident record | R | | | A |
| Create problem record | | | | R/A |

---

#### Process Workflow

| Step | Description | Owner | ServiceNow Action | Time Target |
|---|---|---|---|---|
| 1 | Incident detected via monitoring alert, customer report, or internal observation | Tier 1 / Monitoring | Alert auto-creates incident record OR analyst creates manually | Immediate |
| 2 | Incident record created in ServiceNow with all available information | Tier 1 | Create Incident — populate all required fields | Within 5 min of detection |
| 3 | Initial triage — confirm impact and urgency. Set Priority (1–4) based on Impact/Urgency matrix | Tier 1 | Set Impact, Urgency, Priority fields | Within 5 min of record creation |
| 4 | Sev 3/4: Tier 1 investigates and resolves. Sev 1/2: Escalate immediately to Tier 2 and IC | Tier 1 | Assign to appropriate group. For Sev 1/2 — set Major Incident flag | Per severity SLA |
| 5 | For Sev 1/2: IC opens bridge call. Assigns Technical Lead and Communications Lead | IC | Update incident record — add IC, Technical Lead, Communications Lead | Within 10 min of Sev 1 detection |
| 6 | Technical investigation begins. All findings documented in work notes in real time | Tier 2 / SMEs | Work Notes tab — every action logged as it happens | Continuous |
| 7 | Communications Lead sends initial executive notification | Comms Lead | Log notification in Major Incident Workbench — Stakeholder Notifications tab | Sev 1: 15 min / Sev 2: 30 min |
| 8 | 30-minute status updates sent to stakeholders throughout active incident | Comms Lead | Log each update in ServiceNow | Every 30 min |
| 9 | Resolution achieved. Technical Lead confirms all systems stable | Tier 2 | Update work notes — resolution steps documented | At resolution |
| 10 | IC declares all-clear. Communications Lead sends resolution notification | IC / Comms Lead | Set incident State to Resolved. Log resolution notification. | At resolution |
| 11 | Incident record closed with full resolution documentation | Tier 1 | Set State to Closed. Complete all required fields. | Within 24 hrs of resolution |
| 12 | Problem record created for all Sev 1 and Sev 2 incidents | SDM | Create Problem — link to incident record | Within 24 hrs of closure |

**Decision Points:**

| Decision Point | Condition | If Yes | If No |
|---|---|---|---|
| Step 3 | Is Priority P1 or P2? | Escalate immediately to Tier 2 and IC — go to Step 5 | Continue Tier 1 investigation — go to Step 6 |
| Step 6 | Has Tier 2 identified a resolution path within 60 min of Sev 1 detection? | Continue current path | Escalate to SDM — consider vendor involvement or Level 3 escalation |
| Step 9 | Are all systems confirmed stable? | Proceed to IC all-clear | Continue investigation — do not declare resolution |

---

#### Escalation Triggers

| Trigger | Condition | Escalation Action | Owner |
|---|---|---|---|
| Sev 1 detection | Any incident classified Sev 1 | Immediate page to IC and Tier 2. Bridge call opened within 10 minutes. | Tier 1 Analyst |
| SLA at 75% | ServiceNow SLA timer reaches 75% of target window | Automatic alert fires to SDM. SDM assesses whether additional resources needed. | ServiceNow automation |
| No resolution path at 60 min | Sev 1 with no confirmed resolution path after 60 minutes | SDM escalates to Level 3 (Director/VP). Vendor engagement initiated if third party involved. | SDM |
| Scope expansion | Second system or service impacted during active incident | IC re-evaluates severity. Consider severity upgrade. Notify additional SMEs. | IC |
| SLA breach | ServiceNow SLA timer expires | Automatic alert fires to SDM. Customer notification sent. Post-breach RCA required. | ServiceNow automation / SDM |

---

#### SLA Targets

| SLA | Target | Measured From | Measured To | Breach Action |
|---|---|---|---|---|
| Sev 1 Acknowledge | 5 minutes | Incident created in ServiceNow | Work notes updated with acknowledgment | Automatic alert to SDM |
| Sev 2 Acknowledge | 10 minutes | Incident created in ServiceNow | Work notes updated with acknowledgment | Automatic alert to SDM |
| Sev 1 Resolution | 4 hours | Incident created in ServiceNow | Incident set to Resolved state | SDM notified. Customer credit assessment initiated. |
| Sev 2 Resolution | 8 hours | Incident created in ServiceNow | Incident set to Resolved state | SDM notified. Customer credit assessment initiated. |
| Sev 3 Resolution | 24 hours | Incident created in ServiceNow | Incident set to Resolved state | SDM notified |
| Sev 4 Resolution | 72 hours | Incident created in ServiceNow | Incident set to Resolved state | Queue review |
| Executive Notification (Sev 1) | 15 minutes | Incident created in ServiceNow | Notification logged in ServiceNow | IC notified of miss |
| Incident Closure | 24 hours | Incident set to Resolved | Incident set to Closed | Queue review |

---

#### KPIs and Performance Metrics

| KPI | Definition | Target | Data Source | Review Frequency |
|---|---|---|---|---|
| MTTA — Sev 1 | Average time from detection to acknowledgment | ≤5 minutes | ServiceNow SLA Reports | Monthly |
| MTTR — Sev 1 | Average time from detection to resolution | ≤4 hours | ServiceNow SLA Reports | Monthly |
| SLA Compliance Rate | % of incidents resolved within target MTTR | ≥95% | ServiceNow SLA Dashboard | Monthly |
| Repeat Incident Rate | % of incidents caused by a previously identified root cause | <10% | ServiceNow — incidents linked to known errors | Monthly |
| First Contact Resolution | % of Sev 3/4 resolved by Tier 1 without escalation | ≥70% | ServiceNow Incident Reports | Monthly |
| Escalation Rate | % of incidents requiring Level 3+ escalation | Trending down | ServiceNow Incident Reports | Monthly |
| PIR Completion Rate | % of Sev 1/2 with completed problem records | 100% | ServiceNow Problem Reports | Monthly |

---

#### ServiceNow Configuration Requirements

| Requirement | Description | Priority | Status |
|---|---|---|---|
| Incident form configuration | Required fields, Impact/Urgency matrix, Priority auto-calculation | High | [ ] |
| Major Incident flag | Checkbox on incident form that activates Major Incident Workbench | High | [ ] |
| SLA definitions | One SLA record per severity level — acknowledgment and resolution | High | [ ] |
| SLA breach notifications | Automated alerts at 75% and 100% of SLA window | High | [ ] |
| On-call routing | Assignment group routing to on-call schedule | High | [ ] |
| Major Incident Workbench | Stakeholder notification tracking, bridge call log | High | [ ] |
| Monitoring integration | Alert ingestion from monitoring platform — auto-creates incident records | Medium | [ ] |
| Incident reports | MTTA, MTTR, volume by severity, SLA compliance — standard report set | Medium | [ ] |
| Problem record auto-creation | Prompt on Sev 1/2 closure to create linked Problem record | Medium | [ ] |

---

#### Exception Handling

| Exception | Condition | Handling Procedure |
|---|---|---|
| Monitoring system offline | No automated alerts are firing | Team moves to manual monitoring checks every 15 minutes. SDM notified immediately. Monitoring restoration treated as Sev 2. |
| IC unavailable | On-call IC cannot be reached within 5 minutes of Sev 1 detection | Backup IC designated in on-call schedule activates. SDM notified. |
| Bridge call platform failure | Bridge call tool unavailable during major incident | Backup bridge call number activated. All parties notified via SMS and email. |
| ServiceNow unavailable | Cannot create or update incident records | Manual incident log initiated in shared document. All actions recorded with timestamps. Records retroactively entered in ServiceNow when restored. |

---

#### Related Documents

- Incident Management Runbook — detailed bridge call protocol and executive communication templates
- Problem Management Process Design — RCA process triggered by Sev 1/2 incidents
- Escalation Management Process Design — escalation paths beyond standard incident management
- Change Management Process Design — changes triggered by incident resolution

---

## Section 5 — Change Management Process Design

### Change Management — Process Design

**Process Owner:** Service Delivery Manager  
**Process Version:** 1.0  
**Last Reviewed:** May 2026  
**Next Review Due:** August 2026

---

#### Purpose

To control the lifecycle of all changes to production systems and services, enabling beneficial changes to be made with minimum disruption to existing services.

---

#### Scope

**In scope:**
- All changes to production systems, infrastructure, applications, configurations, and services
- Emergency changes required to restore service or address critical vulnerabilities
- Vendor and third-party changes that affect production systems the team supports

**Out of scope:**
- Changes to development or test environments with no production impact
- Standard operating procedures that do not modify production systems
- Business process changes with no IT system component

---

#### Definitions

| Term | Definition |
|---|---|
| Standard Change | Pre-approved, low-risk, routine change following a documented procedure |
| Normal Change | Planned change requiring CAB review and approval |
| Emergency Change | Unplanned change required immediately to restore service or address critical security risk |
| CAB | Change Advisory Board — governance body that reviews and approves normal changes |
| ECAB | Emergency Change Advisory Board — subset of CAB convened on-demand for emergency changes |
| FSC | Forward Schedule of Change — calendar of approved upcoming changes in ServiceNow |
| Rollback | The process of reversing a change if implementation fails |

---

#### Process Workflow

| Step | Description | Owner | ServiceNow Action | Time Target |
|---|---|---|---|---|
| 1 | Change identified and initiator creates change record in ServiceNow | Change Initiator | Create Change Request — select type (Standard / Normal / Emergency) | At identification |
| 2 | Change record completed — all required fields including implementation plan, rollback plan, risk assessment | Change Initiator | Complete all required fields — incomplete submissions returned without review | Minimum 5 business days before proposed window (Normal) |
| 3 | Standard Change: auto-approved via catalog item. Normal Change: submitted for CAB review. Emergency: ECAB convened. | Change Manager | Update State field — Submitted for Approval | Per type |
| 4 | CAB reviews normal changes at weekly meeting. ECAB convened within 2 hours for emergency changes. | CAB / ECAB | Approval recorded in ServiceNow Approval tab | Weekly CAB / On-demand ECAB |
| 5 | Approved change appears on FSC. Change owner confirms implementation window and resources. | Change Owner | Change added to FSC in ServiceNow Change Calendar | After approval |
| 6 | Go/No-Go checklist completed immediately before implementation window opens | Change Owner / SDM | Checklist documented in work notes | T-2 hours |
| 7 | Implementation executed per approved plan. All steps documented in work notes in real time. | Change Owner / Technical Team | Work notes updated at each step | During implementation |
| 8 | Post-implementation testing completed. Success or rollback decision made at defined decision point. | Change Owner | Update work notes with test results | Per implementation plan |
| 9 | Change closed in ServiceNow within 24 hours — outcome documented (successful / rolled back / partially implemented) | Change Owner | Set State to Closed. Complete outcome field. | Within 24 hrs |
| 10 | Emergency changes reviewed at next weekly CAB — was this a legitimate emergency or a planning failure? | Change Manager / SDM | Post-implementation review notes added to change record | Next weekly CAB |

---

#### SLA Targets

| SLA | Target | Measured From | Measured To | Breach Action |
|---|---|---|---|---|
| Normal change submission lead time | 5 business days minimum | Change record created | Proposed implementation window | Change returned — window rescheduled |
| CAB review turnaround | Weekly CAB meeting | Change submitted | CAB decision recorded | If missed — change held to next CAB |
| ECAB convening | 2 hours | Emergency change request initiated | ECAB decision recorded | SDM escalates to Director |
| Change record closure | 24 hours | Implementation complete | Change State set to Closed | SDM review — queue management |

---

#### KPIs and Performance Metrics

| KPI | Definition | Target | Data Source | Review Frequency |
|---|---|---|---|---|
| Change Success Rate | % of changes implemented without incident or rollback | ≥95% | ServiceNow Change Reports | Monthly |
| Emergency Change Rate | % of total changes classified as emergency | <10% | ServiceNow Change Reports | Monthly |
| Rollback Rate | % of changes requiring rollback | <5% | ServiceNow Change Reports | Monthly |
| Unauthorized Change Rate | Changes implemented without approved change record | 0% | ServiceNow audit / incident correlation | Monthly |
| Change-Induced Incident Rate | % of incidents caused by a recent change | Trending down | ServiceNow — incident/change correlation | Monthly |
| CAB Approval Rate | % of submissions approved at first review | Trending up | ServiceNow Approval Reports | Monthly |

---

#### ServiceNow Configuration Requirements

| Requirement | Description | Priority | Status |
|---|---|---|---|
| Change request form | Required fields, change type selection, risk assessment fields | High | [ ] |
| Standard Change Catalog | Pre-approved standard change templates | High | [ ] |
| CAB approval workflow | Approval routing to CAB members for normal changes | High | [ ] |
| ECAB approval workflow | Expedited approval routing for emergency changes | High | [ ] |
| Change Calendar / FSC | Forward Schedule of Change view — all approved upcoming changes | High | [ ] |
| Blackout period configuration | Frozen period dates visible in Change Calendar | Medium | [ ] |
| Change-to-incident linking | Ability to link change records to incident records for correlation | Medium | [ ] |
| Change reports | Success rate, emergency rate, rollback rate — standard report set | Medium | [ ] |

---

## Section 6 — Problem Management Process Design

### Problem Management — Process Design

**Process Owner:** Service Delivery Manager  
**Process Version:** 1.0  
**Last Reviewed:** May 2026  
**Next Review Due:** August 2026

---

#### Purpose

To identify and manage the root causes of incidents, prevent recurrence, and minimize the impact of incidents that cannot be prevented through the maintenance of known error information.

---

#### Scope

**In scope:**
- All Sev 1 and Sev 2 incidents — mandatory problem record
- Recurring Sev 3 incidents — problem record created at SDM discretion
- Proactively identified risks that could become incidents if not addressed

**Out of scope:**
- Individual Sev 3 and Sev 4 incidents that are not recurring
- Sev 4 incidents — handled through standard incident closure

---

#### Process Workflow

| Step | Description | Owner | ServiceNow Action | Time Target |
|---|---|---|---|---|
| 1 | Problem record created — linked to originating incident record(s) | SDM | Create Problem — link to incident record(s) | Within 24 hrs of Sev 1/2 closure |
| 2 | Problem assigned to Problem Manager. Target resolution date set based on severity. | SDM | Assign Problem. Set target resolution date. | At creation |
| 3 | RCA session scheduled — cross-functional team, blameless format | Problem Manager | Log PIR date in Problem record | Sev 1: within 48 hrs / Sev 2: within 72 hrs |
| 4 | RCA conducted — fishbone and 5 Whys methodology. Root cause documented. | Problem Manager | Document root cause, contributing factors, timeline in Problem record | At RCA session |
| 5 | If root cause identified but fix not yet implemented — Known Error record created in KEDB | Problem Manager | Create Known Error record — link to Problem. Document workaround. | At RCA session if applicable |
| 6 | Action items assigned — specific description, named owner, due date | Problem Manager | Create Problem Tasks — link to Problem record | At RCA session |
| 7 | Change request raised if fix requires production change | Problem Manager | Create Change Request — link to Problem record | Within 5 business days of RCA |
| 8 | Action items tracked monthly. Problem Manager reviews status with SDM. | Problem Manager / SDM | Problem Task status updated in ServiceNow | Monthly |
| 9 | Problem closed when root cause confirmed resolved and all action items complete | SDM | Set Problem State to Closed. Update KEDB if applicable. | After fix confirmed |

---

#### KPIs and Performance Metrics

| KPI | Definition | Target | Data Source | Review Frequency |
|---|---|---|---|---|
| PIR Completion Rate | % of Sev 1/2 with completed Problem records and documented root cause | 100% | ServiceNow Problem Reports | Monthly |
| Action Item Closure Rate | % of Problem Tasks closed by due date | ≥90% | ServiceNow Problem Task Reports | Monthly |
| Repeat Incident Rate | % of incidents caused by previously identified root cause | <10% | ServiceNow — incidents linked to known errors | Monthly |
| KEDB Utilization Rate | % of recurring incidents where KEDB entry existed and was referenced | Trending up | ServiceNow Known Error Reports | Monthly |
| Time to Root Cause | Average time from incident closure to documented root cause | Trending down | ServiceNow — incident close vs. problem RCA date | Monthly |

---

#### ServiceNow Configuration Requirements

| Requirement | Description | Priority | Status |
|---|---|---|---|
| Problem record form | Required fields, link to incident records, root cause documentation fields | High | [ ] |
| Problem Task creation | Task records linked to Problem for action item tracking | High | [ ] |
| Known Error Database (KEDB) | Known Error record type with workaround and fix fields | High | [ ] |
| KEDB search integration | Ability to search KEDB from incident record during triage | High | [ ] |
| Problem-to-change linking | Link Problem records to Change Requests | Medium | [ ] |
| Problem reports | PIR completion rate, action item closure, repeat incident rate | Medium | [ ] |

---

## Section 7 — Service Request Management Process Design

### Service Request Management — Process Design

**Process Owner:** Service Delivery Manager  
**Process Version:** 1.0  
**Last Reviewed:** May 2026  
**Next Review Due:** August 2026

---

#### Purpose

To fulfill standard service requests from users and customers in a consistent, timely, and controlled manner — keeping the incident queue focused on actual service disruptions.

---

#### Scope

**In scope:**
- Standard, pre-defined requests that can be fulfilled without a change record or incident investigation
- Access requests, software installations, hardware provisioning, account modifications
- Information requests and how-to queries that can be answered without service restoration

**Out of scope:**
- Service disruptions — these are incidents, not requests
- Requests that require a change record due to production system modification
- Requests that are not in the standard service catalog — these go through the CSR / change process

---

#### Process Workflow

| Step | Description | Owner | ServiceNow Action | Time Target |
|---|---|---|---|---|
| 1 | User submits request via self-service portal, email, or phone | User | Request record auto-created from portal OR analyst creates manually | At submission |
| 2 | Request received and categorized — matched to service catalog item | Tier 1 | Categorize request. Assign to appropriate fulfillment group. | Within 2 hours |
| 3 | Approval obtained if required (access requests, hardware procurement) | Approver | Approval workflow triggered in ServiceNow | Per catalog item SLA |
| 4 | Request fulfilled per standard catalog procedure | Fulfillment Team | Work notes updated at each fulfillment step | Per catalog item SLA |
| 5 | Requester notified of completion | Tier 1 | Set State to Fulfilled. Notify requester via ServiceNow. | At fulfillment |
| 6 | Request closed after requester confirmation or after 3 business days with no response | Tier 1 | Set State to Closed | Within 3 days of fulfillment |

---

#### SLA Targets

| SLA | Target | Measured From | Measured To | Breach Action |
|---|---|---|---|---|
| Request acknowledgment | 4 hours | Request created | Request categorized and assigned | Queue review |
| Standard request fulfillment | 3 business days | Request created | Request set to Fulfilled | SDM review |
| Access request fulfillment | 1 business day | Approval received | Access granted | SDM review |
| Hardware provisioning | 5 business days | Approval received | Hardware delivered | Procurement review |

---

#### ServiceNow Configuration Requirements

| Requirement | Description | Priority | Status |
|---|---|---|---|
| Service Request Catalog | Catalog items for all standard requests — one item per request type | High | [ ] |
| Approval workflows | Approval routing for requests requiring authorization | High | [ ] |
| Fulfillment group routing | Automatic assignment to correct fulfillment team by catalog item | High | [ ] |
| SLA definitions | One SLA per catalog item category | High | [ ] |
| Self-service portal | User-facing portal for request submission and status tracking | Medium | [ ] |
| Request reports | Volume by category, fulfillment rate, SLA compliance | Medium | [ ] |

---

## Section 8 — Escalation Management Process Design

### Escalation Management — Process Design

**Process Owner:** Service Delivery Manager  
**Process Version:** 1.0  
**Last Reviewed:** May 2026  
**Next Review Due:** August 2026

---

#### Purpose

To define the conditions under which standard processes are insufficient and a higher level of authority, resource, or visibility is required — ensuring that escalations are consistent, fast, and never left without an owner.

---

#### Scope

**In scope:**
- Internal escalation — moving an incident, problem, or request to a higher support tier or management level
- Customer escalation — managing situations where the customer has escalated directly to leadership
- Executive escalation — situations requiring VP or C-suite involvement

**Out of scope:**
- Routine ticket assignments and reassignments — these are not escalations
- Vendor escalation — covered under Vendor Management Framework

---

#### Escalation Tiers

| Tier | Who | When | Trigger |
|---|---|---|---|
| **Tier 1 → Tier 2** | Senior Engineer / SME | Incident or request beyond Tier 1 resolution capability | Tier 1 cannot resolve within 50% of SLA window |
| **Tier 2 → SDM** | Service Delivery Manager | Sev 1 at detection. Sev 2 at 30 min with no resolution path. Any customer complaint. | SLA at 75% with no resolution path. Scope expansion. Customer escalation received. |
| **SDM → Director/VP** | Director of Operations / VP | Sev 1 at 60 min unresolved. Data loss or security component confirmed. | SDM determines current resources insufficient. Customer executive has escalated. |
| **Director → Executive** | C-Suite | Sev 1 at 2 hours unresolved. Regulatory or legal implications. Major customer contract at risk. | Director determines executive visibility required. |

---

#### Customer Escalation Handling

When a customer escalates directly — bypassing the standard support process and contacting leadership — the response protocol is:

| Step | Action | Owner | Time Target |
|---|---|---|---|
| 1 | SDM notified of customer escalation — regardless of channel | Whoever receives it | Immediate |
| 2 | SDM contacts the customer directly — acknowledges the escalation | SDM | Within 1 hour |
| 3 | SDM conducts internal review — what is the current status of the issue? | SDM | Within 1 hour of notification |
| 4 | SDM provides the customer with a specific update — status, root cause if known, action being taken | SDM | Within 2 hours of escalation |
| 5 | Executive sponsor notified if customer is VP-level or above | SDM | Within 1 hour of escalation receipt |
| 6 | Resolution delivered. SDM follows up with customer personally after closure. | SDM | At resolution |
| 7 | Post-escalation review — what caused the escalation? Was it a process failure or a customer expectation gap? | SDM | Within 5 business days |

**Critical rule:** A customer escalation is never routed back into the standard queue. The SDM owns it from the moment it is received until the customer confirms satisfaction.

---

#### KPIs and Performance Metrics

| KPI | Definition | Target | Data Source | Review Frequency |
|---|---|---|---|---|
| Escalation Rate — Internal | % of incidents requiring Tier 2+ | Trending down | ServiceNow Incident Reports | Monthly |
| Customer Escalation Count | Number of customer-initiated escalations per month | Zero target — any escalation triggers review | ServiceNow — escalation flag | Monthly |
| Escalation Response Time | Time from escalation trigger to SDM acknowledgment | ≤30 minutes | ServiceNow timestamps | Monthly |
| Escalation Resolution Time | Time from escalation trigger to resolution | Trending down | ServiceNow — escalation open/close | Monthly |

---

#### ServiceNow Configuration Requirements

| Requirement | Description | Priority | Status |
|---|---|---|---|
| Escalation flag | Field on incident record to mark as escalated — with escalation tier | High | [ ] |
| Escalation notifications | Automated alerts when escalation flag is set | High | [ ] |
| Customer escalation category | Separate categorization for customer-initiated escalations | High | [ ] |
| Escalation reports | Count, response time, resolution time by tier | Medium | [ ] |

---

## Section 9 — Process Interdependencies

The five processes in this document do not operate independently. They connect at specific handoff points. A handoff that is not designed explicitly is a gap — and gaps surface as incidents.

### Key Handoff Points

| From Process | To Process | Trigger | What Transfers |
|---|---|---|---|
| Incident Management | Problem Management | Sev 1 or Sev 2 incident closed | Incident record, work notes, timeline, preliminary root cause hypothesis |
| Incident Management | Change Management | Resolution requires a production change | Incident record linked to change request — urgency drives change classification |
| Problem Management | Change Management | RCA identifies fix requiring production change | Problem record linked to change request — root cause documented |
| Change Management | Incident Management | Change causes a service disruption | Change record linked to incident — change-induced incident flagged |
| Service Request Management | Change Management | Request requires a production system modification | Request record linked to change request — requester notified of process |
| Escalation Management | Incident Management | Escalation resolves into incident | Escalation context documented in incident work notes |
| Escalation Management | Problem Management | Customer escalation reveals systemic issue | Problem record created — escalation context included |

### The Handoff Rules

**Rule 1 — The record follows the handoff.**
When a process hands off to another process, the originating record is linked to the new record in ServiceNow. No handoff without a link. No link — no audit trail.

**Rule 2 — Context transfers completely.**
The receiving process team reads the originating record before acting. A Tier 2 engineer who picks up an escalated incident without reading the Tier 1 work notes is starting from zero — which extends MTTR and frustrates the customer.

**Rule 3 — Handoffs are not handoffs until confirmed.**
The sending team does not consider the work done until the receiving team acknowledges the handoff in ServiceNow. Assignment without acknowledgment is not a handoff — it is a hope.

---

## Section 10 — ServiceNow Configuration Requirements Summary

This section consolidates all ServiceNow configuration requirements from all five processes into a single prioritized list for the ServiceNow administrator.

### Priority 1 — Required Before Any Process Goes Live

- [ ] Incident form — required fields, Impact/Urgency matrix, Priority auto-calculation
- [ ] Incident SLA definitions — all four severity levels, acknowledgment and resolution
- [ ] SLA breach notifications — 75% and 100% automated alerts
- [ ] Major Incident flag and workbench
- [ ] Problem record form — required fields, link to incident records
- [ ] Problem Task creation and tracking
- [ ] Known Error Database (KEDB) — record type and search integration
- [ ] Change request form — all change types, required fields
- [ ] CAB and ECAB approval workflows
- [ ] Change Calendar / Forward Schedule of Change
- [ ] Service Request Catalog — minimum viable catalog items
- [ ] Escalation flag and notifications on incident records
- [ ] On-call routing — assignment group to on-call schedule

### Priority 2 — Required Within 30 Days of Go-Live

- [ ] Monitoring integration — auto-ingestion of alerts as incident records
- [ ] Self-service portal — user-facing request submission
- [ ] Standard Change Catalog — pre-approved standard change templates
- [ ] Blackout period configuration on Change Calendar
- [ ] KEDB search from incident record during triage
- [ ] Problem-to-change and change-to-incident linking

### Priority 3 — Required Within 60 Days of Go-Live

- [ ] Standard report set — incident volume, MTTA, MTTR, SLA compliance
- [ ] Change reports — success rate, emergency rate, rollback rate
- [ ] Problem reports — PIR completion, action item closure, repeat incident rate
- [ ] Service request reports — volume by category, fulfillment rate
- [ ] Escalation reports — count, response time, resolution time
- [ ] Automated CSAT survey on incident closure

---

## Section 11 — Process Governance & Continuous Improvement

### Process Ownership

Every process has a single accountable owner. The owner is responsible for keeping the process current, reviewing performance metrics monthly, and initiating updates when the process is not working.

| Process | Owner | Review Cadence |
|---|---|---|
| Incident Management | Service Delivery Manager | Monthly metrics / Quarterly document review |
| Change Management | Service Delivery Manager | Monthly metrics / Quarterly document review |
| Problem Management | Service Delivery Manager | Monthly metrics / Quarterly document review |
| Service Request Management | Service Delivery Manager | Monthly metrics / Quarterly document review |
| Escalation Management | Service Delivery Manager | Monthly metrics / Quarterly document review |

In a greenfield build, the SDM owns all five processes initially. As the team grows and senior roles are hired, process ownership is distributed — but the SDM retains accountability for the overall process framework.

### Process Review Triggers

A process is reviewed when any of the following occur:

- A KPI is below target for two consecutive months
- A major incident exposes a process gap
- A customer escalation traces back to a process failure
- A team member identifies a gap or improvement opportunity
- The organization scales significantly — team size, customer count, or ticket volume changes materially

A process review does not require a complete rewrite. Most reviews result in one or two targeted changes to specific steps or escalation triggers. Document every change in the process change log.

### Monthly Operations Review — Process Health Agenda Item

Process health is reviewed monthly as part of the standard operations review. The SDM presents:

1. KPI performance for each process — trending green, yellow, or red
2. Any process gaps identified during the month — from incidents, escalations, or team feedback
3. Process changes implemented since last review
4. Upcoming process changes planned

A process that is never discussed in the monthly review is a process that is not being managed.

### Continuous Improvement Cycle

```
Measure → Identify Gap → Design Improvement → Implement → Validate → Measure
```

Every improvement starts with a metric that is trending wrong. Every improvement ends with a validation that the metric has improved. Improvements that cannot be validated with data are not improvements — they are changes.

---

## Appendix A — Process Design Checklist

Use this checklist when adding a new process or conducting a quarterly review of an existing process.

- [ ] Purpose is stated in one to three sentences — clear and specific
- [ ] In-scope and out-of-scope are both defined explicitly
- [ ] All terms that could be interpreted differently are defined
- [ ] Every workflow step has an owner, a ServiceNow action, and a time target
- [ ] Every decision point is documented with both branches
- [ ] Every escalation trigger is specific and measurable — not "when necessary"
- [ ] All SLAs have a measurement start, measurement end, and breach action
- [ ] All KPIs have a target and a named data source in ServiceNow
- [ ] All ServiceNow configuration requirements are listed and prioritized
- [ ] Exception handling covers the most likely failure scenarios
- [ ] RACI matrix is complete — no activity without a Responsible and Accountable
- [ ] Process change log is current
- [ ] Next review date is set

---

## Appendix B — RACI Legend

| Code | Role | Definition |
|---|---|---|
| **R** | Responsible | Does the work. Executes the activity. |
| **A** | Accountable | Owns the outcome. Signs off on completion. Only one A per activity. |
| **C** | Consulted | Provides input before or during the activity. Two-way communication. |
| **I** | Informed | Notified of the outcome. One-way communication. |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release — five core processes | Scott Boehler |

---

*A process that exists only in this document is not a process — it is a plan. The test of every process defined here is whether the team follows it under pressure, on a Friday night, when the customer is calling and the system is down. Design for that moment.*
