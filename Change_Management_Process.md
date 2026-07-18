# Change Management Process Template
### Enterprise IT Operations | Standard & Emergency Change Framework

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.1  
**Last Updated:** July 2026  
**Applies To:** All changes to production systems, infrastructure, applications, and services — including regulated and compliance-sensitive environments

---

## Purpose & Scope

This document defines the end-to-end change management process for enterprise IT operations. It covers how changes are classified, reviewed, approved, implemented, and closed — with equal rigor applied to both standard scheduled changes and emergency changes requiring expedited handling.

The goal is straightforward: protect production stability while enabling the business to move forward. A change management process that only slows things down without reducing risk is not a process — it is a bureaucracy. This framework is designed to do both.

All change records are created, tracked, and closed in ServiceNow. The Change Advisory Board (CAB) operates as the governance body for normal changes. Emergency changes follow an expedited path with post-implementation review.

This version incorporates regulatory and audit controls applicable to organizations operating in compliance-sensitive environments including financial services, healthcare, and other regulated industries.

---

## Section 1 — Change Classification

Every change is classified at the time of request. Classification determines the approval path, lead time, and CAB involvement required.

### Change Types

| Type | Definition | Lead Time | CAB Required |
|---|---|---|---|
| **Standard** | Pre-approved, low-risk, routine change following a documented procedure. Implemented without individual CAB review. | None — follows standing approval | No |
| **Normal** | Planned change requiring full CAB review and approval. Covers any change not pre-approved as standard. | Minimum 5 business days | Yes |
| **Emergency** | Unplanned change required immediately to restore service, prevent an outage, or address a critical security vulnerability. | None — expedited path | ECAB only |

### Risk Classification

All Normal and Emergency changes are assigned a risk level in ServiceNow at the time of submission:

| Risk Level | Criteria |
|---|---|
| **Low** | Minimal blast radius. Rollback straightforward. Affects single system or small user group. Well-tested procedure. |
| **Medium** | Moderate blast radius. Rollback possible but requires coordination. Affects multiple systems or a significant user population. |
| **High** | Large blast radius. Rollback complex or time-consuming. Affects core infrastructure, customer-facing services, or critical data. |
| **Critical** | Maximum blast radius. Rollback may not be possible within acceptable timeframe. Requires executive sign-off in addition to CAB. |

**Rule:** When in doubt, classify higher. A change that turns out to be lower risk than classified costs nothing. A change that turns out to be higher risk than classified can cost everything.

---

## Section 2 — Change Advisory Board (CAB)

The CAB is the governance body that reviews, challenges, and approves normal changes. It is not a rubber stamp — it is a risk assessment forum.

### CAB Membership

| Role | Responsibility |
|---|---|
| **CAB Chair** (Change Manager) | Facilitates the meeting, maintains the forward schedule, makes final approval calls |
| **Operations Representative** | Assesses operational risk and resource availability |
| **Infrastructure / Engineering Lead** | Reviews technical risk and implementation plan |
| **Service Delivery Manager** | Confirms customer impact and SLA implications |
| **Security Representative** | Flags security or compliance concerns |
| **Risk & Compliance Representative** | Reviews changes touching regulated systems or data — required for High and Critical changes in regulated environments |
| **Application Owner(s)** | Confirms application-level risk for relevant changes |
| **Vendor Representative** | Participates when third-party systems or carriers are involved |

### CAB Meeting Cadence

- **Standard CAB:** Weekly — reviews all normal changes scheduled for the following week
- **Emergency CAB (ECAB):** On-demand — convened within 2 hours for emergency changes requiring immediate approval
- **Post-Implementation Review:** Incorporated into the following week's CAB for any high-risk or emergency changes

### CAB Agenda Structure

1. Review of changes implemented since last CAB — any issues or rollbacks?
2. Review of open change records — status and blockers
3. New change submissions for approval — presented by change owner
4. Forward schedule of change (FSC) review — conflicts, blackout periods, resource availability
5. Emergency change post-implementation reviews
6. Action items and close

### CAB Documentation Requirements

In regulated environments, CAB meeting records are audit evidence. They must be complete, accurate, and retained per the organization's records retention policy.

**Required documentation for every CAB meeting:**

| Document | Content | Owner | Retention |
|---|---|---|---|
| **CAB Meeting Minutes** | Date, attendees, changes reviewed, decisions made, rationale for approval or rejection | CAB Chair | Per regulatory requirement — minimum 3 years |
| **Attendance Record** | Named individuals present — role and organization | CAB Chair | Per regulatory requirement |
| **Approval Record** | Each change reviewed — decision (approved / rejected / deferred), approvers by name, timestamp | CAB Chair | Per regulatory requirement |
| **Dissenting Opinion Record** | Any CAB member who disagreed with an approval decision — their name, role, and stated concern documented | CAB Chair | Per regulatory requirement |
| **Action Item Log** | Any follow-up items identified during CAB — owner and due date | CAB Chair | Per regulatory requirement |

**Dissenting Opinion Protocol:**
When a CAB member objects to an approval, their dissent is documented in the meeting minutes regardless of whether the change is ultimately approved. This is not punitive — it is a governance control. A dissenting opinion that proves correct after a change-induced incident is the record that protects the organization and the individual.

The CAB Chair does not suppress dissenting opinions. If a member disagrees, the minutes reflect it — verbatim if requested by the dissenting member.

**ServiceNow documentation:**
Every CAB decision is recorded in the ServiceNow change record within 24 hours of the CAB meeting. The approval state in ServiceNow is the system of record — meeting minutes are the supporting evidence. Both must exist for audit purposes.

---

## Section 3 — Standard Change Process

Standard changes are pre-approved, low-risk, and follow a documented procedure that has been previously reviewed and approved by the CAB. They do not require individual CAB review for each implementation.

### Qualifying a Standard Change

A change qualifies as standard when:
- It has been implemented successfully at least three times previously
- A fully documented procedure exists with step-by-step instructions
- Rollback procedure is defined and tested
- Risk has been assessed as Low
- The CAB has formally approved it as a standing standard change

Standard changes are maintained in the ServiceNow Standard Change Catalog. Implementers select the appropriate catalog item when creating the change record.

### Standard Change Workflow

1. Implementer creates change record in ServiceNow — selects Standard Change Catalog item
2. Change record auto-populates with the pre-approved procedure
3. Implementer confirms implementation window and assigns to themselves
4. Implementation proceeds per the documented procedure
5. Implementer updates work notes throughout implementation
6. Change closed in ServiceNow within 24 hours of completion — success or rollback noted

### Standard Change Review

The CAB reviews the Standard Change Catalog quarterly. Any standard change that has resulted in an incident or required rollback in the past 90 days is flagged for re-evaluation and potential reclassification.

---

## Section 4 — Normal Change Process

Normal changes require individual CAB review and approval. Every normal change submission must include a complete implementation plan before CAB will review it.

### Segregation of Duties

In regulated environments, segregation of duties is a hard compliance requirement — not a preference. The following roles must be held by different individuals. No single person may occupy more than one role for the same change.

| Role | Definition | May Also Be |
|---|---|---|
| **Change Requestor** | The individual who identifies the need for the change and submits the change record | Cannot be Approver or Implementer |
| **Change Approver** | The individual(s) who review and authorize the change — CAB members, SDM, Executive Sponsor as applicable | Cannot be Requestor or Implementer |
| **Change Implementer** | The individual who executes the change in the production environment | Cannot be Requestor or Approver |
| **Change Verifier** | The individual who confirms post-implementation testing and signs off on success | Cannot be Implementer |

**Why this matters in a regulated environment:**
Segregation of duties prevents a single individual from both making and approving a change to a production system — a control required by SOX, PCI-DSS, HIPAA, and most financial services regulatory frameworks. ServiceNow enforces this through role-based access controls that prevent the same user from populating both the Requested By and Approved By fields.

If a segregation of duties conflict is identified during CAB review, the change is returned to the requestor for reassignment before approval proceeds. No exceptions.

### Change Submission Requirements

All normal change requests must include the following before submission for CAB review. Incomplete submissions are returned without review.

| Field | Requirement |
|---|---|
| **Change Description** | Clear, plain-language description of what is changing and why |
| **Business Justification** | Why this change is needed — what problem it solves or what improvement it delivers |
| **Risk Assessment** | Low / Medium / High / Critical with written justification |
| **Impact Assessment** | What systems, services, and users are affected — and for how long |
| **Cybersecurity Review** | Required for all High and Critical changes — Security Representative sign-off confirming no new attack surface, no compliance control gap, no data exposure risk introduced by this change |
| **Regulatory Impact Assessment** | Required for changes touching regulated systems or data — confirmation that the change does not introduce a compliance gap or require regulatory notification |
| **Implementation Plan** | Step-by-step procedure with estimated time for each step |
| **Rollback Plan** | Specific steps to reverse the change if implementation fails — with rollback decision point defined |
| **Test Plan** | How success will be verified post-implementation |
| **Blackout Period Check** | Confirmation that the proposed window does not conflict with frozen periods or major business events |
| **Resource Confirmation** | All required implementers, approvers, and support contacts confirmed available |
| **Downtime Requirement** | Expected service interruption — duration and affected users |
| **Segregation of Duties Confirmation** | Requestor, Approver, Implementer, and Verifier are confirmed as different individuals |

### Normal Change Approval Path

| Risk Level | Required Approvals |
|---|---|
| **Low** | Change Manager + one technical reviewer |
| **Medium** | Change Manager + CAB consensus |
| **High** | Change Manager + CAB consensus + Service Delivery Manager + Security Representative |
| **Critical** | Change Manager + CAB consensus + Service Delivery Manager + Security Representative + Executive Sponsor |

### Normal Change Workflow

1. Change owner creates change record in ServiceNow — completes all required fields
2. Change record submitted for review — minimum 5 business days before proposed implementation
3. CAB reviews at weekly meeting — approves, rejects, or requests additional information
4. If approved — change appears on Forward Schedule of Change (FSC) in ServiceNow
5. Implementation proceeds per approved plan during approved window
6. Change owner updates work notes throughout — documents each step as completed
7. Post-implementation testing completed — success or rollback decision made at defined decision point
8. Change closed in ServiceNow within 24 hours — outcome documented

### Go / No-Go Checklist

This checklist is reviewed by the change owner immediately before implementation begins. If any item is not confirmed, implementation does not proceed.

- [ ] All required implementers are on the bridge / available
- [ ] Rollback procedure is confirmed and resources are ready to execute it
- [ ] Monitoring is in place to detect issues immediately post-implementation
- [ ] Customer notification has been sent if downtime was communicated
- [ ] Change window is confirmed — no conflicts with other active changes
- [ ] CAB approval is confirmed in ServiceNow
- [ ] Rollback decision point is defined — if [specific condition] is not met by [specific time], rollback begins
- [ ] All required vendor support contacts are available if third-party systems are involved
- [ ] Segregation of duties confirmed — Implementer is not the Requestor or Approver
- [ ] Cybersecurity review completed and approved (High and Critical changes)
- [ ] Regulatory impact confirmed — no compliance gap introduced by this change

---

## Section 5 — Emergency Change Process

Emergency changes are implemented outside the normal CAB process when waiting for a scheduled CAB would cause unacceptable business risk. They are not a workaround for poor planning — they are reserved for genuine emergencies.

### Legitimate Emergency Change Triggers

- Active Sev 1 or Sev 2 incident where a change is required to restore service
- Critical security vulnerability requiring immediate remediation
- Imminent risk of service failure identified through proactive monitoring
- Regulatory or compliance requirement with a non-negotiable deadline

### What Is NOT an Emergency Change

- A change that was not submitted in time for the weekly CAB
- A change that was rejected by CAB and resubmitted as emergency to bypass review
- A change that the requestor simply wants implemented faster than the normal process allows

Misuse of the emergency change process is tracked in ServiceNow. Patterns of misuse are reviewed by the Change Manager and escalated to operational leadership.

### Emergency Change Approval Path

1. Change owner contacts Change Manager or on-call SDM immediately
2. Emergency CAB (ECAB) convened — minimum 3 members: Change Manager, technical reviewer, Service Delivery Manager
3. ECAB reviews via bridge call — approval or rejection within 30 minutes
4. If approved — verbal approval documented in ServiceNow change record immediately
5. Implementation proceeds — change owner updates work notes in real time
6. Post-implementation review scheduled within 48 hours — findings presented at next weekly CAB

### Emergency Change Record Requirements

Emergency change records in ServiceNow must be created before implementation begins — not after. The record documents:

- Reason implementation cannot wait for normal CAB
- ECAB members who provided verbal approval and timestamp
- Implementation steps as they are executed (real-time work notes)
- Post-implementation test results
- Whether a follow-up normal change is required to make the emergency fix permanent

**Regulatory note:** In regulated environments, emergency changes receive the same audit scrutiny as normal changes — the timeline is compressed, but the documentation requirement is not. Every emergency change must have a complete record in ServiceNow before it is closed, including the post-implementation review findings.

### Post-Implementation Review — Emergency Changes

Every emergency change receives a post-implementation review at the next weekly CAB. The review covers:

- Was this a legitimate emergency or a planning failure?
- Did the change achieve the intended result?
- Were there any unintended consequences?
- Is a follow-up change required to make the fix permanent and properly documented?
- Should a standard change be created to cover this scenario going forward?

---

## Section 6 — Blackout Periods & Frozen Windows

Certain periods require heightened change controls or a complete freeze on changes to protect business-critical operations.

### Freeze Period Types

| Type | Definition | Change Restrictions |
|---|---|---|
| **Hard Freeze** | No changes of any kind permitted. Reserved for peak business periods (year-end close, major product launches, regulatory reporting periods, audit windows) | Emergency changes only — ECAB approval required with executive sign-off |
| **Soft Freeze** | Change volume reduced. Only pre-approved low-risk changes permitted. | Standard changes only — no normal or emergency changes without executive approval |
| **Heightened Awareness** | No freeze, but all changes receive additional scrutiny. High and Critical risk changes deferred if possible. | All changes proceed through normal process with mandatory Change Manager review |

Blackout periods are maintained in the ServiceNow Change Calendar and are visible to all change submitters. The Forward Schedule of Change (FSC) automatically flags conflicts with blackout periods.

**Regulated environment note:** In financial services and other regulated industries, blackout periods often align with regulatory reporting cycles, audit windows, and fiscal year-end. These periods are coordinated with the Risk and Compliance team and communicated to all change submitters at the start of each calendar year.

---

## Section 7 — Regulatory & Audit Controls

This section applies to organizations operating in regulated environments — financial services, healthcare, government, or any organization subject to external audit of IT change controls.

### Why Change Management Is an Audit Target

Regulators and auditors examine change management for one reason — uncontrolled changes are one of the leading causes of production incidents, data breaches, and compliance failures. A change management process that cannot demonstrate consistent, documented, and enforced controls is a material finding in any IT audit.

The controls in this section are not optional in regulated environments. They are the evidence that demonstrates the change management process is working as designed.

### Audit Evidence Requirements

Every change record in ServiceNow must be complete enough to serve as standalone audit evidence. An auditor reviewing a change record should be able to answer the following questions from the record alone — without interviewing the team:

| Question | Where the Evidence Lives in ServiceNow |
|---|---|
| Who requested this change? | Requested By field — individual name, not a team |
| Why was this change needed? | Business Justification field |
| What was the risk assessment? | Risk field + Risk Assessment notes |
| Who approved this change? | Approval tab — named approvers with timestamps |
| Was cybersecurity reviewed? | Security Approval field — Security Representative sign-off |
| Was segregation of duties maintained? | Requested By, Approved By, and Implemented By fields — must be different individuals |
| When was this change implemented? | Work Notes — implementation start and end timestamps |
| What steps were taken? | Work Notes — step-by-step implementation log |
| Was the change successful? | Closure Code field — Successful / Rolled Back / Partially Implemented |
| Were there any unintended consequences? | Post-implementation notes and linked incident records |
| Was a PIR conducted for high-risk changes? | Related Records — PIR task linked to change record |

**Any change record that cannot answer all of these questions is incomplete for audit purposes.** The Change Manager reviews a sample of closed change records monthly to confirm completeness. Incomplete records are returned to the change owner for remediation.

### Compliance Controls Embedded in the Change Lifecycle

| Control | Where Applied | Purpose |
|---|---|---|
| **Pre-approval cybersecurity review** | High and Critical changes — required before CAB submission | Prevents changes that introduce security vulnerabilities or compliance gaps |
| **Segregation of duties** | All changes — enforced in ServiceNow | Prevents single individual from both making and approving production changes |
| **CAB approval documentation** | All normal changes — documented in ServiceNow within 24 hours | Creates auditable approval record for every production change |
| **Dissenting opinion documentation** | CAB meetings — documented in meeting minutes | Ensures all risk concerns are on record regardless of approval outcome |
| **Emergency change post-implementation review** | All emergency changes — completed at next CAB | Ensures expedited changes receive the same scrutiny as normal changes after the fact |
| **Unauthorized change detection** | Monthly audit of production changes vs. ServiceNow records | Identifies and investigates any production change without an approved change record |
| **Standard Change Catalog quarterly review** | Quarterly CAB agenda item | Ensures pre-approved changes remain low-risk and current |
| **Change record completeness review** | Monthly — Change Manager | Ensures all closed records meet audit evidence standards |

### Unauthorized Change Detection and Response

An unauthorized change is any modification to a production system, application, or configuration that does not have a corresponding approved change record in ServiceNow.

**Detection:**
Monthly reconciliation of production change logs against ServiceNow change records. Any production change without a corresponding approved ServiceNow record is flagged as unauthorized.

**Response:**
1. Unauthorized change identified — flagged to Change Manager and SDM immediately
2. Change owner identified and notified — required to provide written explanation within 24 hours
3. Risk assessment completed — was there any security, compliance, or stability impact?
4. Incident created if production impact is confirmed
5. Formal corrective action issued to change owner — first occurrence: documented warning. Second occurrence: escalated to operations leadership.
6. Root cause documented — was this a process gap, a training gap, or a deliberate bypass?
7. ServiceNow record created retroactively — documenting what was changed, when, and by whom

**Regulatory note:** In financial services environments, unauthorized changes may constitute a regulatory reportable event depending on the systems affected and the nature of the change. Risk and Compliance is notified of all unauthorized changes involving regulated systems.

### Audit Preparation

When an internal or external audit of change management is scheduled:

1. Change Manager pulls the following from ServiceNow for the audit period:
   - Complete change log — all changes by type, risk level, and outcome
   - CAB meeting minutes — all meetings in the audit period
   - Emergency change log — all emergency changes with post-implementation review status
   - Unauthorized change log — all flagged unauthorized changes and disposition
   - Change-induced incident report — all incidents correlated to a recent change
   - Rollback log — all changes that required rollback with root cause

2. Change Manager reviews completeness of all change records in the audit population — remediates gaps before audit begins

3. CAB Chair confirms meeting minutes are complete and retained for all CAB meetings in the audit period

4. Any known gaps or control exceptions are disclosed proactively — auditors discover what you hide and remember it

---

## Section 8 — ServiceNow Quick Reference

| Action | Where in ServiceNow |
|---|---|
| Create change record | Change → Create New |
| Select standard change | Change → Standard Change Catalog |
| Submit for CAB review | Change record → Submit for Approval |
| View Forward Schedule of Change | Change → Forward Schedule of Change |
| Check blackout periods | Change → Change Calendar |
| Document implementation steps | Change record → Work Notes tab |
| Record ECAB approval | Change record → Approval tab → Add Approver → note verbal approval |
| Close change record | Change record → State → Closed (update outcome field) |
| Link to incident record | Change record → Related Records → Add Relationship |
| Create PIR task | Change record → Related Records → Create Task |
| Record cybersecurity sign-off | Change record → Security Approval field |
| Confirm segregation of duties | Change record → Requested By / Approved By / Implemented By — must be different users |
| Pull audit change log | Reports → Change Reports → All Changes by Period |
| Pull unauthorized change report | Reports → Change Reports → Changes Without Approval |

---

## Section 9 — Metrics & Continuous Improvement

| Metric | Definition | Target |
|---|---|---|
| **Change Success Rate** | Percentage of changes implemented without incident or rollback | ≥95% |
| **Emergency Change Rate** | Percentage of total changes classified as emergency | <10% — high rate signals planning problems |
| **CAB Approval Rate** | Percentage of submitted changes approved at first review | Trending up — rejections signal poor submission quality |
| **Rollback Rate** | Percentage of changes requiring rollback | <5% |
| **Unauthorized Change Rate** | Changes implemented without an approved change record | 0% target |
| **Change-Induced Incident Rate** | Percentage of incidents caused by a recent change | Trending down month over month |
| **Change Record Completeness Rate** | Percentage of closed change records meeting audit evidence standards | 100% — incomplete records are a compliance risk |
| **Segregation of Duties Compliance Rate** | Percentage of changes where Requestor, Approver, and Implementer are confirmed different individuals | 100% — any exception is a compliance finding |
| **Cybersecurity Review Compliance Rate** | Percentage of High and Critical changes with completed Security Representative sign-off | 100% |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release | Scott Boehler |
| 1.1 | July 2026 | Added regulatory and audit controls (Section 7), CAB documentation requirements, segregation of duties framework, cybersecurity review checkpoint, and compliance-focused ServiceNow quick reference entries | Scott Boehler |

---

*Changes that fail because of poor planning are not bad luck — they are predictable outcomes. In a regulated environment, they are also audit findings. The purpose of this process is to make those outcomes visible before implementation — and to leave a record that proves it.*
