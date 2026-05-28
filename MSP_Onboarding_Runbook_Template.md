# MSP Onboarding & IT Cutover Runbook Template
### Enterprise IT Operations | Managed Service Provider Transition Framework

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Applies To:** Any IT environment transitioning from a legacy support model to a managed service provider (MSP) or standardized managed services environment

---

## Purpose & Scope

This template defines the structure and content requirements for an MSP onboarding and IT cutover runbook. It is designed to be instantiated once per site, operating company, or discrete migration event.

A cutover runbook without a clear structure is not a runbook — it is a checklist with ambition. This template ensures every migration event is planned consistently, executed with clear accountability, and governed by Go/No-Go criteria that protect the business.

The Service Delivery Manager (SDM) is the single accountable owner for cutover planning, execution, and post-go-live stability. Every section of this runbook reflects that accountability.

---

## How to Use This Template

For each new migration event:

1. Copy this template and create a new instance
2. Fill in all `[bracketed placeholders]` with site-specific details
3. Review Section 7 — Pre-Cutover Checklist — with the MSP and infrastructure teams before setting a cutover date
4. Do not open a cutover window until every Go/No-Go dependency in Section 7.1 is confirmed green
5. Archive the completed runbook in the ITSM system after hypercare closes

---

## Table of Contents

| Section | Title |
|---|---|
| 1 | System Overview |
| 2 | Security and Access Control |
| 3 | System Configuration |
| 4 | Configuration Management |
| 5 | Monitoring and Alerting |
| 6 | Operational Tasks — Cutover Execution |
| 7 | Maintenance Tasks |
| 8 | Failure and Recovery Procedures |
| 9 | Contact Details |

---

## Section 1 — System Overview

### 1.1 Service Overview

**What to document here:**
- What is being transitioned — describe the current support model (legacy local IT, self-managed, previous MSP) and the target state (new MSP, standardized managed services environment)
- Which site, business unit, or operating company this runbook instance covers
- Who the SDM is and what their accountability covers
- What "done" looks like — define what fully onboarded means for this engagement

**Key questions this section must answer:**
- What are we moving from and what are we moving to?
- Who owns the outcome?
- When is the engagement considered complete?

---

### 1.2 Platforms and Tools in Scope

**What to document here:**
List every platform or tool that will be active in the target state post-cutover. For each one, define its purpose so anyone reading the runbook understands what it does and why it matters.

| Platform / Tool | Purpose |
|---|---|
| [Identity Platform — e.g. Entra ID, Okta] | User authentication, SSO, device registration |
| [ITSM Platform — e.g. Jira SM, ServiceNow] | Ticket management, SLA tracking, incident and change workflow |
| [RMM Tool — e.g. NinjaOne, ConnectWise] | Endpoint monitoring, patch management, alerting |
| [EDR Tool — e.g. SentinelOne, CrowdStrike] | Endpoint threat detection and response |
| [Vulnerability Management — e.g. Rapid7, Tenable] | Infrastructure scanning and remediation tracking |
| [Network Security — e.g. Check Point, Palo Alto] | Network security, remote access for distributed workforce |
| [Productivity Suite — e.g. M365, Google Workspace] | Email, collaboration, file storage |
| [Additional tools as applicable] | |

---

### 1.3 Hours of Operation

**What to document here:**
- Standard business hours for the site being onboarded
- Any non-standard operational windows (field crews, shift workers, global time zones)
- MSP service desk coverage hours
- Preferred cutover window — day of week, time of day, rationale

---

### 1.4 Execution Design

**What to document here:**
The high-level approach to the migration. Cover:
- Whether this is a phased approach or a single cutover event
- Pre-cutover activities (discovery, inventory, user provisioning, tool deployment, UAT)
- Change freeze window — how many days before cutover, what is restricted
- Cutover night sequence at a high level
- Post-cutover hypercare period — duration and what it covers

---

### 1.5 Current Environment (Pre-Cutover State)

**What to document here:**
A snapshot of the environment as it exists before migration begins. This is the rollback reference — if cutover fails, this is what you restore to. Do not start a cutover without this documented.

| Component | Pre-Cutover State |
|---|---|
| Identity / Directory | [Local AD / No formal directory / Previous cloud identity] |
| Endpoint Management | [Unmanaged / Legacy MDM / Previous RMM tool] |
| Security | [Describe existing AV, EDR, or security tooling] |
| Ticketing / Support | [None / Local system / Previous MSP portal] |
| Network / Internet | [Describe ISP and network topology] |
| Email / Productivity | [On-prem / Legacy cloud tenant / Previous provider] |

---

### 1.6 Resilience and Rollback Design

**What to document here:**
- SLA commitments from the MSP for post-go-live support (P1, P2, P3, P4 response and resolution targets)
- Platform availability commitments for SaaS components
- Rollback authority — who can declare a rollback and up to what point in the cutover window
- Partial rollback capability — can specific services be rolled back independently?

---

### 1.7 Cutover Team — Roles and Responsibilities

**What to document here:**
Every role that has a responsibility during the cutover window. No unnamed roles — by the time this runbook is used on cutover night, every role has a named person behind it.

| Role | Responsibility During Cutover |
|---|---|
| Service Delivery Manager (SDM) | Overall cutover lead — Go/No-Go authority, executive communications, rollback decision |
| MSP Migration Lead | Technical execution of all cutover steps |
| MSP Service Desk | On-call during cutover night and hypercare period |
| Site Contact | On-site point of contact at the migrating location |
| Infrastructure / Identity Team | Identity platform provisioning and network validation |
| IT Director / Executive Sponsor | Notified of Go/No-Go decision and cutover completion — escalation authority |

---

### 1.8 Peak and Quiet Periods

**What to document here:**
When is this environment busiest? When is the safest window for maintenance and cutover?

- **Peak periods** — days and times when maximum users are active and system availability is most critical
- **Warm periods** — moderate activity, some tolerance for brief disruption
- **Quiet periods** — preferred windows for patching, maintenance, and cutover execution

This informs the cutover window selection and the hypercare support posture.

---

## Section 2 — Security and Access Control

### 2.1 Access Requirements

**What to document here:**
The access control state before, during, and after cutover. This section must be complete before cutover begins.

| Access Type | Requirements |
|---|---|
| End User Accounts | [How user accounts are provisioned in the new environment — timing relative to cutover] |
| Admin Accounts | [MFA requirements, privileged access controls, separate admin account policy] |
| MSP Service Accounts | [What access level the MSP has — read vs. write, which platforms] |
| Legacy Account Handling | [When legacy accounts are disabled — at cutover or after hypercare? Who signs off on deletion?] |
| Remote Access | [How remote and field users access the environment post-cutover] |

**Critical rule:** Legacy accounts are disabled at cutover — not deleted. Deletion requires SDM sign-off after the hypercare period confirms no dependency on legacy accounts exists.

---

### 2.2 Security Platform Deployment Dependencies

**What to document here:**
List every security tool that must be deployed and active before cutover is permitted to proceed. These are Go/No-Go dependencies — if they are not confirmed, cutover does not happen.

- [EDR tool] deployed to [X]% of endpoints — target percentage before Go/No-Go
- [Network security tool] enrolled on all remote and field devices
- [Vulnerability scanner] — baseline scan complete, critical findings remediated
- [Identity platform] — conditional access policies applied and tested

---

### 2.3 Data Classification and Compliance

**What to document here:**
Any regulated or sensitive data that needs special handling during migration. HR data, financial data, healthcare data, PII. Confirm with legal or compliance whether specific handling requirements apply and document them here.

---

## Section 3 — System Configuration

### 3.1 Standard Configuration Baseline

**What to document here:**
Every configuration item that must be validated as complete before the Go/No-Go checkpoint. This is not a wish list — it is the minimum viable configuration for the environment to be considered ready. SDM validates completion; MSP is accountable for technical delivery.

| Configuration Item | Owner | Pre-Cutover Status |
|---|---|---|
| [Identity platform configured] | [Owner] | [ ] Complete |
| [User accounts provisioned and tested] | [Owner] | [ ] Complete |
| [RMM agents deployed to all endpoints] | [Owner] | [ ] Complete |
| [EDR agents deployed and active] | [Owner] | [ ] Complete |
| [Network security enrolled on all devices] | [Owner] | [ ] Complete |
| [ITSM queues configured and tested] | [Owner] | [ ] Complete |
| [Productivity suite licenses assigned] | [Owner] | [ ] Complete |
| [MFA enforced — all users] | [Owner] | [ ] Complete |
| [Vulnerability baseline scan complete] | [Owner] | [ ] Complete |
| [UAT sign-off obtained from site contact] | [Owner] | [ ] Complete |

---

### 3.2 Legacy Environment Documentation

**What to document here:**
Before touching anything in the legacy environment, document it. This is the rollback reference. Minimum required:

- Active Directory or directory service — user list exported, structure documented
- Network topology — IP ranges, DHCP server, DNS servers
- Existing security tools — names, versions, agent coverage
- Current support contact method for users
- Installed applications on managed endpoints — what do users depend on day to day?

---

## Section 4 — Configuration Management

### 4.1 Change Freeze

**What to document here:**
- How many days before cutover the change freeze begins (typically 14 days)
- What is restricted — no infrastructure changes, software deployments, or network modifications without SDM approval
- The formal process for exceptions — how are emergency changes handled during the freeze?
- Who enforces the freeze and how violations are handled

---

### 4.2 Backup Requirements

**What to document here:**

**Pre-cutover backup:**
- Full backup of all in-scope servers and endpoints — timing relative to cutover (within 72 hours is standard)
- Backup verification — restoration test on at least one critical system before cutover proceeds
- Retention period — minimum 90 days post-cutover recommended
- Where backup confirmation is logged (ITSM ticket, runbook sign-off)

**Special files to export before cutover:**
- User list from legacy directory (exported, not just noted)
- Network configuration exports — firewall rules, DNS, DHCP settings
- Legacy ITSM data export if historical ticket data needs to be retained

**Restore procedure:**
- Who declares rollback and notifies whom
- Steps to restore from backup — technical procedure owned by MSP
- How users are notified if rollback occurs
- Post-incident review requirement after any rollback

---

## Section 5 — Monitoring and Alerting

### 5.1 Active Monitoring Tools

**What to document here:**
Every tool that is monitoring the environment post-cutover, and exactly what it monitors.

| Tool | Monitors |
|---|---|
| [RMM Tool] | Endpoint health, patch compliance, offline devices, CPU/disk/memory thresholds |
| [EDR Tool] | Endpoint threats, malware alerts, policy violations |
| [Vulnerability Scanner] | Open vulnerabilities, remediation status, new asset discovery |
| [ITSM Platform] | SLA breach alerts, ticket aging, queue volume |
| [Identity Platform] | Sign-in failures, MFA bypass attempts, conditional access violations |

---

### 5.2 Hypercare Alert Thresholds

**What to document here:**
During the hypercare period, define the specific events that require immediate SDM notification. These thresholds are tighter than steady-state because the environment is new and instability is higher risk in the first 30 days.

Examples of what to define:
- Percentage of endpoints offline simultaneously that triggers escalation
- Number of user authentication failures in a defined time window
- Ticket acknowledgment SLA breach that triggers SDM involvement
- Severity of vulnerability discovered post-cutover that triggers emergency response

---

### 5.3 Daily Health Check — Hypercare Period

**What to document here:**
The daily health check agenda for the SDM and MSP stand-up during the hypercare period.

- [RMM tool] endpoint compliance report — all devices online and patched
- ITSM ticket volume and SLA compliance — previous 24 hours
- [EDR tool] threat summary — active or unresolved alerts
- Open P1/P2 incidents — status and resolution ETA
- User-reported issues from site contact — anything not captured in the ticketing system

---

### 5.4 Reporting Cadence

**What to document here:**

| Report | Frequency | Audience |
|---|---|---|
| Hypercare Daily Stand-Up | Daily | SDM, MSP Migration Lead, Site Contact |
| Hypercare Weekly Summary | Weekly | SDM to [IT Director / Executive Sponsor] |
| Monthly Business Review (MBR) | Monthly post-hypercare | SDM to [Operations Leadership] |
| Executive Summary | [Frequency] | [Executive audience — define who receives this] |

---

## Section 6 — Operational Tasks — Cutover Execution

### 6.1 Pre-Cutover Checklist (T-14 Days to T-0)

**What to document here:**
Every task that must be completed before the Go/No-Go checkpoint. Each task has an owner and a target date relative to cutover (T-14 days, T-10 days, etc.). SDM signs off on readiness.

| Task | Owner | Target Date |
|---|---|---|
| User inventory complete — all accounts mapped | [Owner] | T-14 days |
| Identity platform accounts provisioned and tested | [Owner] | T-10 days |
| RMM agents deployed to all endpoints | [Owner] | T-10 days |
| EDR agents deployed and active | [Owner] | T-10 days |
| Network security enrolled on all devices | [Owner] | T-7 days |
| End-user communication sent — cutover announcement | SDM | T-7 days |
| UAT completed — site contact sign-off obtained | SDM / Site Contact | T-5 days |
| Change freeze enforced | SDM | T-14 days |
| Vulnerability scan complete — critical findings resolved | [Owner] | T-5 days |
| Rollback plan reviewed and approved by all parties | SDM / MSP | T-3 days |
| Cutover workbook distributed to all parties | SDM | T-2 days |
| Go/No-Go meeting held | SDM | T-2 hours |

---

### 6.2 Go/No-Go Criteria

**What to document here:**
The specific conditions that must be true for cutover to proceed. If any condition is red at the Go/No-Go checkpoint, cutover does not happen. This is not a negotiation — it is a gate.

Every Go/No-Go checklist must include:

- [ ] All pre-cutover configuration items confirmed complete (Section 3.1)
- [ ] Security tools deployed to defined minimum coverage percentage
- [ ] UAT sign-off received from site contact
- [ ] Vulnerability scan — no critical findings outstanding
- [ ] Rollback plan confirmed and all parties know their role
- [ ] All cutover night participants confirmed available and on standby
- [ ] Backup completed and verified within 72 hours
- [ ] Change freeze active — no unauthorized changes in past 14 days
- [ ] End-user communications sent and acknowledged

---

### 6.3 Cutover Night Execution

**What to document here:**
The step-by-step cutover sequence. Every step has a time target, a description, and a named owner. This is the script for cutover night — nobody improvises.

Format:

| Time | Step | Owner |
|---|---|---|
| T-2 hours | Go/No-Go checkpoint — all pre-cutover items confirmed green | SDM |
| T-0 | Bridge open — all parties confirmed on communications channel | SDM |
| T+[time] | [Step description] | [Owner] |
| T+[time] | [Step description] | [Owner] |
| T+[final checkpoint] | Final validation — all systems green. SDM declares Go-Live. | SDM |
| T+[+15 min] | Executive sponsor notified — cutover complete | SDM |
| T+[+30 min] | Bridge closed. Hypercare period begins. | SDM |

**Design principles for this table:**
- Every step has an expected completion time — not just a sequence
- Validation steps follow every major technical step — don't move forward without confirming the last step worked
- The Go-Live declaration is always made by the SDM — not the MSP, not the engineer who finished the last task
- Define the last rollback checkpoint explicitly — after this time, rollback requires executive approval

---

### 6.4 End-User Communications

**What to document here:**
The communication schedule for end users before, during, and after cutover. SDM owns all communications.

| Timing | Communication | Content |
|---|---|---|
| T-14 days | Announcement | What is changing, what users need to do, support contact after cutover |
| T-7 days | Reminder | New ITSM portal instructions, MSP contact details |
| T-1 day | Final notice | Cutover tonight, no changes to systems after [time], who to call if issues |
| Day+1 morning | Post-cutover notice | New support process is live, ITSM portal link, hypercare contact |

---

### 6.5 Hypercare Period

**What to document here:**
- Duration — 30 days is standard; adjust based on environment complexity
- SDM on-call commitment — 24x7 for first 7 days is recommended for complex migrations
- Daily stand-up cadence — time, attendees, agenda
- What triggers SDM direct involvement during hypercare
- Hypercare close-out criteria — what must be true for SDM to sign off on hypercare completion and handoff to BAU support

---

## Section 7 — Maintenance Tasks

### 7.1 Patching

**What to document here:**

**Standard patch cycle:**
- Endpoints — frequency, window, tool used, who manages, who reviews
- Servers — frequency, maintenance window process, notification lead time to SDM
- SaaS tools — evergreen / vendor-managed, who monitors for anomalies

**Zero-day response:**
- Notification timeline — when MSP notifies SDM of a zero-day affecting the environment
- Assessment process — SDM and MSP assess scope and impact together
- Emergency change process — how is an emergency patch authorized and executed?
- Target deployment timeline for critical zero-days

---

### 7.2 Routine Operational Checks

**What to document here:**
The recurring checks that keep the environment healthy in steady state. Define frequency and owner for each.

| Check | Frequency | Owner |
|---|---|---|
| Endpoint compliance report — offline/unpatched devices | Weekly | MSP |
| Vulnerability aging review — findings past SLA flagged | Weekly | MSP → SDM |
| EDR policy compliance audit — all endpoints on current policy | Monthly | MSP |
| Identity platform access review — stale accounts, orphaned permissions | Monthly | MSP → SDM |
| ITSM SLA compliance review | Monthly | SDM |
| Backup verification | Monthly | MSP |

---

### 7.3 Post-Deployment Testing

**What to document here:**
The standard test checklist executed after any major change or patch deployment. This is the minimum bar before a change is considered closed.

- Endpoint health confirmed — no offline devices in RMM tool
- Threat detection status clear — no active alerts in EDR tool
- Test ITSM ticket submitted and routed correctly
- Sample user sign-in test — define number and confirm identity platform working
- Site contact confirms no user-reported issues within [timeframe]

---

## Section 8 — Failure and Recovery Procedures

### 8.1 Rollback Criteria

**What to document here:**
The specific conditions that trigger a rollback — automatic and discretionary.

**Automatic rollback triggers** — SDM calls rollback immediately if any of these occur:
- [Authentication failure threshold] — define % of users unable to authenticate by a defined point in the cutover sequence
- [Endpoint visibility threshold] — define % of endpoints offline in RMM tool by a defined point in the sequence
- [Critical application unavailable] — name the business-critical applications; if any are inaccessible at a defined checkpoint, rollback
- [Security event] — active threat detected during cutover window

**Rollback authority:**
- During the cutover window up to the final rollback checkpoint: SDM has unilateral rollback authority
- After the final rollback checkpoint: rollback requires executive sponsor approval

---

### 8.2 Rollback Procedure

**What to document here:**
Step by step — what happens when SDM declares rollback.

1. SDM declares rollback on the bridge — timestamp logged in the ITSM cutover ticket
2. MSP halts all cutover steps immediately
3. Infrastructure team re-enables legacy accounts and legacy environment
4. MSP confirms legacy environment accessible — test user sign-in completed
5. Site Contact confirms users can work normally — verbal confirmation on bridge
6. SDM notifies executive sponsor — rollback complete, new cutover date to be determined
7. Bridge closed — timestamp logged
8. Post-incident review scheduled within 48 hours — root cause analysis required before new cutover date is set

---

### 8.3 Major Incident During Hypercare

**What to document here:**
The incident response process specific to the hypercare period. This is tighter than steady-state because the environment is newly migrated and the SDM maintains direct involvement.

- How P1 is detected or reported during hypercare
- MSP notification timeline to SDM — define in minutes, not hours
- SDM join timeline for bridge call
- Executive sponsor notification requirement
- Status update cadence during the incident
- Post-incident review requirement — timing and format

---

### 8.4 Common Cutover Failure Scenarios

**What to document here:**
The failure scenarios most likely to occur during this specific cutover — and the first response for each. This is written before cutover night, not improvised during it.

| Issue | First Response |
|---|---|
| Users cannot authenticate | [Define first diagnostic step and who executes it] |
| Endpoints not appearing in RMM tool | [Define first diagnostic step and who executes it] |
| Security tool not active on endpoints | [Define first diagnostic step and who executes it] |
| ITSM tickets not routing correctly | [Define first diagnostic step and who executes it] |
| Remote users cannot connect | [Define first diagnostic step and who executes it] |
| [Add environment-specific scenarios] | |

---

## Section 9 — Contact Details

### 9.1 Internal IT Team

**What to document here:**
Every internal team member with a role in the cutover. Name, phone, email, and role. No unnamed contacts — by cutover night, every row has a person behind it.

| Role | Name | Phone | Email | Notes |
|---|---|---|---|---|
| Service Delivery Manager | | | | Primary cutover lead and P1 escalation |
| IT Director / Executive Sponsor | | | | Executive escalation and rollback authority |
| Infrastructure / Identity Team | | | | Identity platform and network support |

---

### 9.2 MSP Team

**What to document here:**

| Role | Name | Phone | Email | Notes |
|---|---|---|---|---|
| MSP Migration Lead | | | | Technical lead on cutover night |
| MSP Service Desk | | | | 24x7 support — post-cutover |
| MSP Escalation Manager | | | | P1 escalation if service desk unresponsive |

---

### 9.3 Site Contact

**What to document here:**

| Role | Name | Phone | Email | Notes |
|---|---|---|---|---|
| Site Contact (Primary) | | | | On-site during cutover and Day+1 |
| Site Contact (Backup) | | | | Available if primary is unavailable |
| General Manager / Business Lead | | | | Business escalation if operations impacted |

---

### 9.4 Vendor Support Lines

**What to document here:**
Support contact information for every third-party vendor or platform in scope. For each one, define whether the MSP manages the relationship or the internal team manages it directly.

| Vendor | Support Contact | Managed By |
|---|---|---|
| [Identity Platform Vendor] | [Support line / portal] | [MSP / Internal] |
| [EDR Vendor] | [Support line / portal] | [MSP / Internal] |
| [RMM Vendor] | [Support line / portal] | [MSP / Internal] |
| [Vulnerability Scanner Vendor] | [Support line / portal] | [MSP / Internal] |
| [Network Security Vendor] | [Support line / portal] | [MSP / Internal] |
| [Productivity Suite Vendor] | [Support line / portal] | [MSP / Internal] |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release — generic template | Scott Boehler |

---

*A cutover runbook that sits in a drawer until the night of the migration is not a runbook — it is a hope. Build it, walk through it with the team, and know every step before you open the bridge.*
