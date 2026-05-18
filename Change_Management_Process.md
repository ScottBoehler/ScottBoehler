# Change Management Process Template
### Enterprise IT Operations | Standard & Emergency Change Framework

**Author:** Scott Boehler — Service Delivery & Operations Leader  
**Version:** 1.0  
**Last Updated:** May 2026  
**Applies To:** All changes to production systems, infrastructure, applications, and services

---

## Purpose & Scope

This document defines the end-to-end change management process for enterprise IT operations. It covers how changes are classified, reviewed, approved, implemented, and closed — with equal rigor applied to both standard scheduled changes and emergency changes requiring expedited handling.

The goal is straightforward: protect production stability while enabling the business to move forward. A change management process that only slows things down without reducing risk is not a process — it is a bureaucracy. This framework is designed to do both.

All change records are created, tracked, and closed in ServiceNow. The Change Advisory Board (CAB) operates as the governance body for normal changes. Emergency changes follow an expedited path with post-implementation review.

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

### Change Submission Requirements

All normal change requests must include the following before submission for CAB review. Incomplete submissions are returned without review.

| Field | Requirement |
|---|---|
| **Change Description** | Clear, plain-language description of what is changing and why |
| **Business Justification** | Why this change is needed — what problem it solves or what improvement it delivers |
| **Risk Assessment** | Low / Medium / High / Critical with written justification |
| **Impact Assessment** | What systems, services, and users are affected — and for how long |
| **Implementation Plan** | Step-by-step procedure with estimated time for each step |
| **Rollback Plan** | Specific steps to reverse the change if implementation fails — with rollback decision point defined |
| **Test Plan** | How success will be verified post-implementation |
| **Blackout Period Check** | Confirmation that the proposed window does not conflict with frozen periods or major business events |
| **Resource Confirmation** | All required implementers, approvers, and support contacts confirmed available |
| **Downtime Requirement** | Expected service interruption — duration and affected users |

### Normal Change Approval Path

| Risk Level | Required Approvals |
|---|---|
| **Low** | Change Manager + one technical reviewer |
| **Medium** | Change Manager + CAB consensus |
| **High** | Change Manager + CAB consensus + Service Delivery Manager |
| **Critical** | Change Manager + CAB consensus + Service Delivery Manager + Executive Sponsor |

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
| **Hard Freeze** | No changes of any kind permitted. Reserved for peak business periods (year-end close, major product launches, etc.) | Emergency changes only — ECAB approval required with executive sign-off |
| **Soft Freeze** | Change volume reduced. Only pre-approved low-risk changes permitted. | Standard changes only — no normal or emergency changes without executive approval |
| **Heightened Awareness** | No freeze, but all changes receive additional scrutiny. High and Critical risk changes deferred if possible. | All changes proceed through normal process with mandatory Change Manager review |

Blackout periods are maintained in the ServiceNow Change Calendar and are visible to all change submitters. The Forward Schedule of Change (FSC) automatically flags conflicts with blackout periods.

---

## Section 7 — ServiceNow Quick Reference

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

---

## Section 8 — Metrics & Continuous Improvement

| Metric | Definition | Target |
|---|---|---|
| **Change Success Rate** | Percentage of changes implemented without incident or rollback | ≥95% |
| **Emergency Change Rate** | Percentage of total changes classified as emergency | <10% — high rate signals planning problems |
| **CAB Approval Rate** | Percentage of submitted changes approved at first review | Trending up — rejections signal poor submission quality |
| **Rollback Rate** | Percentage of changes requiring rollback | <5% |
| **Unauthorized Change Rate** | Changes implemented without an approved change record | 0% target |
| **Change-Induced Incident Rate** | Percentage of incidents caused by a recent change | Trending down month over month |

---

## Change Log

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | May 2026 | Initial release | Scott Boehler |

---

*Changes that fail because of poor planning are not bad luck — they are predictable outcomes. The purpose of this process is to make those outcomes visible before implementation, not after.*
