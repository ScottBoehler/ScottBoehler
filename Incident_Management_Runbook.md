# Incident Management Runbook
### Enterprise IT Operations | Major Incident Response Framework

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Applies To:** All severity-classified incidents impacting production systems, customer-facing services, or critical infrastructure

---

## Purpose & Scope

This runbook defines the end-to-end process for identifying, responding to, escalating, and resolving IT incidents across a 24x7x365 enterprise operations environment. It establishes clear roles, communication standards, escalation paths, and post-incident practices that ensure consistent, accountable incident response regardless of the time of day or who is on shift.

This framework is built on ITIL v4 principles and is designed to integrate with ServiceNow as the system of record for all incident lifecycle management.

**What this runbook covers:**
- Severity classification and priority assignment
- Roles and responsibilities during active incidents
- Response timeline standards by severity level
- Bridge call protocol and communication cadence
- Executive notification standards
- Escalation paths including vendor escalation
- Post-Incident Review (PIR) and Root Cause Analysis (RCA)
- Metrics, SLA tracking, and continuous improvement

**What this runbook does not cover:**
- Security incident response (handled under separate Security Incident Response Plan)
- Disaster recovery and business continuity (handled under separate BCP/DR procedures)
- Routine service requests and standard change execution

---

## Section 1 — Severity Classification Matrix

Every incident is assigned a severity level at the time of detection. Severity drives response speed, resource mobilization, and executive notification requirements. Severity is set in the ServiceNow incident record at creation and can be escalated — never downgraded — during an active incident without Incident Commander approval.

### Severity Definitions

| Severity | Label | Business Impact | Examples |
|---|---|---|---|
| **Sev 1** | Critical | Complete service outage. Multiple customers or business-critical systems unavailable. Revenue impact active or imminent. | Core platform down, payment processing failure, complete network outage, data center event |
| **Sev 2** | Major | Significant degradation. Core functionality impaired for a subset of customers or users. Workaround may exist but is not sustainable. | Primary application degraded, high error rates, latency exceeding SLA thresholds, partial outage |
| **Sev 3** | Moderate | Non-critical service impacted. Limited customer impact. Workaround available and sustainable short-term. | Secondary system degraded, isolated user reports, monitoring alert without confirmed customer impact |
| **Sev 4** | Minor | Minimal or no customer impact. Informational or proactive. No immediate action required beyond tracking. | Single-user issue, cosmetic defect, low-priority alert, scheduled maintenance follow-up |

### Priority Assignment in ServiceNow

ServiceNow calculates priority automatically based on two fields set at incident creation:

- **Impact** — How many users, customers, or systems are affected (High / Medium / Low)
- **Urgency** — How quickly does this need to be resolved before business impact escalates (High / Medium / Low)

| Impact \ Urgency | High | Medium | Low |
|---|---|---|---|
| **High** | P1 — Sev 1 | P2 — Sev 2 | P3 — Sev 3 |
| **Medium** | P2 — Sev 2 | P3 — Sev 3 | P3 — Sev 3 |
| **Low** | P3 — Sev 3 | P4 — Sev 4 | P4 — Sev 4 |

**Critical rule:** When in doubt, classify higher. It is always better to mobilize resources for a Sev 2 that turns out to be a Sev 3 than to under-classify a Sev 1 and lose 30 minutes of response time.

---

## Section 2 — Roles & Responsibilities

A major incident requires clear role assignment within the first five minutes. Role confusion during active incidents is one of the leading causes of extended MTTR. These roles are assigned by the on-call Incident Commander at the time the bridge call is opened.

### Incident Commander (IC)
The single point of accountability for the incident from detection to closure. The IC does not troubleshoot — the IC manages the process.

**Responsibilities:**
- Declare the incident severity and open the ServiceNow major incident record
- Open and chair the bridge call
- Assign technical and communication roles
- Drive the resolution timeline — no one leaves the bridge without IC acknowledgment
- Make the call to escalate severity or bring in additional resources
- Approve the all-clear before incident is closed in ServiceNow
- Own the Post-Incident Review scheduling

### Technical Lead
The subject matter expert accountable for the technical resolution path.

**Responsibilities:**
- Lead troubleshooting on the bridge call
- Provide clear, jargon-free status updates to the IC every 30 minutes or sooner if status changes
- Coordinate technical resources and vendor support
- Document all actions taken in the ServiceNow incident work notes in real time
- Confirm resolution before IC declares all-clear

### Communications Lead
Owns all stakeholder communication during the incident. On Sev 1 and Sev 2, this role is always filled — it is never collapsed into the IC or Technical Lead.

**Responsibilities:**
- Send initial executive notification per timeline standards (see Section 4)
- Distribute 30-minute status updates to stakeholder distribution list
- Draft resolution notification and post-incident summary
- Manage customer-facing communication if applicable
- Update ServiceNow major incident workbench with stakeholder notification log

### Executive Sponsor
Senior leadership representative — VP or above — who is notified on Sev 1 incidents and available for escalation decisions.

**Responsibilities:**
- Available by phone during active Sev 1 incidents
- Authorize resource decisions that exceed Incident Commander authority (emergency vendor engagement, DR invocation, etc.)
- Receive executive bridge briefings as needed — not on the main technical bridge

### On-Call Engineer / Subject Matter Expert (SME)
Technical resource pulled into the incident based on the affected system or service.

**Responsibilities:**
- Join bridge call within 15 minutes of page (Sev 1) or 30 minutes (Sev 2)
- Provide system-specific expertise and execute remediation steps
- Document findings in ServiceNow work notes
- Confirm when their system component is stable

---

## Section 3 — Response Timeline Standards

Speed is non-negotiable on Sev 1 and Sev 2 incidents. These timelines are measured from the moment an alert fires or an incident is reported — not from when someone decides to act on it.

ServiceNow SLA timers start automatically when the incident record is created. Breach warnings fire at 75% of the SLA window. A breached SLA is flagged in ServiceNow and triggers automatic escalation to the on-call manager.

| Action | Sev 1 | Sev 2 | Sev 3 | Sev 4 |
|---|---|---|---|---|
| **Incident acknowledged in ServiceNow** | 5 min | 10 min | 30 min | 4 hours |
| **On-call engineer paged via PagerDuty / on-call system** | Immediate | 5 min | 15 min | Next business day |
| **Bridge call opened** | 10 min | 20 min | N/A | N/A |
| **Initial executive notification sent** | 15 min | 30 min | N/A | N/A |
| **First status update to stakeholders** | 30 min | 30 min | 1 hour | N/A |
| **Subsequent status updates** | Every 30 min | Every 30 min | Every 2 hours | N/A |
| **Target resolution (MTTR)** | 4 hours | 8 hours | 24 hours | 72 hours |
| **Incident closed in ServiceNow** | Within 24 hrs of resolution | Within 24 hrs | Within 48 hrs | Within 72 hrs |
| **PIR scheduled** | Within 48 hrs | Within 72 hrs | If warranted | No |

**Important:** Resolution time targets are goals, not guarantees. What is non-negotiable is the communication cadence. Stakeholders will tolerate a longer outage if they are informed. They will not tolerate silence.

---

## Section 4 — Bridge Call Protocol

The bridge call is the command center for a major incident. How you run the bridge determines how fast you resolve the incident. A poorly run bridge — with crosstalk, unclear ownership, and no discipline — adds hours to MTTR.

### Opening the Bridge Call

The Incident Commander opens with this standard structure — every time, no variation:

> *"This is [IC Name], Incident Commander for this event. We have a [Sev 1/Sev 2] incident — [one sentence description of what is down and what the customer impact is]. The incident record is [ServiceNow ticket number]. Time of detection was [time]. We are [X] minutes into the incident window.*
>
> *On this bridge: [confirm Technical Lead], [confirm Communications Lead]. SMEs, please identify yourselves and your system area.*
>
> *Technical Lead — what do we know right now and what is the current working theory?*"

That is it. No preamble. No story. The bridge starts with facts and immediately puts the Technical Lead on the clock.

### Bridge Call Discipline

- **One speaker at a time.** IC enforces this. Always.
- **No speculation on the bridge.** "I think it might be..." is not a status update. "We have confirmed X and are testing Y" is.
- **No war stories.** "This happened last year and..." is not relevant until the PIR.
- **Status updates on the clock.** Technical Lead provides a structured update every 30 minutes whether there is new information or not. "No change, still working" is a valid update. Silence is not.
- **Document in real time.** Every action taken, every finding, every theory tested goes into the ServiceNow work notes as it happens — not at the end of the incident.

### 30-Minute Status Update Structure (Technical Lead)

> *"Status update — [time]. Current status: [up / down / degraded]. What we know: [confirmed findings]. What we are doing: [active remediation steps]. Next update: [time]."*

Thirty seconds. Done. Back to work.

### Closing the Bridge Call

The IC closes — not the Technical Lead, not the engineer who fixed it.

> *"Confirming resolution. [Technical Lead] — are all systems stable and performing within normal parameters? [Wait for confirmation.] Communications Lead — resolution notification is being sent to stakeholders. I am updating the ServiceNow incident record to Resolved status. PIR will be scheduled within [48/72] hours. Bridge is closed."*

Incident is not closed until IC says it is closed.

---

## Section 5 — Executive Communication Templates

Executive communication during a major incident is a discipline, not an afterthought. The goal is to give leadership enough information to make decisions and set expectations — not a technical deep dive.

All executive notifications are logged in the ServiceNow major incident workbench under the Stakeholder Notifications tab.

### Template 1 — Initial Executive Notification (Sev 1: 15 min | Sev 2: 30 min)

> **Subject:** [SEV 1 INCIDENT] — [Impacted Service] — [Time] — IN PROGRESS
>
> **What happened:** [One sentence. What is down or degraded.]
>
> **Customer impact:** [Who is affected and how. Be specific — "all users" vs. "users in the Northeast region."]
>
> **Time of detection:** [Time]
>
> **Current status:** Investigation underway. Technical team engaged.
>
> **Incident Commander:** [Name]
>
> **Next update:** [Exact time — 30 minutes from this notification]
>
> **Incident record:** [ServiceNow ticket number]

### Template 2 — 30-Minute Status Update

> **Subject:** [SEV 1 UPDATE — [Time]] — [Impacted Service] — IN PROGRESS
>
> **Current status:** [Still down / Partially restored / Monitoring]
>
> **What we know:** [Two to three sentences. Confirmed findings only.]
>
> **What we are doing:** [Active remediation steps in plain language.]
>
> **Customer impact:** [Updated if changed from last notification.]
>
> **Estimated resolution:** [Give a range if known. Do not guess. "Under investigation" is acceptable if genuinely unknown.]
>
> **Next update:** [Exact time]

### Template 3 — Resolution Notification

> **Subject:** [RESOLVED — [Time]] — [Impacted Service] — RESOLVED
>
> **Status:** Resolved
>
> **Resolution time:** [Total duration from detection to resolution]
>
> **What happened:** [Two sentences. Plain language, no jargon.]
>
> **How it was resolved:** [One to two sentences.]
>
> **Customer impact:** [Confirmed scope of impact during the incident window.]
>
> **Next steps:** Post-Incident Review scheduled for [date/time]. Findings will be shared with stakeholders.
>
> **Incident record:** [ServiceNow ticket number — now closed]

---

## Section 6 — Escalation Path

Escalation is a process decision, not a failure. The Incident Commander escalates when the current resources, authority level, or resolution path is not sufficient to meet the response timeline. Escalating early is always better than escalating late.

### Internal Escalation Triggers

Escalate to the next level when any of the following are true:

- SLA timer has reached 75% of the target window with no confirmed resolution path
- Technical team has exhausted known remediation options
- A second system or service has been impacted — scope is expanding
- Severity needs to be upgraded based on new information
- A decision is required that exceeds Incident Commander authority

### Escalation Levels

| Level | Who | When |
|---|---|---|
| **Level 1** | On-call Incident Commander | At incident detection — first point of contact |
| **Level 2** | On-call Manager / Service Delivery Manager | Sev 1 at detection. Sev 2 at 30 minutes if no resolution path confirmed |
| **Level 3** | Director of Operations / VP of Technology | Sev 1 at 60 minutes if not resolved. Any incident with confirmed data loss or security component |
| **Level 4** | Executive Sponsor (VP / C-Suite) | Sev 1 at 2 hours if not resolved. Any incident with regulatory, legal, or major customer contract implications |

### Vendor Escalation

When a third-party vendor or carrier is involved in the resolution path:

1. Open a vendor support ticket immediately — do not wait for internal investigation to complete
2. Document the vendor ticket number in the ServiceNow incident record under the Related Records tab
3. Assign a dedicated SME to own the vendor bridge — IC does not manage vendor calls directly
4. If vendor response is not meeting SLA — escalate to vendor account manager, not just support queue
5. Log every vendor interaction — time, name, what was communicated — in ServiceNow work notes

**Vendor escalation is not optional when a Sev 1 has a confirmed third-party component.** Open the vendor ticket in parallel with internal investigation, not after.

---

## Section 7 — Post-Incident Review & Root Cause Analysis

The Post-Incident Review (PIR) is where the real value of incident management lives. Resolving the incident stops the bleeding. The PIR prevents it from happening again.

### PIR Principles

- **Blameless.** The PIR is not about finding who broke it. It is about finding what broke and why the system allowed it to break. People make mistakes — the process should catch mistakes before they become incidents.
- **Factual.** Timeline is built from ServiceNow work notes and monitoring data — not from memory.
- **Action-oriented.** Every PIR ends with assigned action items, owners, and due dates tracked as Problem tasks in ServiceNow.

### PIR Scheduling

| Severity | PIR Required | Scheduled Within |
|---|---|---|
| Sev 1 | Always | 48 hours of resolution |
| Sev 2 | Always | 72 hours of resolution |
| Sev 3 | If recurring or customer-impacting | 1 week |
| Sev 4 | No | N/A |

### PIR Attendees

- Incident Commander
- Technical Lead and relevant SMEs
- Communications Lead
- Service Delivery Manager
- Vendor representatives if third-party was involved
- No executives in the room — their presence changes the dynamic and undermines the blameless principle

### PIR Structure

**1. Timeline Review (15 minutes)**
Walk through the incident chronologically — detection, notification, escalation, resolution. Source of truth is the ServiceNow work notes and SLA timer data. Correct the record if anything is missing.

**2. What Happened (10 minutes)**
Confirm the root cause. One sentence: what failed, why it failed, what the contributing factors were.

**3. What Went Well (10 minutes)**
Acknowledge what worked. Communication? Detection speed? Vendor response? This is not a formality — it tells you what to protect.

**4. What Could Be Improved (20 minutes)**
This is the core of the PIR. For each gap identified, the question is not "who did this wrong" — it is "what process, tool, or safeguard would have caught this earlier or prevented it entirely."

**5. Action Items (15 minutes)**
Every improvement identified gets an action item with:
- Specific description of what will be done
- Named owner
- Due date
- Priority (P1/P2/P3)

Action items are entered as Problem Management tasks in ServiceNow and linked to the originating incident record. They do not sit in a slide deck.

### RCA Template

```
INCIDENT: [ServiceNow ticket number]
DATE OF INCIDENT: 
SEVERITY: 
DURATION: Detection to Resolution

ROOT CAUSE:
[One to two sentences. The specific technical or process failure that caused the incident.]

CONTRIBUTING FACTORS:
- [Factor 1]
- [Factor 2]
- [Factor 3]

TIMELINE:
[Time] — [Event]
[Time] — [Event]

CUSTOMER IMPACT:
[Who was affected, for how long, and what the business impact was.]

WHAT WENT WELL:
- 
- 

WHAT NEEDS IMPROVEMENT:
- 
- 

ACTION ITEMS:
| # | Action | Owner | Due Date | Priority |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |

KNOWN ERROR DATABASE (KEDB):
Has this failure mode been added to the ServiceNow Known Error Database? [Yes / No]
If yes — KEDB record number: 

PIR COMPLETED BY: 
PIR DATE: 
```

---

## Section 8 — Metrics & Continuous Improvement

You cannot improve what you do not measure. These are the metrics that matter for incident management — tracked in ServiceNow reporting dashboards and reviewed on a monthly cadence with operations leadership.

### Core Incident Metrics

| Metric | Definition | Target |
|---|---|---|
| **MTTA** (Mean Time to Acknowledge) | Average time from incident detection to acknowledgment in ServiceNow | Sev 1: ≤5 min / Sev 2: ≤10 min |
| **MTTR** (Mean Time to Resolve) | Average time from detection to resolution and ServiceNow closure | Sev 1: ≤4 hrs / Sev 2: ≤8 hrs |
| **SLA Compliance Rate** | Percentage of incidents resolved within target MTTR by severity | ≥95% |
| **Escalation Rate** | Percentage of incidents that required Level 3 or Level 4 escalation | Trending down month over month |
| **Repeat Incident Rate** | Percentage of incidents caused by a previously identified root cause | Target: <10% |
| **PIR Completion Rate** | Percentage of Sev 1 and Sev 2 incidents with completed PIRs | 100% |
| **Action Item Closure Rate** | Percentage of PIR action items closed by due date | ≥90% |

### Monthly Operations Review

Metrics are pulled from ServiceNow reporting and reviewed monthly with the following agenda:

1. Incident volume by severity — trending up or down?
2. SLA compliance rate — are we hitting targets?
3. Top 3 recurring incident categories — what patterns are emerging?
4. PIR action item status — what is open, what is overdue?
5. KEDB review — is the Known Error Database current and being used?

### Continuous Improvement Cycle

The output of every monthly review feeds one of three actions:

- **Process update** — runbook revised, new procedure documented
- **Training identified** — gap in team knowledge addressed
- **Tool or monitoring enhancement** — alert threshold adjusted, new monitoring rule created

Every change made to this runbook as a result of a PIR finding or monthly review is logged in the change log at the bottom of this document.

---

## Appendix — ServiceNow Quick Reference

| Action | Where in ServiceNow |
|---|---|
| Create incident record | Incident → Create New |
| Set priority (Impact + Urgency) | Incident form — Impact and Urgency fields auto-calculate Priority |
| Flag as Major Incident | Incident form — Major Incident checkbox → triggers Major Incident Workbench |
| Page on-call group | Incident form — Assignment Group → on-call schedule auto-routes notification |
| Log work notes | Incident form — Work Notes tab (internal only, not visible to end user) |
| Track SLA timer | Incident form — SLA tab — shows time remaining and breach status |
| Open vendor ticket link | Incident form — Related Records tab |
| Log stakeholder notifications | Major Incident Workbench — Stakeholder Notifications tab |
| Create Problem record from incident | Incident form → Related Records → Create Problem |
| Add to Known Error Database | Problem record → KEDB tab |
| Generate MTTR report | Reports → Incident Reports → Resolution Time by Priority |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release | Scott Boehler |

---

*This runbook is a living document. It should be reviewed after every Sev 1 incident and updated at minimum on a quarterly basis. A runbook that does not reflect how the team actually operates is not a runbook — it is a paperweight.*
